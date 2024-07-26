# Debian and LMint Suggest

```bash
sudo apt purge gnote gedit libreoffice* hexchat hypnotix redshift onboard celluloid transmission gnome-calendar  gnome-2048 gnome-chess gnome-games gnome-klotski gnome-mahjongg gnome-mines gnome-nibbles gnome-robots gnome-sound-recorder gnome-sudoku gnome-taquin gnome-tetravex gnome-video-effects thunderbird pidgin remmina shotwell sound-juicer transmission-common transmission-gtk rhythmbox xterm drawing pix sticky thingy warpinator && sudo apt autoremove
```

```bash
sudo apt purge gnote gedit libreoffice* hexchat hypnotix redshift onboard celluloid transmission gnome-calendar gnome-2048 gnome-chess gnome-games gnome-klotski gnome-mahjongg gnome-mines gnome-nibbles gnome-robots gnome-sound-recorder gnome-sudoku gnome-taquin gnome-tetravex gnome-video-effects thunderbird pidgin remmina shotwell sound-juicer transmission-common transmission-gtk rhythmbox xterm && sudo apt autoremove
```

## Usuario en cinnamon

```bash
/usr/sbin/lightdm --show-config
```

Verificar ruta:

```bash
sudo nano /usr/share/lightdm/lightdm.conf.d/01_debian.conf
```

Deberá aparecer:

```bash
greeter-hide-users=false
```
