The CB1 and the Pi1 are pretty much the same thing, so they use all the same software. And since it's not a raspberry pi chip, you'll have to use the images provided by BTT.

For this guide, you'll need about 1GB of free space on your computer c:

# Image
## Pi Imager
First, you'll need to download Raspberry Pi imager from [here](https://github.com/raspberrypi/rpi-imager/releases). The screenshots in this guide are of v1.8.5 but other versions shouldn't be too different. Download and install it.

## BTT Image
Now the actual image.

BTT released the v3.0.0 image that uses debian 12, but get the V2.4.3. I've fully tested it and I know that it works wihtout issues.

*Download the `CB1_Debian11_minimal_kernel5.16_20240319.img.xz`, theres no use for the klipper version, it only brings more potential problems.*

[Here's the download page.](https://github.com/bigtreetech/CB1/releases/tag/V2.3.4) Save it somewhere you'll be able to access.

## Write
Grab an SD card that's atleast 8GB, and plug it into your device. (Windows is preferred but Mac and Linux work too). It is also recommended to unplug other external storage devices from your computer to reduce confusion.

Now open the Pi Imager.

Under "Device" select "No Filtering" and under "Storage" select your SD card.

For "Operating System" scroll down, and click "Use Custom". It will open a file explorer window and you'll need to pick the image that you downloaded earlier.

<img src="./Images/CustomOS.png">

Click "Write" and if it prompts to change settings, select "No".

<img src="./Images/OS-Settings.png">

Click yes to continue.

<img src="./Images/Imager-writing.png">

When it finishes writing, unplug the SD card and plug it back in, just to make sure it reads correctly.
## Configure settings
### WiFi
If you're using ethernet, skip this section and go to "Overlays"

Go to file explorer and click on the SD card. There should be a file named `system.cfg`. Edit it in a notepad or any other supported editor.

<img src="./Images/Boot-partition.png">

Under the Wifi section, find the wifi name and password settings. Set your WiFi name and password. It should be something like this:
```
# wifi_name
WIFI_SSID="SuzukiWifi"
# wifi password
WIFI_PASSWD="SuzukiWifiPass"
```
__________________________________________________________
### Overlays
Really the only one that's important for us is the tft display, since a lot of people would be using that.

i2c doesn't work on these (because BTT), spi isnt really needed if you're not using it, and everything else is some specific thing that one in a million people uses. c:

To change overlays, go to `BoardEnv.txt`, and uncomment what you need.

For a TFT display, uncomment `overlays=tft35_spi`, don't forget to save and restart.
# First boot
Plug the SD card into the Pi or CB1. For CB1 make sure it's the right slot.
