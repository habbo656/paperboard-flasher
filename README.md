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
  for the NM-EPD-420 (the Wi-Fi settings area is left alone).
- `source/paperboard-firmware-<version>-src.tar.gz`: the corresponding source of the firmware.

## Licence

The firmware binaries contain GxEPD2 (GPL-3.0), so they are distributed under the GPL-3.0; the corresponding source is
the tarball in `source/`. They also contain the LGPL-2.1 Arduino cores for ESP8266 and ESP32 and Apache-2.0 ESP-IDF
parts. The project's own code is MIT. Licences of all components: `THIRD_PARTY.md` inside the tarball.
