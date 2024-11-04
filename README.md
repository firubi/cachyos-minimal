# Cachyos-minimal
In order to install a minimal KDE-desktop, deselect everything except `plasma-desktop`, `sddm` and `sddm-kcm`. Remove any other program you see fit. 

## Basic KDE functionality
`sudo pacman -S --needed kscreen dolphin breeze-gtk kde-gtk-config`

## Enable btrfs-snapper support
In the CachyOS Hello app, enable snapper support, and in addition install `sudo pacman -S --needed grub-btrfs grub-btrfs-support` and enable the service `sudo systemctl enable --now grub-btrfsd`.
