# Cachyos-minimal
In order to install a minimal KDE-desktop, deselect everything except `plasma-desktop`, `sddm` and `sddm-kcm`. Remove any other program you see fit. Switch from paru to yay :)

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
- `flatpak install flathub net.davidotek.pupgui2 dev.vencord.Vesktop org.keepassxc.KeePassXC org.qbittorrent.qBittorrent org.ryujinx.Ryujinx com.obsproject.Studio com.usebottles.bottles com.github.tchx84.Flatseal info.cemu.Cemu sh.ppy.osu org.prismlauncher.PrismLauncher org.fooyin.fooyin org.gnome.Boxes io.github.xiaoyifang.goldendict_ng`



## Various tips
### Fcitx5
Add in /etc/environment
```
GTK_IM_MODULE=fcitx
QT_IM_MODULE=fcitx
XMODIFIERS=@im=fcitx
```

### SDDM-themes
My preferred SDDM-theme is `Sugar Candy/Dark`, which you can download through the KDE's SDDM settings. This theme needs a few dependencies: `sudo pacman -S --needed qt5‑graphicaleffect qt5‑quickcontrols2 qt5‑svg`

### SDDM-fixes
You can change the refresh rate and primary monitor in SDDM. Edit the file /usr/share/sddm/scripts/Xsetup as sudo and add in the lines:
```
xrandr --output DP-0 --primary --mode 2560x1440 --rate 180
xrandr --output HDMI-0 --brightness 0
```
You can get the numbers from running `xrandr | grep -w connected` while in an **X-session**.

### Anki
After an update, the audio in Anki is low. You need to specify ao=pulse in mpv.conf, and put it in ~/.local/share/Anki2/ so Anki reads it.
