# Paperboard web flasher

This repository is the public flasher site of [Paperboard](https://github.com/habbo656/paperboard) (a 4.2" e-paper
dashboard for Homey Pro): a web page (GitHub Pages) that installs the Paperboard firmware on a D1 mini or an
NM-EPD-420 board from Chrome or Edge, using [ESP Web Tools](https://github.com/esphome/esp-web-tools) (Apache-2.0,
vendored in `vendor/esp-web-tools/`).

Everything here is generated from the main project (`flasher/` of the source repository, published by
`tools/publish-release.sh`). Do not edit it by hand.

- `index.html`, `manifest-<board>.json`: the page and the ESP Web Tools manifests.
- `firmware/paperboard-<board>-<version>-factory.bin`: image for flash offset 0 (D1 mini: the normal image,
  NM-EPD-420: merged bootloader, partition table, otadata and app; for esptool only).
- `firmware/paperboard-nm_epd_420-<version>-{bootloader,partitions,boot_app0,app}.bin`: the parts the web flasher writes
  for the NM-EPD-420 (and likewise `nm_epd_420_4c`) (the Wi-Fi settings area is left alone).
- `source/paperboard-firmware-<version>-src.tar.gz`: the corresponding source of the firmware.

## Running the page locally

Web Serial only works over HTTPS or from `localhost`, so a local copy needs a small web server:

1. Start it in the folder that contains `index.html`: `python3 -m http.server` (in the source repository:
   `python3 -m http.server -d flasher`).
2. Open `http://localhost:8000` in Chrome or Edge.
3. ESP32-S3 boards (NM-EPD-420, NM-EPD-420-4C): if the port does not show up or the install fails to connect, enter
   ROM download mode first – hold BOOT, press RESET, release BOOT.
4. Click the install button of your board and pick its USB port.
5. After the install, press RESET or replug the USB cable if the board does not restart by itself.
6. Stop the server with Ctrl-C.

## Licence

The firmware binaries contain GxEPD2 (GPL-3.0), so they are distributed under the GPL-3.0; the corresponding source is
the tarball in `source/`. They also contain the LGPL-2.1 Arduino cores for ESP8266 and ESP32 and Apache-2.0 ESP-IDF
parts. The project's own code is MIT. Licences of all components: `THIRD_PARTY.md` inside the tarball.
