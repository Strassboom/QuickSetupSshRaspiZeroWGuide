# QuickSetupSshRaspiZeroWGuide
Quickest way to set up a Raspberry Pi Zero W for ssh over usb

## Materials required

- (1) Computer with at least one USB Type-A port
- (1) Raspberry Pi Zero W
- (1) Raspbian Image, downloadable from [here](https://www.raspberrypi.org/downloads/raspbian)
    - This tutorial was conducted with an image of Raspbian Buster Lite
- MicroSD Card
    - Recommended Size 16GB 
    - Minimum Size: 4GB
- MicroUSB to USB cable

## Stages

1. **Flashing**: **Flashing Raspbian** onto your MicroSD Card
2. **Boot Editing**: Editing **config.txt** and **cmdline.txt**
3. **Testing Connection**: Using ssh over MicroUSB to USB cable

## Flashing
##### Step Count: 5
1. Insert your MicroSD card into your computer:
    - If your computer does not have a MicroSD slot, use a MicroSD to USB or MicroSD to SD adaptor
    - Do NOT remove the MicroSD card until one of the later steps suggests so.
    - **Time to completion**: 5-10 secs

2. Download an raspbian image if not already possessed 
    - **Time to completion**: 0 minutes if already installed ;) otherwise...
    - **Time to completion**: 3-8 mins depending on the size (lite\normal\full) of the image, and your internet connection speed
3. Install the [balenaEtcher](https://www.balena.io/etcher/) program
    - **Time to completion**: 30 secs
4. Run balenaEtcher
    - in the gui...
        1. Select your raspbian image
        2. Select your target (your MicroSD card)
        3. Finally click "Flash!"
    - **Time to completion**: 30 seconds
5. Wait until the program says it is finished.
    - A second loading bar appears for validation after the "flashing loading bar" is complete
    - **Time to completion**: ~3 minutes

## Boot Editing
##### Step Count: 8
1. Go to the boot drive in your computer
2. Open config.txt
3. Append `dtoverlay=dwc2` to a new line at the end of the file
4. Save and close config.txt
5. Open cmdline.txt leave (1) space between the text `rootawait` and `modules-load=dwc2,g_ether`
    -  If any text follows `rootawait`, then leave (1) space between `modules-load=dwc2,g_ether` and that text block as well
6. create an empty file named `ssh` in the boot drive
    - Ensure the file is not followed by `.txt` or any other file extension
7. Select eject for the boot drive
8. Physically unplug the MicroSD card from your computer

## Testing Connection

1. Insert the MicroSD Card into your Raspberry Pi Zero W
    - The golden strips should be facing the the raspberry pi if you are looking from the top of the Raspberry pi during insertion, or "butter-side down"
2. Plug the MicroUSB connector of your cable into the "Data" MicroUSB port on your Raspberry Pi Zero W
    - This port is between the MiniHDMI port and the "Power" MicroUSB port
3. Plug the other side of the cable into your computer
4. Wait about a minute for the raspberry pi to boot up
5. Open your terminal
6. Type `ssh pi@raspberrypi.local` and press enter
7. if asked to pass to continue regarding a "Key Fingerprint", select type yes and press enter
8. Enter the default password `raspberry`
    - If you see `pi@raspberrypi:` Then you are now done!
