
## My shop keyboard-hoarders.com and keyboardhoarders.etsy.com -

![lily](https://github.com/user-attachments/assets/41c643e3-44f1-4863-9274-2a0181e748f5)

# Flashing firmware:
1.Leave both halves powered on.

2.Plug in right half via USB to computer.  > Press the reset button on the inner halves twice quickly to put into bootloader mode. > Drag and drop the settings_reset file into the directory NICENANO. > After transfer you may get an error and you can ignore and move on to next step. > Unplug right half

3.Plug in left half and follow step one to put into bootloader and drag and drop settings-reset file. > after transfer leave left plugged in. 

4.With left still plugged in put into bootloader again > drag and drop lily-left firmware into directory. > unplug left half.

5.Plug in right half and follow step 3 but this time drag and drop lily58-right firmware.

6.After this your done.  You will need to go into your computers bluetooth device history and remove your old pairing on Lily58 and pair it as a new device.

# keymap


<img width="984" height="1173" alt="414038139-877a66fd-3059-4b77-a9e4-e73b154922ca" src="https://github.com/user-attachments/assets/2a5678f7-cc8e-49db-ae4c-32e0522eabca" />


# Trackpad (Azoteq TPS43)

The right half has an Azoteq TPS43 trackpad instead of a nice!view display.
It's wired through the PCB's OLED header (now free since this half has no
screen) plus two spare pads on the nice!nano itself:

| TPS43 pin | nice!nano pad |
|---|---|
| VDD | 3V (OLED header) |
| GND | GND (OLED header) |
| SDA | D2 (OLED header "SDA/MOSI" pad) |
| SCL | D3 (OLED header "SCL/SCK" pad) |
| RDY | D21 |
| RST | D20 |

After changing `config/west.yml` you'll need to run `west update` (or let
the GitHub Action do it) to pull in the trackpad driver module before
building.

Cursor movement, scrolling, tap-to-click, two-finger right-click,
press-and-hold drag, pinch-to-zoom, and 4-direction swipes all work out of
the box. If the cursor is inverted or the axes are swapped once you flash
it, adjust the commented-out `switch-xy` / `invert-x` / `invert-y` /
`invert-scroll-y` properties in `config/lily58_right.overlay` to match how
the module ends up mounted. Swipe/zoom shortcuts default to
Windows/Linux-style bindings; flip the `TRACKPAD_WIN_MODE` define at the
top of `config/lily58_left.overlay` for macOS-style shortcuts instead.

# Bluetooth
ZMK uses secure bluetooth profiles.  This means only one device per profile.  If you run into bluetooth issues I recommend wiping the stored profiles with BT_CLR_ALL button combo thats found on the lower layer.  If you want to flash your own firmware I have a guide on my website over at https://keyboard-hoarders.com/pages/guides-1
