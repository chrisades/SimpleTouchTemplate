# SIMPLE TOUCH TEMPLATE
This is a barebones template for quick and dirty C++ development to get some sounds going on the [Synthux SimpleTouch](https://www.synthux.academy/store/touch-2-kit) platform. If you want to see an example of an instrument built using this template as a base, please see [ZoscTouch](https://github.com/chrisades/ZoscTouch).

The hardware peripheral logic and the rest of this README below was adapted from official Synthux projects like [TouchBass](https://github.com/Synthux-Academy/TouchBass) and [TouchString](https://github.com/Synthux-Academy/TouchString).

## CONTROLS
<img src="touch.jpeg" width="300"/>

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