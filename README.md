# ADV360 Pro ZMK All-in-One Qwerty, Colemak, Dvorak, Programmer Dvorak Layout

It's a single keyboard layout for the Kinesis Advantage 360 (Adv360) that lets you choose between Qwerty, Colemak, Dvorak (dvk), and Programmer Dvorak (dvp).

- Fork it to make your own: [Instructions](https://github.com/KinesisCorporation/Adv360-Pro-ZMK
) (fork this repository instead, though)
- Kinesis's Keymap GUI for your fork: [See here](https://kinesiscorporation.github.io/Adv360-Pro-GUI)
- Just Give me the Firmware: Look at the releases, to the right. Look at the support page for full instructions. Summary: mount left module with mod+(1), drag left into the directory; then, mount right module with mod+(3), drag right into directory.
- Kinesis 360 Pro support page: [see here](https://kinesis-ergo.com/support/kb360pro/)

Instructions: Tap the (1) macro key to cycle through the available layouts:

1. qwerty
2. [colemak](colemak.com)
3. dvorak
4. [programmer dvorak](https://www.kaufmann.no/roland/dvorak/) (I use this)

And some notes:

- You can also tap Mod+LCTRL or Mod+Delete to swap LCTRL and Delete. I use that myself but didn't set it by default to keep the layout vanilla.
- I don't use Colemak but threw it in there to be helpful. I hope it works right.
- Change unused keys on the base qwerty layer (e.g. the thumb clusters) to apply those changes to all layouts.
- Programmer Dvorak (dvp) is based on the way the layout acts on my Linux computer, with the number row keys corrected so that 1 is on the left index finger. Programmer Dvorak changes the shift-behavior of the number row, which I implemented with [ZMK mod-morphs](https://zmk.dev/docs/behaviors/mod-morph) -- `&dvp_` labels in config/dvp_morphs.dtsi. Since the Kinesis web configurator regenerates the keymap every time, I shunted those extra rules into the macros.dtsi file inside of .github/build.yml.
- I estimated a good symbol layout for dvorak, and kept the bracket keys unchanged from qwerty since they're in a non-standard position already. It looks like this, where blank keys are identical to the default qwerty layout:

![Screenshot_2023-07-24_23-48-22](https://github.com/sabslikesobs/Adv360-Pro-ZMK/assets/57574500/c6e0d77f-8694-464f-8fbe-1edac22e5911)
