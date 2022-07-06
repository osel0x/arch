### Credits to 

https://www.dwarmstrong.org/arch-lts-kernel/

### Install

#### 1. Install linux-lts ...
```
$ sudo pacman -S linux-lts
```
#### 2. arch-lts.conf

Example setup uses the systemd-boot loader. Copy existing arch.conf to arch-lts.conf ...
```
$ sudo cp /boot/loader/entries/arch.conf /boot/loader/entries/arch-lts.conf
```
Modify arch-lts.conf with settings:

    title Arch LTS
    linux /vmlinuz-linux-lts
    initrd /initramfs-linux-lts.img

#### 3. Boot loader

Confirm we have a valid configuration by listing boot loader entries ...
```
$ bootctl list
```
#### 4. Reboot

Reboot and select LTS kernel. Check to see if the running kernel is indeed -lts ...
```
$ uname -r
5.10.75-1-lts
```
#### 5. Make default

Optional: If you want to use LTS as the default boot kernel, it is safe to remove Arch's linux kernel ...
```
$ sudo pacman -R linux
```
Set default in /boot/loader/loader.conf to default arch-lts.conf.
