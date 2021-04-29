# Zoom Leave Meeting Button
<img src="https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png"/><br/>
<img src="./images/switch.jpg?raw=true" width="400" height="400"/>

*Edited* files for building your own Single-button "keyboard" that ~~does only one thing~~ can do whatever you want it to do, including: leaving any Zoom meetings.
This fork was made since I wanted to make this as a leaving gift for some co-workers. I've made a QMK keymap and have added build instructions since the original creator hasn't been active with this for a while now.

See demo here: https://www.youtube.com/watch?v=0GqqAG8KL6Q
And here's the Reddit thread that prompted the sharing: https://www.reddit.com/r/MechanicalKeyboards/comments/l7to85/singlebutton_keyboard_gives_the_satisfaction_of_a/

## What it is

* A single-switch mechanical keyboard / macropad with a large 3D-printed keycap
* Supported by 3 stabilizers so you can press anywhere on the key
* Powered by a Pro Micro Arduino microcontroller
* ~~Really only sends an Alt-F4 to the active window. So this assumes the Zoom window is the current focus (see improvement ideas below)~~
* Edited to be powered by [QMK](https://qmk.fm/). This makes it easier to make custom macros and add more features such as single press for x function, double press for y function, hold for z function, etc.
* ~~A prototype - not for sale (yet) - if you would rather buy something like this, [let me know here](https://us7.list-manage.com/survey?u=ac16f42c5affbb6b6658ad19d&id=0ef51ae243) . If there's enough interest, I'll figure out how to mass-produce this~~ I'm not sure if the original creator still intends on doing this, he hasn't been active for a while.

## How to build
### Parts list:
  * 1x standard Cherry MX compatible switch - I used a [Kailh Box Jade](https://novelkeys.xyz/products/novelkeys-x-kailh-box-thick-clicks) for the thick click effect. You may consider an even heavier switch, such as the Kailh Box Navy. (@hotinglok note: I used a Kailh Box Navy. I think something with less than a 70g spring won't work too well. I tried with some 62g Holy Pandas first and the keycap seemed a bit too heavy. I would also like to give special thanks to the guys over at [mechboards.co.uk](https://mechboards.co.uk/) for getting the parts I needed to me so quickly since I needed to make this on time for my coworkers.)
  * 1x 6.25u plate-mounted stabilizer
  * 2x 2u plate-mounted stabilizer
  * 1x Sparkfun Pro Micro, clone, or a microcontroller of your choosing. (@hotinglok note: I used [these](https://www.amazon.co.uk/KeeYees-ATmega32U4-Development-Microcontroller-Bootloader/dp/B07FQBQ4Z6) since they were on sale at the time.)
  * ~~One 10K resistor - 1/4 W worked for me~~ No idea why this was needed.
  * 2x M3x10 countersunk screws. I used some self-tapping screws and without nuts and it holds fine.
  * 1x Micro-usb cable
  * Wires, solder, soldering iron to connect the switch legs to the Pro Micro.
  * (Recommended) Plastic Nippers - The prints I ordered were generally pretty good, but I think the fittings are a bit tight. Too tight for one of my cases for the pro micro clones I had actually. I'm not sure if this is a fault of the .stl file/design or the print itself so I recommend having some nippers or wire cutters to try cut off a tiny bit of the mount where the pro micro goes. Pictures included in the build instructions illustrating this.
  * (Optional) 2x M3 nuts
  * (Optional) 4x Adhesive Anti-slip stickers. Just makes it move around less on the desk.

### Build Instructions (written by @hotinglok):
  1) Print the 3 STL files. I don't have a 3D printer so I used [Champion3d](https://champion3d.com/) as I am based in the UK.
    * The settings I used with them are: 
         * Material: PLA by Filamentive UK
         * Layesr thickness: Standard (200μm)
         * Filling: 25%
        * The keycap (Zoom Leave Meeting Device Keycap) is the only thing you need to print in red    
  * The keycap base (Zoom Leave Meeting Device Keycap Base) slides into the keycap. It's not super secure, there is a bit of play since nothing secures the ends. There are two tabs in the middle of the keycap that holds the base in place. Not a major issue.
  * ### I would seriously recommmend you do NOT attach it straight away. 3D Printing has been a bit hit and miss with the fittings on switches/stabs. Ensure that it fits on your switches/stabs together before sliding it into the keycap. 

  2) Flash the Pro Micro with the .hex file using QMK Toolbox or avrdude directly if QMK Toolbox doesn't work for whatever reason.
      * The Pro Micro uses the Caterina bootloader which makes it a little annoying to work with QMK Toolbox sometimes.
      * To put the Pro Micro into bootloader mode, short (make a connection between) the GND (ground) and RST (reset) pins together. Supposedly you should short it twice in quick succession for the full 8 seconds of it being put in bootloader mode but I've not really had an issue with just shorting it once.
      * I've included the config & keymap files in case you wanted to add in more functionality. Feel free to re-fork this/submit a pull request if you come up with anything interesting that you want to share! 
  
  3) Test the Pro Micro works by shorting the respective pins together. I've mapped them to pins D1 and C6 (2 and 5 printed on the Pro Micro) since you could bend a switch leg just so slightly to just stick in the holes for easy testing. 
      * I would recommend not soldering it just yet. Test that the switches/stabs actually fit on the keycap base first.
      * I've not bothered to make a schematic since it's just a connection from any of the pins to either switch leg. I followed [this guide](https://golem.hu/article/pro-micro-pinout/) to find AVR pinouts for QMK. I think you can use any pin you want since the Pro Micro has an internal pull-up resistor. [This guide](https://www.baldengineer.com/arduino-internal-pull-up-resistor-tutorial.html) explains this more, hence I'm really confused as to why @9gel used a random 10k resistor in his original build.
      
  4) Attach your stabs and single switch to the case. Try and fit the keycap base onto them. I had two made for two coworkers, one keycap base fit more or less perfectly first time, the other I couldn't properly fit the switch into the hole. You might have to play around with screwdrivers/other things to try make the hole a bit wider if the fit is too tight.

  5) Try and fit the Pro Micro into the slot where it goes. Both of miine could not fit at all so I had to cut some of the upper left 'L'-shaped tab off using plastic nippers.
      * Original image - I've left the 'L'-shaped tab on the right as it was and made cuts on the left one. There's no objective fit for this since your print may be more/less precise than mine so I'd recommend just going bit by bit and seeing if the pro micro fits in. 
      * ![IMG_20210418_160220](https://user-images.githubusercontent.com/53564281/116581840-a5206f00-a90c-11eb-95fc-6b18ecc34ee2.jpg)
      * Edited image - I basically tried removing the bottom half of the 'L'. It's a bit messy but this was the point when mine fit flush so I decided it was fine.
      * ![edited shapes](https://user-images.githubusercontent.com/53564281/116582388-3a236800-a90d-11eb-9e6a-c21f5f621268.png)
      * Other angle
      * ![IMG_20210418_160236](https://user-images.githubusercontent.com/53564281/116582474-51faec00-a90d-11eb-8418-6c3768a2bf93.jpg)

  5) After ensuring that everything fits (both onto the case and on the keycap base), place the switch and stabs into the respective slots.  Solder wires to the Pro Micro and the switch legs (the order doesn't matter). I would recommend doing this before putting the Pro Micro into the slot since it can be a real pain to solder/get out if you put it in the slot first.

  6) Remove the keycap base from your stabs/switch if you haven't already. Slide the keycap base into the keycap. I would recommend keeping your thumb on the mounts on the end that you're sliding it in from and then keep it on the central switch mount as you slide it in further.
      * Image to show how to start
      * ![IMG_20210417_222019](https://user-images.githubusercontent.com/53564281/116582819-a43c0d00-a90d-11eb-80f3-09246045bccc.jpg)

  7) Fit the completed keycap on the switch/stabs. Connect it to your computer and test it out. Hopefully everything works (it should)!
## Outstanding items

If you can help out here it will be much appreciated:

* ~~Complete the detailed version of the build~~
* Use [Autohotkey](https://www.autohotkey.com/) for more reliable scripting (@hotinglok note: Might not be needed anymore with QMK?)
* ~~Test on a Mac with different key presses~~
* Add keymaps to make this work on Windows/Linux
* Use a cheaper microcontroller - some suggested digispark / Attiny85
* RGB lighting effects?
* Figure out if I (9gel) should get it mass produced (?)
* Redesign the .stls to address some of minor annoyances in the build process (will detail later)


