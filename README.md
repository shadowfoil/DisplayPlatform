# DisplayPlatform
Repository of information regarding the Shadowfoil Display Platform

# JFO Saber Stand
![image](./images/JFOHolderBoxArt.png)

## TouchSense PCB
The TouchSense PCB is a custom PCB designed in house by Shadowfoil Props to power the JFO Saber Stand. The PCB uses a JSM8233 touch sensor (functionally identical to TTP223), has an onboard touch sensitive red LED, 4 JST SH1.0 (1mm pitch) connectors, and a CR2032 coin cell battery holder. 

![image](./images/2025-02-21-142708_002-topaz-remove-.jpg)
![image](./images/2025-02-21-142708_004.jpg)

### Touch Rails
The touch rails are v-cut at the fab and can be gently removed for assembly in the saber stand. We recommend using the edge of a table or toothless pliers to break at the v-cut.

![image](./images/2025-02-21-142708_002.jpg)
![image](./images/2025-02-21-142708_005.jpg)

### Wiring
The PCB supports both hardwired LED connections at each corner or four JST SH1.0 connectors for quick disconnects. The TCH pads on either side are for touch input leads.

![image](./images/2025-02-21-142708_003.jpg)

JST Connectors are accessible from one side of the PCB if you prefer to have quick disconnects for your LEDs.

![image](./images/2025-02-21-144004_004.jpeg)

Careful not to damage the wires when adjusting the angle of the arms!

![image](./images/2025-02-21-144004_008.jpeg)

### Battery
The TouchSense PCB runs on a standard CR2032 coin cell battery and should get around 24 hours of continuous on-time. If you prefer rechargeable batteries you can instead opt to using a lithium ion LIR2032 in it's place and remove to recharge it.

![image](./images/2025-02-21-144004_006.jpeg)

## Installation
### Prep work:
1. Glue pre-wired 0802 LEDs to the underside of the resin posts with a drop of CA/Super glue. The LEDs should be positioned with the light side in the channel facing the top of the post.
2. Allow these to dry fully before continuing
3. Ensure you have 1.5mm, 2mm, and 2.5mm hex drivers

### Disassembly:
1. Remove underside hex screws with 1.5mm driver. (These can also be loosened to adjust the width of the stand)

    ![image](./images/2025-02-21-144004_002.jpeg)
2. Slide arm assemblies off the center body
3. Using 2.5mm hex driver, remove the larger hex screws on the arm sides to separate the upper and lower portions of the arm assembly.
4. Using 2mm hex driver, remove the single set screw from each arm.

### Assembly:
1. Once the glue has dried on the resin posts gently thread the wires down through the upper portion of the arm assembly. This may take some gentle finangling to get the wires to thread out the center hole in the bottom of the upper arm. Tweezers can be helpful at this step.
2. Next, carefully thread the wire ends through the center of the lower half of the arm assembly so that it extends into the area shared with the center piece.
3. Re-insert the screws for the arm assembly removed during disassembly. The arm angle can be adjusted before tightening screws as desired.
4. If using connectors solder them to the LED wire leads; if hardwiring you can solder the wires directly to the GND and OUT pads of the PCB.
5. Gently break the touch rails off the main PCB.

    ![image](./images/2025-02-21-142708_002.jpg)
6. Solder a wire from one of the TCH pads on the rails to either TCH pad on the main PCB, these touch rails will sit in the groove on either side of the center body. The TCH pads should extend slighlty past the end on either side.

    ![image](./images/2025-02-21-142708_005.jpg)

    ![image](./images/2025-02-21-144004_004.jpeg)
7. Once all soldering and connections are complete, insert a CR/LIR 2032 coin cell battery into the PCB's battery holder. Attaching a small amount of tape to the battery edge can make it easier to remove later.
8. Verify LEDs all toggle on and off with consecutive touches on the touch rails. The red led on the main pcb is a GRC (gross reality check) output to verify touch input without external LEDs.
9. Place the touch rails into the grooves on the center body
10. Re-attach the side assembly to the center body, pinning the touch rails in place.

    ![image](./images/2025-02-21-144004_007.jpeg)

## Adjustment

### Side Arm Angle
Adjust the angle of the arms as desired by loosening side screws and rotating it. Be careful not to break the wires by over-rotating.

### Bottom Width
Adjust the width of the bottom assembly by loosening the underside screws and sliding the arms in or out. 

## Battery replacement
When the battery dies, remove the arm assembly that exposes the battery slot. Gently pull the PCB out enough to remove the battery. Tape or a small tool can be helpful in pulling/pushing the battery free. Insert a fresh battery and re-assemble.

![image](./images/2025-02-21-144004_005.jpeg)

# JFO Workbench
![image](./images/JFOBenchBoxArt.png)

## Workbench PCB
The workbench PCB is a shield type PCB meant to pair with a Waveshare ESP32-C3-Zero MCU. The PCB comes mostly pre-assembled with only the MCU needing to be added. We've increased the size of the pads for the MCU to make hand soldering a bit easier. 

The PCB itself comes with 88 recessed neopixel (WS2812-mini-E) LEDs evenly distributed around the board's edge, two JST connectors for USB-C breakout with USB2.0 data connection to the MCU, 3A polyfuses with solder jumper bypasses, and a physical AP Mode switch.

### Disclaimer
We've tested the PCB with up to 3A input power which is the max rating for the USB-C connectors we utilize as well as the max for devices without specific USB-PD (power delivery) configuration. We however limit the amperage in software to 1A since not all power supplies/computer ports/etc are capable of delivery 3A continuously and 1A generated a decent brightness output. The software limit can easily be changed by the user in WLED settings, and the hardware limit can be removed by closing the solder jumper bypasses next to each polyfuse, we however do not accept any liability for user modifications to our devices.

## WLED
A fast and feature-rich implementation of an ESP8266/ESP32 webserver to control NeoPixel (WS2812B, WS2811, SK6812) LEDs or also SPI based chipsets like the WS2801 and APA102!

[Source](https://github.com/wled/WLED)

### Why WLED?
We utilize WLED as our firmware of choice for the workbench PCB as it is robust, well-maintained, and has cross platform functionality with PC, Mac, Android, and iOS devices. It is also relatively simple to get up and running with no coding necessary for our users. 

### Installation
The firmware can be easily loaded by utilizing their [web installer](https://install.wled.me). Navigate to this page, plug in your device (the Workbench in this case) and click Install. Your computer should prompt you to select the correct device, we recommend disconnecting other microcontroller boards such as Proffie/GHv4/CFX before installing.

### Kno.WLED.ge
You can find a ton more information [here](https://kno.wled.ge)

### WLED+
WLED+ is a third party Android and iOS application for controlling WLED devices. It works with any existing WLED device (including our workbench) and has a cleaner more modern UI and runs natively on both Android and iOS phones and tablets. You can find it [here](https://wledplus.com)

We highly recommend using this software for controlling the workbench and have been using it ourselves for most of our testing and development process.

### Pre-Installed Setup
If you bought one of our kits pre-installed we will have already loaded a default config and preset bank for WLED onto the workbench. However, the workbench will not be aware of your local wifi details. You have two options to control it from here: 

- OPTION 1: Control it through the WLED-AP WiFi Hotspot
    If the workbench is unable to find the pre-configured wifi network it will instead create its own WiFi Hotspot called "SHADOWFOIL" and does not have a password. You can connect directly to this WiFi hotspot and control the device through the web interface.

- OPTION 2: Change WiFi details and control it through your local WiFi
    1. Plug the workbench into your computer with either USB-C port
    2. Navigate to the [web installer](https://install.wled.me)
    3. Click "Install"

        ![image](./images/install_button.png)

    4. Select the device from the available ports

        ![image](./images/port_select.png)
    
    5. Click "Change Wi-Fi"

        ![image](./images/options.png)
    
    6. It should prompt you for your WiFi credentials then connect automatically
    7. Once completed you should see the following dialog

        ![image](./images/connected.png)
    
    8. You can then click "Visit Device" to open the web interface or open the WLED+ app from your phone or tablet to adjust settings.

### Self-Install
If you bought the workbench as a kit and are doing the install yourself, good luck! (jk we are working on finishing this portion of the documentation and will have it available soon, if you have questions don't hesitate to ask!) An important note is that the JFO board is set tonuse GPIO 5 for neopixel data instead of WLED's default GPIO 2. You will need to specify that in the WLED config settings.

### Shadowfoil Default Config and Preset Bank
We have put together our default config and preset bank and exported them to json files for anyone to then upload onto their workbench if they don't want to fiddle with settings or presets. You can find them in this repository here:

[Config](./config/JFO_Config.json)

[Presets](./config/JFO_Presets.json)

Once you have these files saved to your local computer you can upload them to the workbench by following these instructions

1. Navigate to the WLED web portal for your device (if you go to the install page with your device plugged into your computer and click install it will show you the "Visit Device" button which takes you there)
2. Click Config

    ![image](./images/config.png)

3. Click Security & Updates

    ![image](./images/security.png)

4. Scroll down to Backup & Restore

    ![image](./images/restore.png)

5. Upload the presets file to the Restore presets input
6. Upload the config file to the Restore configuration input
