# Kraftor SAM Designer

Browser control surface for the Kraftor SAM firmware. It provides live text-to-speech control, MIDI voice shaping, RAM and FRAM sentence-bank editing, printable reference sheets, and a few retro interface skins.

[Open the published app](https://deladriere.github.io/SAM_Designer/)

![Kraftor SAM Designer screenshot](assets/screenshot.png)

## Features

- Speak typed text over USB Serial at 115200 baud.
- Shape the SAM voice with Speed, Pitch, Mouth, and Throat controls.
- Send MIDI CC and pitch-bend messages to the firmware.
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
3. Type text in the live speech field.
4. Click `Speak`.

For MIDI voice control:

1. Click `Connect MIDI`.
2. Allow MIDI access if prompted.
3. Select the MIDI output.
4. Move the voice controls or choose a preset.

When multiple boards expose the same MIDI name, the selector adds a compact Web MIDI ID
to each duplicate name. This distinguishes the browser endpoints, but does not establish
which MIDI endpoint belongs to a particular serial port. Reliable automatic pairing
requires each board to expose a unique USB serial number or unique MIDI product name.

## Manual

The included [user manual](user_manual.html) has setup details, MIDI mappings, RAM/FRAM behavior, and firmware command notes.

## Project Structure

- `index.html` - Main Kraftor SAM Designer interface.
- `user_manual.html` - Browser-readable user manual.
- `assets/screenshot.png` - Screenshot used by this README.
