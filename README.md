ckormanyos/mpir
==================

`ckormanyos/mpir` preserves the _legacy_
[MPIR Library](https://en.wikipedia.org/wiki/MPIR_(mathematics_software))
from William Bart and the MPIR Team.

It appears as though the original [MPIR source code](https://github.com/wbhart/mpir)
has for the most part fallen out of support. `ckormanyos/mpir` preserves
the build of MPIR on VS2022 (and beyond). `ckormanyos/mpir` is, itself,
a fork of [winlibs/mpir](https://github.com/winlibs/mpir).

There are assembly files in this project and they are assembled
to object code using the [YASM assembler](https://github.com/yasm/yasm).
  - Get the YASM assembler.
  - Copy `yasm.exe` to `C:\Program Files\YASMyasm.exe`.
  - Enable the YASM customization as described below.

## YASM _vsprops_

In order to build this project, the so-called _vsprops_ for YASM
are needed. These props basically tell VS how to handle the assembly
files with YASM and define the appropriate command lines needed.
Note that your assembly files need to have the extension `.asm`.
The props from the [ShiftMediaProject/VSYASM](https://github.com/ShiftMediaProject/VSYASM)
project have been successfully used in combination with VS2022.

For the `core2` builds, the YASM props located in the
[`build-vc`](./build-vc) directory have already been preselected.

## Enable the YASM Customization

To enable the YASM customization,
  - Right-click on the project in the Solution Explorer.
  - Select `Build Customizations...`.
  - This will give you a dialog box that allows you to select YASM as the default assembler for `.asm` assembly files.

---
**LEGACY**

Original docs from [winlibs/mpir](https://github.com/winlibs/mpir) follow.

---

# MPIR

MPIR is built using VC9/VC11 projects files. No patch are necessary but to rename
the library to mpir__a.lib. Follow the instructions in the readme.txt in the
MPIR sources and build “lib_mpir_p4” to get the static library we use for PHP.

To build an ASM optimized version, you will have to install
[Yasm](http://www.tortall.net/projects/yasm/) assembler. Complete instructions
are available
[here](http://www.tortall.net/projects/yasm/wiki/VisualStudio2005).

### Building for PHP

PHP 5.4 and below requires the VC9 build of the MPIR library.<br>
PHP 5.5 and above requires the VC11 build of the MPIR library.

* cd win/
* 32 bit
 * configure --cpu=x86
* 64 bit
 * configure --cpu=x86_64 
* building
 * make
 * OR
 * make.vc11

### NOTE

If you plan to run PHP on a specific platform, the MPIR library can use the optimized assembler files. For more information on supported platforms see mpn\README. 
