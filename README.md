# Anne pro 2 arch linux
## _The better way to use bluetooth in archlinux with Annepro, Ever_

<p align="center">
  <img src="https://www.hexcore.xyz/images/obinskit/icon.png" />
</p>

I used orico adapter to connect Annepro2 keyboard.

- Orico 5.0 USB Bluetooth Adapter
- Anne pro2



## Tools

Open source projects to work properly:

- [rfkill](https://man7.org/linux/man-pages/man8/rfkill.8.html) - The rfkill command lists, enables and disables wireless devices!
- [bluez](http://www.bluez.org/) - Provides support for the core Bluetooth layers and protocols. It is flexible, efficient and uses a modular implementation
- [obinskit](https://www.hexcore.xyz/obinskit) - Obinskit is the driver software for ANNE PRO 2.

## Installation

Enable bluetooth.service
```sh
sudo systemctl enable --now bluetooth.service
```

```sh
sudo systemctl start bluetooth.service
sudo systemctl status bluetooth.service
```

Unblock bluetooth using rfkill
```sh
rfkill list bluetooth
```

```sh
rfkill unblock bluetooth
```

Install packages
```sh
sudo pacman -S bluez
sudo pacman -S bluez-utils 
sudo pacman -S blueman
sudo pacman -S bluez-alsa
```

If you want use pulseaudio
```sh
sudo pacman -S pulseaudio-bluetooth
pulseaudio -k
pulseaudio --start
```
I needed install this packge to fix pulseaudio
```sh
git clone https://aur.archlinux.org/pulseaudio-bluetooth-a2dp-gdm-fix.git
cd pulseaudio-bluetooth-a2dp-gdm-fix
makepkg -si
```
Start bluetoothctl
```sh
bluetoothctl
```
If you want use config file to setup your choices
```sh
sudo vim /etc/bluetooth/main.conf
```

Install obinskit to annepro2
```sh
git clone https://aur.archlinux.org/obinskit.git
cd obinskit
makepkg -si
sudo $(which obinskit) --no-sandbox
```

Turn on Bluetooth broadcast on keyboard
```sh
FN2 + 1 （5 Seconds） = Turn on Bluetooth broadcast on position 1
```

