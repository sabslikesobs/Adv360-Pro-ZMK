# ADV360 Pro ZMK Qwerty, Dvorak, Programmer Dvorak Layout

- Fork it to make your own: [Instructions](https://github.com/KinesisCorporation/Adv360-Pro-ZMK
) (fork this repository instead, though)
- Kinesis's Keymap GUI for your fork: [See here](https://kinesiscorporation.github.io/Adv360-Pro-GUI)
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
<img width="1028" alt="image" src="https://github.com/michaelfindlater/Adv360-Pro-ZMK/assets/25244708/a9eadf88-f39b-4e96-b362-88c4968ca77e">

Dvorak
<img width="1028" alt="image" src="https://github.com/michaelfindlater/Adv360-Pro-ZMK/assets/25244708/79a85bff-5e93-4018-81ac-9cdf23498e1d">

Programmer Dvorak (pink keys are mod-morph combos for e.g. left-parenthesis with 1 on shift)
<img width="1033" alt="image" src="https://github.com/michaelfindlater/Adv360-Pro-ZMK/assets/25244708/9dab59b8-9bd2-490a-b78f-4cd20141069a">
