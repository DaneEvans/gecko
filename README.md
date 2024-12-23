# Gecko keyboard
Somewhere between the corne, and the sofle. 

Adding several small thumbwheels, as full size encoders are too big. 

The Gecko uses CRKBD as a base, 
Add a few extra keys to the bottom row, useful for mute / sleep etc, and find space one or more small wheel encoder. 


# Parts required
## PCBAs
- These can be ordered through pcbway? 
- <list settings here> 
Based on the options available / cost, I went with back side only (only the USB is on the front), and missed both the Kailh Hotswap sockets, and the LEDs. 

## Parts list
*Boards*
- PCBA's, pair (see above)
- top plate, pair, 1.2mm 
- Bottom plate, pair (or alternate case)

*PCBA* 
- 2x USB Sockets (TYPE-C-31-M-13C)
- 2x audio sockets (PJ-398A-5A_PJ-399B-6A)
- 4x Scroll wheel encoders (EC05E) (optional)
- 46x LEDs (SK6812MINI-E) (optional)
- 2x OLED displays (optional)

*Tools* 
- Soldering iron, fine tip, solder etc. 
- Screwdriver for the bolts

*Assembly* 
- M2 standoffs (min 8mm? ) x 10? 
- M2 flat ended bolts, max length standoff height/2   x10
- 3 wire cable assembly(3.5mm male - 3.5mm male)

*Keys*
- 46 x Kailh hotswap sockets ()
- 46 x Choc V1 switches (any variety you like)
- 46 x Choc V1 keycaps (all singles is fine, or 2 x 1.5U)


# Assembly instructions

## Electrics

- Find parts
- Assemble PCBA's 
  - Bottom side
    - install USB-C ports
    - install TRS connectors
    - install hotswap switch plates
    - install Mini-E LED's (optional) 
  - Top side 
    - install encoders
    - install OLED display

## Mechanics
- Take a top plate and attatch M2 standoffs to it's bottom surface. (I use loctite)
- place the corner switches into the top plate
- add the PCB (care of the pins)
- Add the rest of the switches
- If you plan to use the tenting kit, add standoffs to the bottom of the bottom plate in the additional holes.
- place the bottom plate on the assembly, and tighten the bolts.

# Programming
Now test that everything is working 
- Recognisable on USB.
- All key presses etc. 
- encoders
- LED's
- OLEDs, 


Get the QMK firmware from (here)
this is the keymap ()
follow programming directions (here)

Once you know 


# Known Issues: 
- The encoder cutouts for the horizontal wheels aren't big enough - if you want to use them, you will need to modify the top plate.

- Always unplug the USB before the 3.5mm connector - the 3.5mm has the potential to short out the board, and fry the mcu. 

# Troubleshooting
Odds are, any issues will be in the parts you soldered.

If you can't communicate with an MCU to program it, it's likely the USB-C

If the two halves won't communicate, it's the TRS connectors or cable.

The LED's are often very fiddly, and I won't offer any guidance on them, they do not effect the usage of the keyboard, and are a tedious job to get working. 

# Programming 

## Flashing 
Flashing is simple drag and drop. 
The tagged release that I currrently use is [here](https://github.com/DaneEvans/qmk_firmware/releases/tag/gecko_devdev_1.0)
*On Windows* 
- Plug the keyboard half in. 
- Reset if needed (hardware button, or a key combination)
- It should initialise as a RPi storage device 
- Drag the firmware file to it (*.uf2)
- The window will close and the keyboard will reboot with the new firmware. 

## Configuring Firmware
The firmware uses QMK, My fork is located [here](https://github.com/DaneEvans/qmk_firmware) Use the keyboard/gecko branch, or a tagged release to base changes on. 

### To build on Windows
Use QMK WSL 
- get the git repo https://github.com/DaneEvans/qmk_firmware
- use the keyboards/gecko branch. 
- `qmk build -kb gecko -km devdev`
- Navigate to the /Linux/QMK/home/qmk/qmk_firmware directory (Where QMK WSL resides)
- Copy the keyboard_xxx.uf2 file to the keyboard halves. 
