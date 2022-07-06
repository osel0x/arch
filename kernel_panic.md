### Credits to 

https://wiki.archlinux.org/title/General_troubleshooting_(Espa%C3%B1ol)

### Recover from kernel panic

#### Show partitions
```
# lsblk
```
### Open encrypted partitions
```
# cryptsetup open /dev/nvme0n1p1 home
# cryptsetup open /dev/nvme0n1p2 root
```
### Mount encrypted partitions
```
# mount /dev/mapper/root /mnt
# mount /dev/mapper/home /mnt/home
```
### Fix Kernel Panic
```
# arch-chroot /mnt
# pacman -Syu
```

### If it  fails, exit chroot and try:
```
# pacman -Syu --sysroot /mnt
```
### If it  fails, try:
```
# pacman -Syu --root /mnt --cachedir /mnt/var/cache/pacman/pkg
```
