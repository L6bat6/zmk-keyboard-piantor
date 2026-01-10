# ZMK Support For Beekeeb Piantor Keyboard

This repository contains shield definition for
[Beekeeb Piantor](https://github.com/beekeeb/piantor) keyboard.

> [!NOTE]
> I have only tested this shield definition with WeAct Studio RP2040 board.

> [!IMPORTANT]
> When using keyboard with this ZMK configuration, left half is defined as the
> main half. So keyboard will only work when left half is plugged in.

> [!WARNING]
> Don’t connect or disconnect the TRRS cable when the keyboard is powered. Always
> disconnect the USB cable first.

Useful links:
* [Piantor documentation](https://docs.beekeeb.com/piantor-keyboard)
* [Piantor repository](https://github.com/beekeeb/piantor)
* [ZMK documentation](https://zmk.dev/docs)
* [ZMK repository](https://github.com/zmkfirmware/zmk)

## ZMK CLI
ZMK CLI is the simplest way to setup config repository with
required modules.

Setup:
1. Create a repository from [unified-zmk-config-template](https://github.com/zmkfirmware/unified-zmk-config-template)
2. [Install ZMK CLI](https://zmk.dev/docs/user-setup#install-zmk-cli)
3. Run `zmk init` and use URL from repository created in 1st step
4. Add required modules
   ```
   zmk module add https://github.com/dani0854/zmk-keyboard-piantor
   zmk module add https://github.com/dani0854/zmk-component-rpi-pico
   ```
   `zmk-component-rpi-pico` module is only needed for hardware metadata files
   since they are currently not in-tree. This should change in v0.4.0, and this
   module will no longer be needed.
5. Add keyboard `zmk keyboard add -k piantor -c rpi_pico`

After that you can edit keymap, commit everything and push, firmware will be
built in GitHub actions. You can even use zmk cli to download built firmware.

[ZMK CLI documentation](https://zmk.dev/docs/zmk-cli)

## Building
### GitHub Actions
Prebuilt firmware is available in GitHub actions artifacts. However, default
keymap is very basic, and this a ZMK module, meant to be included in custom
zmk-config repository, or other.

More information available here:
* [Installing ZMK](https://zmk.dev/docs/user-setup)
* [Modules](https://zmk.dev/docs/features/modules)

### Local
More information available here:
* [Setup](https://zmk.dev/docs/development/local-toolchain/setup)
* [Building and Flashing](https://zmk.dev/docs/development/local-toolchain/build-flash)

## Flashing
There are two uf2 files, for left and right half of keyboard. Hold `BOOTSEL`
when plugging the keyboard half in, then mount disk, copy respective file over,
and unmount. Do it for both halves.

More information available here:
* [Flash the firmware](https://docs.beekeeb.com/piantor-keyboard#flash-the-firmware)
