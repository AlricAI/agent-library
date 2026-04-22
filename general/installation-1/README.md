# Installation

> <!-- TOC -->
* [Installation](#installation)
  * [UEFI](#uefi)
  * [Windows](#windows)
  * [Arch Linux](#arch-linux)
    * [mozc](#mozc)
    * [Wiresh

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Installation

<!-- TOC -->
* [Installation](#installation)
  * [UEFI](#uefi)
  * [Windows](#windows)
  * [Arch Linux](#arch-linux)
    * [mozc](#mozc)
    * [Wireshark](#wireshark)
    * [Google Chrome](#google-chrome)
    * [Android Studio](#android-studio)
    * [IntelliJ](#intellij)
    * [How to set up a VM for Windows 11](#how-to-set-up-a-vm-for-windows-11)
<!-- TOC -->

## UEFI

1. AI Tweaker | Precision Boost Overdrive | Precision Boost Overdrive | AMD ECO Mode
2. AI Tweaker | Ai Overclock Tuner | DOCP I
3. Advanced | Onboard Devices Configuration | LED lighting | Stealth Mode
4. Tweak FAN settings to Silent
5. Tweak Boot Option Priorities to prioritize Linux

## Windows

1. Install Windows(Disk: 200GB)
2. Install drivers from disk
3. Disable Fast Startup at control panel

## Arch Linux

```sh
$ iwctl station "$WIRELESS_NIC" connect "$SSID" --passphrase "$PASSWORD"
$ gdisk /dev/nvme0n1
# Use the rest of the disk for LVM
$ LVM_PARTITION=/dev/nvme0n1p5
$ pvcreate $LVM_PARTITION
$ vgcreate vg0 $LVM_PARTITION
$ lvcreate -L 1000G -T vg0/thinpool
$ lvcreate -V 2000G vg0/thinpool -n root
$ cryptsetup luksFormat -c aes-xts-plain64 -s 512 /dev/mapper/vg0-root
$ cryptsetup open /dev/mapper/vg0-root root
$ mkfs.btrfs /dev/mapper/root

$ mount -o compress=zstd,discard=async /dev/mapper/root /mnt
$ mkdir /mnt/boot
$ mount /dev/nvme0n1p1 /mnt/boot
$ pacman -Sy archlinux-keyring
$ pacstrap /mnt base base-devel
$ genfstab -U /mnt >> /mnt/etc/fstab
$ lvcreate -L 100G vg0 -n swap
$ mkswap /dev/vg0/swap
$ echo "/dev/vg0/swap none swap defaults 0 0" >> /mnt/etc/fstab
$ lvcreate -V 100G vg0/thinpool -n nfs
$ mkfs.xfs /dev/vg0/nfs
$ echo "/dev/vg0/nfs /srv/nfs xfs defaults 0 0" >> /mnt/etc/fstab
$ arch-chroot /mnt

$ pacman -S vim linux amd-ucode linux-firmware mkinitcpio lvm2 iwd nvidia-open git btrfs-progs
$ ln -sf /usr/share/zoneinfo/Asia/Tokyo /etc/localtime
$ hwclock --systohc --utc
$ vim /etc/locale.gen # comment out en_US.UTF-8,ja_JP.UTF-8
$ locale-gen
$ echo LANG=en_US.U

*[truncated — see source for full prompt]*