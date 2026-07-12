# Kraftor SAM Designer

Browser control surface for the Kraftor SAM firmware. GUI version 1.5 provides live text-to-speech control, MIDI voice shaping, RAM and FRAM sentence-bank editing, printable reference sheets, and a few retro interface skins.

[Open the published app](https://deladriere.github.io/SAM_Designer/)

![Kraftor SAM Designer screenshot](assets/screenshot.png)

## Features

- Speak typed text over USB Serial at 115200 baud.
- Display the connected board model and unique chip ID with firmware 1.2 or newer.
- Identify serial and MIDI connections when several Kraftor boards are connected.
- Shape the SAM voice with Speed, Pitch, Mouth, and Throat controls.
- Select MIDI channels 1–15 for CC, pitch-bend, and Identify MIDI messages.
- Edit RAM sentence slots and FRAM sentence slots when supported by the board.
- Bulk-fill sentence banks from pasted text.
- Print RAM/FRAM MIDI reference sheets.
- Switch between Amiga, HAL 9000, WOPR, Moon 1999, and Alien skins.

## Requirements

- A browser with Web Serial and Web MIDI support, such as Chrome or Edge.
- A Kraftor SAM board running compatible firmware.
- USB connection from the board to the computer.

## Usage

Open `index.html` in a supported browser.

For serial speech:

1. Click `Select port`.
2. Choose the Kraftor USB serial device.
3. Confirm the board model and chip ID shown by the app.
4. Click `Identify Serial` to make that board speak "serial connection".
5. Type text in the live speech field.
6. Click `Speak`.

For MIDI voice control:

1. Click `Connect MIDI`.
2. Allow MIDI access if prompted.
3. Select the MIDI output.
4. Select MIDI channel 1–15 to match the firmware 1.3 DIP switches.
5. Click `Identify MIDI`. The app writes "meedee connection" into temporary RAM
   slot 0 through the selected serial connection, then sends MIDI note 28.
6. Confirm that the expected board speaks.
7. Move the voice controls or choose a preset.

Firmware 1.3 reads its MIDI mode at startup. DIP1 has value 8, DIP2 value 4,
DIP3 value 2, and DIP4 value 1. Set the switches to the binary value of the GUI
channel, then reset or power-cycle Kraftor. All four switches OFF select Omni mode.
The complete switch table is in the [user manual](user_manual.html#midi-dip-switches).

When multiple boards expose the same MIDI name, the selector adds a compact Web MIDI ID
to each duplicate name. Chrome does not expose a guaranteed relationship between a Web
Serial port and a Web MIDI endpoint, so `Identify Serial` and `Identify MIDI` provide a
practical way to match them.

## Firmware Compatibility

- Firmware 1.3 adds DIP-switch MIDI channel selection. GUI 1.5 sends CC, pitch bend,
  and Identify MIDI on the selected channel so it can match the board.
- Firmware 1.2 or newer reports `MODEL=SAM` and the unique SAMD21 chip ID. The app
  displays both after connecting over serial.
- Firmware 1.1 remains compatible with speech, sentence banks, MIDI controls, and both
  identification buttons, but the serial connection label cannot show its model or chip ID.

## Manual

The included [user manual](user_manual.html) has setup details, MIDI mappings, RAM/FRAM behavior, and firmware command notes.

## Project Structure

- `index.html` - Main Kraftor SAM Designer interface.
- `user_manual.html` - Browser-readable user manual.
- `assets/screenshot.png` - Screenshot used by this README.
