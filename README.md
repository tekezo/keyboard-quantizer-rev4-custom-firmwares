# Custom firmwares for Keyboard Quantizer rev4

## Files

-   [keyboard_quantizer_rp_e34d270.uf2](files/keyboard_quantizer_rp_e34d270.uf2)
-   [CH559USB_b8a6387.bin](files/CH559USB_b8a6387.bin)

## Changes

-   qmk_firmware
    -   Disable debounce.
    -   Disable system_report_parser, consumer_report_parser, vendor_report_parser in order to avoid an issue that RollerMouse Mobile prevents macOS sleep.
-   CH559sdccUSBHost
    -   Disable delay in the main loop to prevent RollerMouse Mobile input events from being dropped.

---

## Repositories

-   qmk_firmware
    -   <https://github.com/tekezo/qmk_firmware/tree/rp2040-tekezo>
-   CH559sdccUSBHost
    -   <https://github.com/tekezo/CH559sdccUSBHost/tree/quantizer_ex-tekezo>

## How to build firmwares

### qmk_firmware

Run the following commands on Ubuntu 22.04.

```shell
cd qmk_firmware

SERIAL_NUMBER=$(git rev-parse --short HEAD) make keyboard_quantizer/rp:default:uf2
```

### CH559sdccUSBHost

Run the following commands on Ubuntu 22.04.

```shell
sudo apt install -y sdcc

cd CH559sdccUSBHost

make
```
