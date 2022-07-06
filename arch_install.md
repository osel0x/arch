#### 1. Change keyboard layout
```
loadkeys la-latin1
```
#### 2. Setup wI-fI
```
iwctl
station wlan0 connect Gotham_5G
exit
ping 4.2.2.2
```
#### 3. Setup partitions
```
fdisk -l
cfdisk /dev/nvme0n1
```

Create 3 partitions
 - 512 MB - EFI
 - 128 G - linux 
 - 348 G - linux
write on menu

#### 4. Arch install file
```
sudo pacman -Sy archinstall
archinstall

select: ?
type: la-latin1
select:0

country select:38

select disk 2(nvme)
select yo choose individula what to do with each partition

perform option 4:
mount /boot 
mount /home
mount /
 
perform option 5 on partitions 1 and 2, choose "btrfs" as filesystem --> verify "format:true"
perform option 6 on partitions 1 and 2 --> verify "encrypted:true"
perform oprtion 7 on partition 0

done, press no option
set LUKS password:
do not use GRUB:N
use zram:Y
```

Set hostname, root pass and osel0x pass and set it as superuser

select option X: 

- i3 works fine and install light-gdm light-gdm-greeter
- desktop y only gnome , with this option all works fine with second monitor


select all open source drivers : 1
select pipewire:0
select linux (the only working with virtualbox) >>linux 

#### 5. Additional packages
additional packages (i3): git nano firefox linux-hardened-headers alacritty networkmanager
additional packages (gnome): git nano firefox linux-hardened-headers wpa_supplicant wireless_tools networkmanager nm-connection-editor network-manager-applet

select wlan0
select dhcp
set tz to America/Mexico_City
setntp:Y
perform post installation configurations : yes

#### 6. Setup wI-fI
configure network with these commands disable dhcpd and start networkmanager fails (no problem)
```
sudo systemctl enable NetworkManager.service
sudo systemctl disable dhcpcd.service
sudo systemctl enable wpa_supplicant.service
sudo systemctl start NetworkManager.service
exit
reboot
```

Setup Wi-Fi
```
sudo nmtui
```

#### 7. Setup GNOME
** betTer option install gnome from beginning**

```
install gnome
sudo pacman -S gnome
all
1
Y
```

to enable at start
```
sudo systemctl enable gdm.service
```

to start gnome
```
sudo systemctl start gdm.service
```

#### 7. Setup miscellaneous
```
sudo pacman -Sy htop
sudo pacman -Sy firefox
```

Install yay package manager
```
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -sri
```

install timeshift
```
yay timeshift
select option 1
remove dependencies: N
Launch : sudo timeshift-gtk
```

exclude home
Create your first snapshot 

install virtualbox
```
sudo pacman -S virtualbox virtualbox-guest-iso
```
