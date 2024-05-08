# My system backup and installer

## Description

The setup that I use is arch linux with dwm anything else is pretty trival in terms of functioning OS

The desktop experience is created by scripts patches and programs that work well with each other.

## Core programs

dwm - window manager

dwmblocks - clickable status bar

dmenu - application / script launcher

st zsh - terminal emulator and shell

lf - file manager

mpv - audio video player and image viewwer

vim - text editor

## What should be chanaged if you want to use it

config file that the installer use

`linux-k4/config`

packages to be installed in the installer

`linux-k4/setup-2-pacstrap.sh` or `linux-k4/resources/package_list/*`

enviromental variables in zsh config

`linux-k4/resources/dotfiles/.config/env-vars`

dwm keybinds

`linux-k4/resources/dotfiles/.static/src/dwm/config.h`

## Resources & Helpful links

https://wiki.archlinux.org/

https://suckless.org/

https://github.com/torrinfail/dwmblocks

https://github.com/ohmyzsh/ohmyzsh/wiki/Plugins

https://github.com/gokcehan/lf

https://github.com/thimc/lfimg

https://mpv.io/

https://github.com/occivink/mpv-image-viewer

https://neovim.io/doc/user/

<br/>


# Scriptless Arch Install 

<details>

<summary>Installation</summary>

<br/>

Each step is described well on arch wiki

it only serves as a reminder for a basic install for myself

The most curious thing to look up would be a different file system to ext4

<br/>

## inside arch iso (pre setup)

`loadkeys uk` (ls -R /usr/share/kbd/keymaps)

`vim /etc/pacman.conf`

&emsp; &emsp; `ParallelDownloads = 5`

<br/>

### Internet

connect to wifi if no ethernet available (use help command / common sense / google to do it with a command below)

`iwctl`

<br/>

### Partitioning Disk SDX = drive (could be nvme0n1 instead)

`gdisk /dev/SDX`

<br/>

p1 boot | end sector = +200M, Type Efi EF00

p2 root | default

<br/>

`mkfs.fat -F32 /dev/SDXp1`

`mkfs.ext4 /dev/SDXp2`

</br>

`mount /dev/SDXp2 /mnt`

`mkdir -p /mnt/boot/efi`

`mount /dev/SDXp1 /mnt/boot/efi`

</br>

### Base System

`pacstrap -K /mnt base base-devel linux linux-firmware grub os-prober efibootmgr networkmanager neovim`

<br/>

### Generate /etc/fstab

`genfstab -U /mnt >> /mnt/etc/fstab`

<br/>

### Enter into new system

`arch-chroot /mnt bash`

`nvim /etc/pacman.conf`

&emsp; &emsp; `Color`

&emsp; &emsp; `ParallelDownloads = 5`

<br/>

### time zone

`ln -sf /usr/share/zoneinfo/Europe/Warsaw /etc/localtime`

`hwclock --systohc`

<br/>

### locale

```
echo "en_GB.UTF-8 UTF-8
pl_PL.UTF-8 UTF-8" >> /etc/locale.gen
```

`locale-gen`

```
echo "LANG=en_GB.UTF-8
LC_COLLATE=C" > /etc/locale.conf
```

```
echo "KEYMAP=uk" > /etc/vconsole.conf
```

<br/>

### Root / User setup

`passwd`

`useradd -G wheel -m user`

`passwd user`

`nvim /etc/sudoers`

&emsp; &emsp; `%wheel ALL=(ALL:ALL) NOPASSWD: ALL`

<br/>

### Network configuration

`echo "hostname" > /etc/hostname`

<br/>

`nvim /etc/hosts`

```
echo "127.0.0.1    localhost
::1          localhost
127.0.1.1    hostname.localdomain hostname" > /etc/hosts
```

<br/>



### Boot Loader

<br/>

<details>

<summary> No Boot Option fix </summary>

`grub-install --removable --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=grub`

`nvim /etc/default/grub`

&emsp; &emsp; `GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"`
``

<br/>

</details>

`grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=grub`

<br/>

`grub-mkconfig -o /boot/grub/grub.cfg`

<br/>

### Reboot  

`exit`

`umount -R /mnt`

`reboot`

Minimal installation is finished

</details>
