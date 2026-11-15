# TCL 55S434 cleanup kit

Prepared for CleanYourTV (https://github.com/Gathin23/cleanyourtv), based on its tested `examples/tcl-50s434` list.
Not yet run on the TV. Run it from a computer on the same Wi-Fi as the TV.

Dock order: Netflix, YouTube, Prime Video, Play Store.

## Files
- `launcher-config.patch` sets the dock order. It also hides the Live TV app and the TKey tile from the grid, and uses `com.tcl.tv` as Live TV in the Inputs menu.
- `config.json` holds the same settings in theme/example format.
- `debloat.txt` is the 50S434 list, unchanged.

## Steps
1. Turn on Developer options and USB debugging on the TV. Turn on Network/ADB debugging too if it's there.
2. Run `git clone https://github.com/Gathin23/cleanyourtv && cd cleanyourtv`.
3. Run `git apply /path/to/tcl-55s434/launcher-config.patch` and `mkdir -p examples/tcl-55s434 && cp /path/to/tcl-55s434/debloat.txt examples/tcl-55s434/`.
4. Start `claude`, paste PROMPT.md with model "TCL 55S434", and say to use `examples/tcl-55s434/debloat.txt`.

## Check before disabling anything
- Run `adb shell getprop ro.build.fingerprint`. It should contain `C03_4K_NA` and `AR02`. If it doesn't, don't use this list.
- Run `adb shell dumpsys wifi | grep cname`. If it shows `setupwraith`, forget your Wi-Fi network and join it again first.
- Comment out any line in `debloat.txt` for something you use. It turns off Assistant, YouTube Music, Play Movies, Play Games, Gallery and the USB player.

## Undo
`TV_HOST=<tv ip> tools/restore.sh examples/tcl-55s434/debloat.txt`
