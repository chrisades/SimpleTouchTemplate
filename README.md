# SIMPLE TOUCH TEMPLATE
This is a barebones template for quick and dirty C++ development to get some sounds going on the [Synthux SimpleTouch](https://www.synthux.academy/store/touch-2-kit) platform. If you want to see an example of an instrument built using this template as a base, please see [ZoscTouch](https://github.com/chrisades/ZoscTouch).

The hardware peripheral logic and the rest of this README below was adapted from official Synthux projects like [TouchBass](https://github.com/Synthux-Academy/TouchBass) and [TouchString](https://github.com/Synthux-Academy/TouchString).

## CONTROLS
<img src="touch.jpeg" width="300"/>

All of these get read in the main loop and stored in global variables, so you can use them anywhere (including `AudioCallback`).

- **Touch pads (12):** Read from the MPR121 over I2C and numbered 0 to 11. `OnPadTouch(int pad)` runs when a pad is touched and `OnPadRelease(int pad)` runs when it's let go. Put your code in those, or check `padPressed[]` to see which pads are being held down.
- **Switches (2):** Two 3-way switches, A (S09/S10) and B (S07/S08). `switchAValue` and `switchBValue` are `2` for left, `0` for center and `1` for right.
- **Pots (8):** Pots 0 to 7 are on A0 to A7 (S30 to S37), in order. `potValue[]` holds each one as a float from 0 to 1.

## PREREQUISITES
- [Daisy Toolchain](https://docs.daisy.audio/tutorials/cpp-dev-env/) (ARM GCC + make)
- **Windows:** use [Git Bash](https://git-scm.com/downloads) to run the commands below — cmd and PowerShell won't work

## PROJECT SETUP
```shell
$ git clone --recurse-submodules https://github.com/chrisades/SimpleTouchTemplate.git
$ cd SimpleTouchTemplate/lib/libDaisy
$ make
$ cd ../DaisySP
$ make
$ cd ../..
$ make clean; make
```

If you already have the repo cloned without submodules, run this first:
```shell
$ git submodule update --init --recursive
```

## UPLOAD
```shell
$ make program-dfu
```

> [!NOTE]
> When tweaking code, run `make clean && make` for a full rebuild, or just `make` for an incremental rebuild (only recompiles changed files). The compiled binary is placed in the `build/` folder as `Template.bin`.
