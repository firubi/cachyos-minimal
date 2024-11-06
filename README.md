# CachyOS-minimal
In order to install a minimal KDE-desktop, deselect everything except `plasma-desktop`, `sddm` and `sddm-kcm`. Remove any other program you see fit. Switch from paru to yay :)

## CachyOS-Hello Tweaks
I recommend only using ananicy rules and bluetooth. I've had issues with high ram usage (when browser is not even up) and Firefox reporting running out of disk space with profile-sync-daemon enabled. 

## Basic KDE functionality
- `sudo pacman -S --needed kscreen dolphin breeze-gtk kde-gtk-config ffmpegthumbs kdegraphics-thumbnailers kate plasma-pa plasma-nm plasma-systemmonitor bluedevil ark zathura`

## Enable btrfs-snapper support
In the CachyOS Hello app, enable snapper support, and in addition install `sudo pacman -S --needed grub-btrfs grub-btrfs-support` and enable the service `sudo systemctl enable --now grub-btrfsd`.

## Remove some more bloat
- Make sure to switch to bash `chsh -s /usr/bin/bash`
- `sudo pacman -Rns  fish cachyos-fish-config fish-autopair fish-pure-prompt fisher konsole`
- Reboot

## Personal packages for me
- Install `cachyos-gaming-meta`
- `sudo pacman -S --needed gnome-disk-utility fastfetch fcitx5 fcitx5-configtool fcitx5-mozc mpv flatpak xdg-desktop-portal-gtk filelight nvidia-settings kitty`
- `flatpak install flathub net.davidotek.pupgui2 dev.vencord.Vesktop org.keepassxc.KeePassXC org.qbittorrent.qBittorrent org.ryujinx.Ryujinx com.obsproject.Studio com.usebottles.bottles com.github.tchx84.Flatseal info.cemu.Cemu sh.ppy.osu org.prismlauncher.PrismLauncher org.fooyin.fooyin org.gnome.Boxes io.github.xiaoyifang.goldendict_ng org.kde.kdenlive org.kde.gwenview`



## Various tips
### Fcitx5
Add in /etc/environment
```
GTK_IM_MODULE=fcitx
QT_IM_MODULE=fcitx
XMODIFIERS=@im=fcitx
```

### SDDM-themes
My preferred SDDM-theme is `Sugar Candy/Dark`, which you can download through the KDE's SDDM settings. This theme needs a few dependencies: `sudo pacman -S --needed qt5-graphicaleffects qt5-quickcontrols2 qt5-svg`

### SDDM-fixes
You can change the refresh rate and primary monitor in SDDM. Edit the file /usr/share/sddm/scripts/Xsetup as sudo and add in the lines:
```
xrandr --output DP-0 --primary --mode 2560x1440 --rate 180
xrandr --output HDMI-0 --brightness 0
```
You can get the numbers from running `xrandr | grep -w connected` while in an **X-session**.

### Anki
After an update, the audio in Anki is low. You need to specify ao=pulse in mpv.conf, and put it in ~/.local/share/Anki2/ so Anki reads it.

## Apparmor
Make sure to make a snapshot before installing apparmor. See installation guide [here](https://wiki.cachyos.org/configuration/post_install_setup/#4-enable-apparmor-support-using-apparmord-profiles). It does slightly increase RAM usage - an increase of about ~800Mb for me. I personally don't use this as it blocks thumbnail generation in Dolphin (I'm sure you could edit this out but I won't bother). 

## Hyprland with HyprPanel
- Install `bun`
- `yay -S --needed hyprland hyprlock jq swww waypaper tofi qt5ct qt6ct-kde xdg-desktop-portal-hyprland grim slurp pipewire libgtop bluez bluez-utils btop networkmanager dart-sass wl-clipboard brightnessctl hyprpicker aylurs-gtk-shell python gnome-bluetooth-3.0 pacman-contrib power-profiles-daemon gvfs libdbusmenu-gtk3 archlinux-xdg-menu`
- Follow the instructions [here](https://hyprpanel.com/getting_started/installation.html)

- If you want to uninstall: `yay -Rns hyprland hyprlock swww waypaper tofi qt5ct qt6ct-kde xdg-desktop-portal-hyprland grim slurp libgtop dart-sass wl-clipboard brightnessctl hyprpicker aylurs-gtk-shell gnome-bluetooth-3.0 gvfs libdbusmenu-gtk3 archlinux-xdg-menu`, then remove orhpans `sudo pacman -Rns $(pacman -Qdtq)`.
- Uninstall `bun`, instructions [here](https://bun.sh/docs/installation).

## Simple Hyprland
- `yay -S hyprland waybar hyprlock swww waypaper swaync tofi qt6ct-kde xdg-desktop-portal-hyprland grim slurp wl-clipboard archlinux-xdg-menu`

## Basic maintenance
- `sudo pacman -Syu` - to update
- `sudo pacman -Rns` - to remove package
- `pacman -Qq | wc -l` - to show package count
- `sudo pacman -Rns $(pacman -Qdtq)` - to remove orphans (does also remove some make dependencies for AUR and tkg)
- `paccache -r` - to remove previous versions of packages, but keep the latest 3
- `paccache -ruk0` - to remove previous versions of uninstalled packages
