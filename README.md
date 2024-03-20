# ADV360 Pro ZMK All-in-One Qwerty, Dvorak, Programmer Dvorak Layout

It's a single keyboard layout for the Kinesis Advantage 360 (Adv360) that lets you choose between a bunch of different keyboard layouts.

- Fork it to make your own: [Instructions](https://github.com/KinesisCorporation/Adv360-Pro-ZMK
) (fork this repository instead, though)
- Kinesis's Keymap GUI for your fork: [See here](https://kinesiscorporation.github.io/Adv360-Pro-GUI)
- Just Give me the Firmware: Look at the releases, to the right. Look at the support page for full instructions. Summary: mount left module with mod+(1), drag left into the directory; then, mount right module with mod+(3), drag right into directory.
- Kinesis 360 Pro support page: [see here](https://kinesis-ergo.com/support/kb360pro/)

## Instructions

After you follow the flashing instructions (see the links above), tap the (1) macro key to cycle through the available layouts:

1. qwerty
2. dvorak
3. [programmer dvorak](https://www.kaufmann.no/roland/dvorak/) (I use this)

And some notes:

- **Important**: When multiple layers are activated, the one with the highest number takes priority. They are not stacked. Mod and Fn must be kept at the end of the list. You can create new layers with proper ordering by copying a list item from keymap.json, saving it, then reloading the web configurator.
- You can also tap Mod+LCTRL or Mod+Delete to put LCTRL on Delete, LSHIFT on LCTRL, and DEL on RCTRL. I use that myself, but didn't set it by default to keep the layout vanilla.
- Change unused keys on the base qwerty layer (e.g. the thumb clusters) to apply those changes to all layouts.
- Programmer Dvorak (dvp) based on the way the layout acts on my Linux computer, with the number row keys corrected so that 1 is on the left index finger. Programmer Dvorak changes the shift-behavior of the number row, which I implemented with [ZMK mod-morphs](https://zmk.dev/docs/behaviors/mod-morph) -- `&dvp_` labels in config/dvp_morphs.dtsi. Since the Kinesis web configurator regenerates the keymap every time, I shunted those extra rules into the macros.dtsi file inside of .github/build.yml.
- I estimated a good symbol layout for dvorak, and kept the bracket keys unchanged from qwerty since they're in a non-standard position already.

## Screenshots
Qwerty
![Screenshot_2023-07-24_23-56-31](https://github.com/sabslikesobs/Adv360-Pro-ZMK/assets/57574500/fa9b7276-36e9-459d-ba7d-eedc9cb5a10e)

Dvorak
![Screenshot_2023-07-24_23-48-22](https://github.com/sabslikesobs/Adv360-Pro-ZMK/assets/57574500/c6e0d77f-8694-464f-8fbe-1edac22e5911)

* Either Podman or Docker is required, Podman is chosen if both are installed.
* Make is also required

Programmer Dvorak (pink keys are mod-morph combos for e.g. left-parenthesis with 1 on shift)
![Screenshot_2023-07-24_23-50-48](https://github.com/sabslikesobs/Adv360-Pro-ZMK/assets/57574500/22d6c1fd-43b2-4e89-8531-a25eb69374bb)

* If compiling on Windows use WSL2 and Docker [Docker Setup Guide](https://docs.docker.com/desktop/windows/wsl/).
* Install make using `sudo apt-get install make` inside the WSL2 instance.
* The repository can be cloned directly into the WSL2 instance or accessed through the C: mount point WSL provides by default (`/mnt/c/path-to-repo`).

#### macOS specific

On macOS [brew](https://brew.sh) can be used to install the required components.

* docker
* [colima](https://github.com/abiosoft/colima) can be used as the docker engine

```shell
brew install docker colima
colima start
```
> Note: On Apple Silicon (ARM based) systems you need to make sure to start colima with the correct architecture for the container being used.
> ```
> colima start --arch x86_64
> ```


### Build firmware locally

1. Execute `make` to build firmware for both halves or `make left` to only build firmware for the left hand side.
2. Check the `firmware` directory for the latest firmware build. The first part of the filename is the timestamp when the firmware was built.

### Cleanup

The built docker container and compiled firmware files can be deleted with `make clean`. This might be necessary if you updated your fork from V2.0 to V3.0 and are encountering build failures.

Creating the docker container takes some time. Therefore `make clean_firmware` can be used to only clean firmware without removing the docker container. Similarly `make clean_image` can be used to remove the docker container without removing compiled firmware files.

## Flashing firmware

Follow the programming instruction on page 8 of the [Quick Start Guide](https://kinesis-ergo.com/wp-content/uploads/Advantage360-Professional-QSG-v8-25-22.pdf) to flash the firmware.

### Overview

1. Extract the firmwares from the archive downloaded from the GitHub build job (If using the cloud builder) or the firmware folder (If building locally).
1. Connect the left side keyboard to USB.
1. Press Mod+macro1 to put the left side into bootloader mode; it should attach to your computer as a USB drive.
1. Copy `left.uf2` to the USB drive and it will disconnect.
1. Power off both keyboards (by unplugging them and making sure the switches are off).
1. Turn on the left side keyboard with the switch.
1. Connect the right side keyboard to USB to power it on.
1. Press Mod+macro3 to put the right side into bootloader mode to attach it as a USB drive.
1. Copy `right.uf2` to the mounted drive.
1. Unplug the right side keyboard and turn it back on.
1. Enjoy!

> Note: There are also physical reset buttons on both keyboards which can be used to enter and exit the bootloader mode. Their location is described in section 2.7 on page 9 in the [User Manual](https://kinesis-ergo.com/wp-content/uploads/Advantage360-ZMK-KB360-PRO-Users-Manual-v3-10-23.pdf) and use is described in section 5.9 on page 14. 

> Note: Some operating systems wont always treat the drive as ejected after the settings-reset file is flashed, this doesn't mean that the flashing process has failed.

### Upgrading from V2 to V3

If you encounter a git conflict when updating your repository to V3.0 please follow the instructions on how to resolve it [here](UPGRADE.md).

Updating from V2.0 based firmwares to V3.0 based firmwares can be a rather complex process. There are reset files for every major firmware revision as well as documentation on the update process available [here](https://kinesis-ergo.com/support/kb360pro/#firmware-updates).

## Versioning

Starting on 11/15/2023 the Advantage 360 Pro will now automatically record the compilation date, branch and Git commit hash in a macro that can be accessed with Mod+V. This will type out the following string: YYYYMMDD-XXXX-YYYYYY, where XXXX is the first 4 characters of the Git branch and YYYYYY is the Git commit hash. In addition to this the builds compiled by GitHub actions are now timestamped and also record the commit hash in the filename. 

## Bluetooth LE Privacy

Since the update on 20/10/2023, BLE privacy is now disabled by default and due to an update in upstream ZMK cannot be enabled again as it will cause issues for the split halves connecting to each other. 

Recent updates to MacOS have improved the behaviour for devices without BLE privacy and caused regressions with privacy enabled (e.g. being unable to enter the password on the filevault screen) so BLE privacy is not necessary any more.

## N-Key Rollover

By default this keyboard has NKRO enabled, however for compatibility reasons the higher ranges are not enabled. If you want to use F13-F24 or the INTL1-9 keys with NKRO enabled you can change `CONFIG_ZMK_HID_KEYBOARD_EXTENDED_REPORT=n` to `CONFIG_ZMK_HID_KEYBOARD_EXTENDED_REPORT=y` in [adv360_left_defconfig](/config/boards/arm/adv360/adv360_left_defconfig#L65)

## Battery reporting

By default reporting the battery level over BLE is disabled as this can cause some computers to spontaneously wake up repeatedly. If you'd like to enable this functionality change `CONFIG_BT_BAS=n` to  `CONFIG_BT_BAS=y` in [adv360_left_defconfig](/config/boards/arm/adv360/adv360_left_defconfig#L58). Please note that a known bug in windows prevents the battery level from updating by default, it is only updated when the board is paired. A workaround is to set `CONFIG_BT_GATT_ENFORCE_SUBSCRIPTION=n` in [adv360_left_defconfig](/config/boards/arm/adv360/adv360_left_defconfig). This may cause unexpected results on other OSes

## Changelog

The changelog for both the config repo and the underlying ZMK fork that the config repo builds against can be found [here](CHANGELOG.md).

## Beta testing

The Advantage 360 Pro is always getting updates and refinements. If you are willing to beta test you can follow [this guide from ZMK](https://zmk.dev/docs/features/beta-testing#testing-features) on how to change where your config repo points to. The `west.yml` file that is mentioned is located in config/. [This link](config/west.yml) can take you to the file. Typically you will only need to change the `revision: ` to match the beta branch. The current beta branch is [adv360-z3.2-beta](https://github.com/ReFil/zmk/tree/adv360-z3.2-beta) which is compatible with V3.0 config repositories however users must [disable BT privacy](#bluetooth-le-privacy).

Feedback on beta branches should be submitted as a GitHub issue on the base ZMK repository as opposed to this config repository

In the event of a major update the beta branch may not be compatible with the current mainline version of the config repository. If this is the case it will be detailed here along with instructions on how to update.

## Note

By default this config repository references [a customised version of ZMK](https://github.com/ReFil/zmk/tree/adv360-z3.2) with Advantage 360 Pro specific functionality and changes over [base ZMK](https://github.com/zmkfirmware/zmk). The Kinesis fork is regularly updated to bring the latest updates and changes from base ZMK however will not always be completely up to date, some features such as new keycodes will not be immediately available on the 360 Pro after they are implemented in base ZMK.

Whilst the Advantage 360 Pro is compatible with base ZMK (The pull request to merge it can be seen [here](https://github.com/zmkfirmware/zmk/pull/1454) if you want to see how to implement it) some of the more advanced features (the indicator RGB leds) will not work, and Kinesis cannot provide customer service for usage of base ZMK. Likewise the ZMK community cannot provide support for either the Kinesis keymap editor, nor any usage of the Kinesis custom fork.

## Other support

Further support resources can be found on Kinesis.com:

* https://kinesis-ergo.com/support/kb360pro/#firmware-updates
* https://kinesis-ergo.com/support/kb360pro/#manuals

In the event of a hardware issue it may be necessary to open a support ticket directly with Kinesis as opposed to a GitHub issue in this repository.
* https://kinesis-ergo.com/support/kb360pro/#ticket
