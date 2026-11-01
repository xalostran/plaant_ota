# Plaant OTA firmware

This repository hosts the ESP32 firmware binary and the manifest used by an
OTA client to discover and verify an update.

## Manifest

OTA clients should fetch:
`https://raw.githubusercontent.com/xalostran/plaant_ota/main/manifest.json`

`manifest.json` contains:

- `version`: version embedded in the firmware.
- `url`: HTTPS URL from which the OTA client downloads the binary.
- `sha256`: lowercase SHA-256 digest of the complete binary.
- `size`: binary size in bytes.

The OTA client must use these same field names and verify the checksum and
size before installing the firmware.

## Publishing a firmware update

1. Build the firmware with its intended version embedded in the image.
2. Name the binary `esp32_firmware/firmware-v<VERSION>.bin`.
3. Update `version`, `url`, `sha256`, and `size` in `manifest.json`.
4. Push both files to the `main` branch.

The current binary identifies itself as version `1.0.0` and targets the
ESP32-S3. Its filename, manifest URL, size, and SHA-256 are aligned with that
version.
