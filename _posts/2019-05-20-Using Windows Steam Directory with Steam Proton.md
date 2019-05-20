---
title: Using a Windows Steam Directory with Steam Proton
layout: post
permalink: /:year/:month/:day/:title/
excerpt_separator: <!--more-->
---

## Introduction
If you are like me and have a large Steam library and are still switching from Windows to Linux, you can actually use your Windows installed games on Linux thanks to the Valve developed [Proton](https://github.com/ValveSoftware/Proton/wiki/Requirements)!

## Requirements
- The Linux version of [Steam](https://store.steampowered.com/about/) installed (I am using Ubuntu 19.04)
- A separate NTFS formatted disk with your Steam library folder (this guide assumes that Windows is NOT installed on this disk)
- Up to date graphics drivers:
    - NVIDIA
    ```
    sudo add-apt-repository ppa:graphics-drivers/ppa
    sudo apt install nvidia-driver-418
    ```
    - AMD/Intel
    ```
    sudo add-apt-repository ppa:paulo-miguel-dias/pkppa
    sudo apt dist-upgrade
    sudo apt install mesa-vulkan-drivers mesa-vulkan-drivers:i386
    ```
    - Radeon R9 200/300 series
    ```
    echo "blacklist radeon" | sudo tee --append /etc/modprobe.d/blacklist.conf
    echo "options amdgpu si_support=1 cik_support=1" | sudo tee --append /etc/modprobe.d/amdgpu.conf
    sudo update-initramfs -u
    ```
- Python 3 and Python Minimal:
    - Python 3
    ```
    sudo apt install python3
    ```
    - Python Minimal
    ```
    sudo apt install python-minimal
    ```

<!--more-->

## Finding the Attached Disk Partition and UUID
In order to find your NTFS partition label you can use the following command:
```
sudo fdisk -l
```
It will have an output similar to this:
```
...
Disk /dev/sda: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 2E9F174D-53CA-42AD-9CD4-DF7CA90B0C7A

Device      Start        End    Sectors  Size Type
/dev/sda1      34     262177     262144  128M Microsoft reserved
/dev/sda2 264192 7814035455 7813771264 3.7T Microsoft basic data
...
```

If you are using GNOME Nautilus, you can see what it is labeled by clicking on *Other Locations*.

*The trailing letter and number (a2) will depend on how many disks are attached.*

The disk partition I want to mount is labeled `/dev/sda2`.

Now that you know what your disk partition is labeled, we need to find out that partition's UUID. To find your UUID use the `blkid` command like this:

```
sudo blkid
```

You will see an output similar to this:
```
...
/dev/sda1: UUID="0CAEEC94AEEC781A" TYPE="ntfs" PARTUUID="1e6ca286-01"
/dev/sda2: UUID="50E2054BE205372E" TYPE="ntfs" PARTUUID="1e6ca286-02"
...
```

Look for the line that matches the disk partition you want to mount, for me that line would be `/dev/sda2`. Record what the UUID is for that parition, mine is `50E2054BE205372E`.

## Configuring and Automounting the NTFS Partition
We are now going to create a mount point for our game disk:

```
sudo mkdir /media/gamedisk
```

For the next part, we need to know our User ID and Group ID. You can find them by using the following commands:

### User ID
```
id -u
```
### Group ID
```
id -g
```

The results by default should be `1000` for both the User and Group ID, but check to make sure.

### FSTAB

Next, we are going to edit our `/etc/fstab` file to mount the partition:
```
sudo nano /etc/fstab
```
At the bottom of the file, add the following line (changing UUID, mount point, UID, and GID to match your results):
```
...
UUID=38CE9483CE943AD8 /media/gamedisk ntfs uid=1000,gid=1000,rw,user,exec,umask=000 0 0
```

*On Ubuntu, as long as ntfs-3g is installed using ntfs as the filesystem type will work*

Use the Arrow Keys <kbd>←</kbd><kbd>↑</kbd><kbd>→</kbd><kbd>↓</kbd> to position the Insertion Cursor.

Hit <kbd>CTRL</kbd> + <kbd>X</kbd> to exit, <kbd>Y</kbd> to save, and <kbd>Enter</kbd> to confirm.

We need to reboot the computer for the changes to take effect:
```
sudo reboot
```

## Preventing NTFS Read Errors
Due to the nature of NTFS, creating files/folders with characters Windows cannot read will cause disk errors (leading to games that don't launch), the most common issue is a `;` character in filenames that Proton creates on the NTFS disk.

Fixing this is pretty simple. Create a symlink from the `/compatdata` folder on Linux to the mounted NTFS disk.

Creating the symlink:

```
ln -s ~/.steam/steam/steamapps/compatdata /media/gamedisk/Games/Steam/steamapps/
```

*If the `/compatdata` folder already exists on your mounted disk BEFORE the syslink, DELETE IT!*

## Enabling Steam Proton
Open up your Linux version of Steam.

Click on *Steam* → *Settings* → *Steam Play*.

Make sure there is a check next to:

- Enable Steam Play for support titles
- Enable Steam Play for all other titles

For the *Run other titles with* dropdown, by default it will select the latest version of Proton (as of this post it is Proton 4.2-4).

*You may want to change this option depending on the game you want to play, some games perform better or worse on a specific Proton version.*

Click *Ok* to confirm, Steam should prompt you to restart for the changes to take effect, click *Restart Now*.

## Adding Second Steam Library Path
Once Proton is enabled, you need to add your old Windows Steam library path so your currently installed games show up in your library as installed.

Click on *Steam* → *Settings* → *Downloads* → *STEAM LIBRARY FOLDERS*.

Click on *Downloads* → *STEAM LIBRARY FOLDERS*.

Then *ADD LIBRARY FOLDER*.

Navigate to your Steam folder, my full path is `/media/gamedisk/Games/Steam/`.

Click *Ok* to confirm, then right click on your new library and click *Make Default Folder*.

Click *Ok* again and Steam should prompt you to restart for the changes to take effect, click *Restart Now*.

When Steam launches again it will start downloading small bits of information for every game in your library, depending on how many games and the specific games, it may take a bit to complete.

Once everything is done downloading, you can go ahead and run your Steam games!

## What games work?

You can check the [ProtonDB](https://www.protondb.com/) website to get an idea how well certain games will run. If you don't mind getting your hands dirty, there will usually be some extra configurations to help you fix bugs and get more performance out of your games.

Also, post any issues you may have on the official [Proton issue tracker](https://github.com/ValveSoftware/Proton/issues) so Valve can fix them!