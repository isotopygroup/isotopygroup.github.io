# Machine

Install [Ubuntu](https://ubuntu.com) as main OS and allow for future install of additional OS.
Keep all documents in a shared partition accessable by all OS.
To begin create a bootable USB startup disk containing Ubuntu.

## Partition Hard Drive
Boot Ubuntu from the USB and run [GParted](https://gparted.org).

- Create a new partition table (WARNING: this will erase all data, so copy anything you wish to keep first) and then add the following partitions.
  1. Leave 1MB free space at beginning and make a partition (1000MB fat32) for an EFI System Partition (ESP).
  2. Make a partition (250MB unformatted) for possible future bios\boot use.
  3. Make a partition (32000MB linux-swap) for swap space.
  4. Make a partition (300000MB ext4) for documents and work shared across operating systems.
  5. Make a partition (150000MB ext4) for main OS.
  6. Make a partition (150000MB ext4) for secondary OS.
  7. Make a partition (20000MB ext4) for experimenting with an OS.
  8. Make a partition (20000MB ext4) for experimenting with a second OS.
  9. Reserve any remaining space for future use, either leave unallocated or make a partition (ext4).
- Apply all changes to the partition table.
  - Set the `boot` and `esp` flags on the first partition.
  - Set the `swap` flag on the third partition.

## Install Main OS
Choose to install Ubuntu from the USB.

- Choose `Minimal Installation` instead of 'Normal Installation'.
- Choose to 'download updates while installing Ubuntu'.
- Choose to 'install third-party software for graphics and Wi-Fi hardware and additional media formats'.
- Choose the do `Something else` option when selecting the installation type.
  - Make sure partition 1 is set to be used as 'EFI System Partition'.
  - Make sure partition 3 is set to be used as a 'swap partition'.
  - Use partition 4 as 'Ext4 Journaling file system' and choose to mount it somewhere (e.g. `/work`). Do not format if it contains data.
  - Use partition 5 as 'Ext4 Journaling file system' and make sure to mount it at root `/`. Select the format option.
- After the installation is complete and the computer reboots into the new OS install any software updates
  - First check with the `Software Updater` utility.
  - Next check with the `Ubuntu Software` app.
- Look through system `Settings` and customize (e.g. dark mode, multiple displays).

## Install Git

```
sudo apt update
sudo apt install git
```

## Install rEFInd Boot Manager
We will use [rEFInd](https://www.rodsbooks.com/refind) to select which OS to boot.
Before getting started check that the ESP is mounted at `/boot/efi` (e.g. in the terminal enter `> df /boot/efi`).

The rEFInd website describes several methods of installation.
I used the following:

```
sudo apt-add-repository ppa:rodsmith/refind
sudo apt-get update
sudo apt-get install refind
```

### Adding a theme to rEFInd
One of the themes mentioned on the rEFInd website is [Regular-theme](https://github.com/bobafetthotmail/refind-theme-regular) which can be installed as follows:

```
git clone https://github.com/bobafetthotmail/refind-theme-regular.git

rm -rf refind-theme-regular/{src,.git}
rm refind-theme-regular/install.sh

sudo rm -rf /boot/efi/EFI/refind/{regular-theme,refind-theme-regular}
sudo cp -r refind-theme-regular /boot/efi/EFI/refind/

rm -rf refind-theme-regular
```

Finally, edit the file `/boot/efi/EFI/refind/refind.conf` by adding a the following line at the end:
  
```
include refind-theme-regular/theme.conf
```

### Remove unwanted boot options
Create a directory within `/boot/efi` called `IGNORE` in which to move unwanted directories or files (e.g. move `/boot/efi/ubuntu` into `/boot/efi/IGNORE`).
