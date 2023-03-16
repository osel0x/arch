Based on 
https://www.youtube.com/watch?v=LBNEW4ZKvEc&t=357s

#### Change keyboard language

````shell
loadkeys la-latin1
````
#### Connect to Wi-Fi

````shell
iwctl
station wlan0 connect Gotham_5G
passprhase:
exit
ping 4.2.2.2
````

#### archinstall package
````shell
pacman -Sy archinstall
archinstall
````

#### Installation (nvme0 -> Linux disk)
Additional packages

````shell
git nano iwd
````
![img.png](images/installation/img.png)

Finish installation and enter chroot to enable iwctl

````shell
systemctl enable --now iwd.service
systemctl enable --now systemd-netword.service
systemctl enable --now systemd-resolved.service
````

Restart computer

#### Configuring Network

##### Wired
https://wiki.archlinux.org/title/Systemd-networkd
````shell
/etc/systemd/network/20-wired.network

[Match]
Name=enp1s0

[Network]
DHCP=yes
````
##### Wireless
````shell
iwctl
station wlan0 connect SSID
passphrse:
exit
ping 4.2.2.2
````

#### Configuring Environment
````shell
git clone https://github.com/Axarva/dotfiles-2.0.git
cd dotfiles-2.0
chmod +x install-on-arch.sh
./install-on-arch.sh
````
Select 3 if you have NVIDIA
![img_1.png](images/installation/img_1.png)

#### Configure environment

````shell
AUR helper: paru (all dependencies [y])
````
#### Configure
````shell
nano ~/.bashrc
````
Add to top below comments & save it
````shell
export PATH="$PATH:$HOME/bin"
````

#### Set Weather API (Openweather)
````shell
cd
pwd
ls
nano .config/eww/scripts/getweather
````

#### Recompile monad
````shell
xmonad --recompile
sucess!!
````
#### Add startx to bash_profile file 
#### 
````shell
pwd (check home dir)
nano .bash_profile
startx
exit nano
````
#### Create xinitrc file

````shell
nano .xinitrc
exec xmonad
save & exit nano
````

#### Edits .yml files
````shell
nano .config/alacritty.yml
size: 12
save & exit nano
````
#### Start Monad
````shell
exit & login again
````

#### Install config manager
````shell
shift + Enter -> New terminal
sudo pacman -Syu gtk2
tint2conf
````

#### Basic Commands
````shell
shift + Enter -> New terminal
Mod (Win key) + Enter -> New terminal
tint2conf

````
