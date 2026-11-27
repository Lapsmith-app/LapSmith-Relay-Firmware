# LapSmith Relay firmware

Published releases of the firmware for the **LapSmith Relay**, a small
Bluetooth relay that sits in the car, wakes a camera and reaches cameras the
phone can't.

**Setting up a new relay?** Plug an M5Stack AtomS3 Lite or Atom Lite into a
computer and install from the setup page, in Chrome or Edge:
<https://relay.lapsmith.app>. Then pair it in the
LapSmith app, under Settings › Bluetooth relays.

The firmware source is private. This repository only carries the release
images, published automatically each time a release is tagged. The LapSmith
app downloads updates from here.

## What each release contains

| File | What it is |
| --- | --- |
| `lapsmith-relay-atom-lite-X.Y.Z.bin` | The image for an M5Stack Atom Lite |
| `lapsmith-relay-atoms3-lite-X.Y.Z.bin` | The image for an M5Stack AtomS3 Lite |
| `lapsmith-relay-atom-lite-X.Y.Z-factory.bin` | Everything for a new Atom Lite, written from 0x0: bootloader, partition table and relay (from 0.1.1) |
| `lapsmith-relay-atoms3-lite-X.Y.Z-factory.bin` | The same for a new AtomS3 Lite |
| `lapsmith-relay-X.Y.Z.json` | Its manifest: version, protocol, commit, and each board's file, size and SHA-256 |
| `latest.json` | The same manifest, under a fixed name |
| `SHA256SUMS` | Checksums of all of the above |

The newest release's manifest is always at:

    https://github.com/Lapsmith-app/LapSmith-Relay-Firmware/releases/latest/download/latest.json

## How an image is checked

Images are not signed. The app checks each download's size and SHA-256
against the manifest. The relay checks the SHA-256 of what it received, and
that the image is for its chip, before switching to it. A new image runs on
trial: if the relay restarts before a phone connects to it, it goes back to
the firmware it had.

## Installing

- **A new board:** the setup page above writes the Latest release's factory
  image over USB. It erases the board, so a relay that is already set up
  forgets every phone: update those over Bluetooth instead. If you do
  reinstall one, first forget LapSmith Relay on each iPhone that used it
  (Settings › Bluetooth), or it can't pair again.
- **Over Bluetooth:** LapSmith offers the update in Settings › Bluetooth
  relays.
- A relay on firmware older than 0.1.0 can't update over Bluetooth and needs
  one USB flash first.
