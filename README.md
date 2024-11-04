# Cachyos-minimal
In order to install a minimal KDE-desktop, deselect everything except `plasma-desktop`, `sddm` and `sddm-kcm`. Remove any other program you see fit. 

## Basic KDE functionality
- `sudo pacman -S --needed kscreen dolphin breeze-gtk kde-gtk-config`

## Enable btrfs-snapper support
In the CachyOS Hello app, enable snapper support, and in addition install `sudo pacman -S --needed grub-btrfs grub-btrfs-support` and enable the service `sudo systemctl enable --now grub-btrfsd`.

## Remove some more bloat
- Make sure to switch to bash `chsh -s /usr/bin/bash`
- `sudo pacman -Rns  fish cachyos-fish-config fish-autopair fish-pure-prompt fisher konsole`
- Reboot

## Personal packages for me
- Install `cachyos-gaming-meta`
- `sudo pacman -S --needed gnome-disk-utility fastfetch fcitx5 fcitx5-configtool fcitx5-mozc mpv flatpak xdg-desktop-portal-gtk filelight nvidia-settings kitty`
