# retroarch-setup
Deploy a retroarch dedicated box on Ubuntu 20.04

## Ubuntu 20.04
Deploy an Ubuntu 20.04 Minimal Desktop Installation. I like to separate my partitions like this
| size | mount point |
| ---- | ---- |
| 50gb | / |
| whatever is left | /data |

- Enable auto login

### Disable Screensaver/Black screen
This setting is disabled from the `Settings` app under `Power`

### Force specific resolution
Find the output you are using and open/create `~/.config/autostart/xrandr.desktop` and add the following lines

```
[Desktop Entry]
Type=Application
Exec=/usr/bin/xrandr --output [your output] --mode [your resolution]
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_US]=Set Resolution
Name=Set Resolution
Comment[en_US]=Change Resolution Upon Login
Comment=Change Resolution Upon Login
```

set the mode to 664

## Install Vulkan
Validate that your video card is [compatible with Vulkan](http://vulkan.gpuinfo.org/listdevices.php?platform=linux). You can check your video card by running `ubuntu-drivers devices` in the [terminal](https://linuxconfig.org/how-to-install-the-nvidia-drivers-on-ubuntu-20-04-focal-fossa-linux). Use the following commands to install vulkan,

```
sudo add-apt-repository ppa:oibaf/graphics-drivers
sudo apt update
sudo apt upgrade -y
apt install -y libvulkan1 mesa-vulkan-drivers vulkan-utils
```

## Install Retroarch
Use the following commands to install 

```
sudo add-apt-repository ppa:libretro/stable && sudo apt-get update && sudo apt-get install retroarch*
```
you might need to update the assets if your icons are missing.

### Autostart Retroarch
Create `~/.config/autostart/retroarch.desktop` and add the following lines

```
[Desktop Entry]
Type=Application
Exec=/usr/bin/retroarch
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_US]=RetroArch
Name=Set RetroArch
Comment[en_US]=Start RetroArch
Comment=Start Retroarch
```

set the mode to 664
