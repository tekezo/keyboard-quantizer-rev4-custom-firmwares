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

## How to update device firmware

-   qmk_firmware
    -   Follow the official instructions.
    -   <https://github.com/sekigon-gonnoc/keyboard-quantizer-doc/blob/master/rev4.md#%E3%83%95%E3%82%A1%E3%83%BC%E3%83%A0%E3%82%A6%E3%82%A7%E3%82%A2%E3%81%AE%E6%9B%B8%E3%81%8D%E8%BE%BC%E3%81%BF>
-   CH559sdccUSBHost
    -   Follow the official instructions.
    -   <https://github.com/sekigon-gonnoc/keyboard-quantizer-doc/blob/master/rev4.md#%E3%83%9B%E3%82%B9%E3%83%88%E7%94%A8%E3%83%95%E3%82%A1%E3%83%BC%E3%83%A0%E3%82%A6%E3%82%A7%E3%82%A2>
    -   Example on macOS.
        -   `python3 ch559update.py flash -p /dev/tty.usbmodem4ce5a667ed6 -f CH559USB_b8a6387.bin -b`

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
