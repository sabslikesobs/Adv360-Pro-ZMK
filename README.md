# ADV360 Pro ZMK All-in-One Qwerty, Colemak, Colemak-DH, Dvorak, Programmer Dvorak, Workman, Workman-P Layout

It's a single keyboard layout for the Kinesis Advantage 360 (Adv360) that lets you choose between a bunch of different keyboard layouts.

- Fork it to make your own: [Instructions](https://github.com/KinesisCorporation/Adv360-Pro-ZMK
) (fork this repository instead, though)
- Kinesis's Keymap GUI for your fork: [See here](https://kinesiscorporation.github.io/Adv360-Pro-GUI)
- Just Give me the Firmware: Look at the releases, to the right. Look at the support page for full instructions. Summary: mount left module with mod+(1), drag left into the directory; then, mount right module with mod+(3), drag right into directory.
- Kinesis 360 Pro support page: [see here](https://kinesis-ergo.com/support/kb360pro/)

## Instructions

After you follow the flashing instructions (see the links above), tap the (1) macro key to cycle through the available layouts:

1. qwerty
2. [colemak](https://colemak.com)
3. [colemak-dh](https://colemakmods.github.io/mod-dh/)
4. dvorak
5. [programmer dvorak](https://www.kaufmann.no/roland/dvorak/) (I use this)
6. [workman](https://workmanlayout.org)
7. [workman-p](https://workmanlayout.org)

And some notes:

- **Important**: When multiple layers are activated, the one with the highest number takes priority. They are not stacked. Mod and Fn must be kept at the end of the list. You can create new layers with proper ordering by copying a list item from keymap.json, saving it, then reloading the web configurator.
- You can also tap Mod+LCTRL or Mod+Delete to put LCTRL on Delete, LSHIFT on LCTRL, and DEL on RCTRL. I use that myself, but didn't set it by default to keep the layout vanilla.
- I don't use Colemak or Workman but threw them in there to be helpful. I hope it works right.
- Change unused keys on the base qwerty layer (e.g. the thumb clusters) to apply those changes to all layouts.
- Programmer Dvorak (dvp) based on the way the layout acts on my Linux computer, with the number row keys corrected so that 1 is on the left index finger. Programmer Dvorak changes the shift-behavior of the number row, which I implemented with [ZMK mod-morphs](https://zmk.dev/docs/behaviors/mod-morph) -- `&dvp_` labels in config/dvp_morphs.dtsi. Since the Kinesis web configurator regenerates the keymap every time, I shunted those extra rules into the macros.dtsi file inside of .github/build.yml.
- I estimated a good symbol layout for dvorak, and kept the bracket keys unchanged from qwerty since they're in a non-standard position already.
- I didn't really verify workman-p or colemak-dh very much.

## Screenshots
Qwerty
![Screenshot_2023-07-24_23-56-31](https://github.com/sabslikesobs/Adv360-Pro-ZMK/assets/57574500/fa9b7276-36e9-459d-ba7d-eedc9cb5a10e)

Colemak
![Screenshot_2023-07-24_23-52-10](https://github.com/sabslikesobs/Adv360-Pro-ZMK/assets/57574500/013a2325-04d3-4c9c-b66d-767eedd28308)

Colemak-DH
![Screenshot_2023-07-29_16-25-14](https://github.com/sabslikesobs/Adv360-Pro-ZMK/assets/57574500/b3f2a185-70ae-4ef9-8545-8515f6783472)

Dvorak
![Screenshot_2023-07-24_23-48-22](https://github.com/sabslikesobs/Adv360-Pro-ZMK/assets/57574500/c6e0d77f-8694-464f-8fbe-1edac22e5911)

Programmer Dvorak (pink keys are mod-morph combos for e.g. left-parenthesis with 1 on shift)
![Screenshot_2023-07-24_23-50-48](https://github.com/sabslikesobs/Adv360-Pro-ZMK/assets/57574500/22d6c1fd-43b2-4e89-8531-a25eb69374bb)

Workman
![Screenshot_2023-07-29_16-25-31](https://github.com/sabslikesobs/Adv360-Pro-ZMK/assets/57574500/07c0de62-8c28-4a1f-ace1-e8967154de47)

Workman-P
![Screenshot_2023-07-29_16-25-48](https://github.com/sabslikesobs/Adv360-Pro-ZMK/assets/57574500/651da268-70c6-4582-a789-25d08ee5554d)
