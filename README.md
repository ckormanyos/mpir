ckormanyos/mpir
==================

`ckormanyos/mpir` preserves a _legacy_ library. It appears as though the original
[mpir](https://github.com/wbhart/mpir)
has for the most part fallen out of support. `ckormanyos/mpir` preserves
the MSVC build of mpir on MSVC 2022 (and beyond). `ckormanyos/mpir` is, itself,
a fork of [winlibs/mpir](https://github.com/winlibs/mpir).

There are assembly files in this project and they are assembled
to object code using the [yasm assembler](https://github.com/yasm/yasm).

In order to build this project, the so-called _vsprops_ for yasm
are needed. These props basically tell VS how to handle the assembler
files (having extension .asm) with yasm. The props from
[ShiftMediaProject/VSYASM](https://github.com/ShiftMediaProject/VSYASM).

After installing the props, you must still enable the customization
by right clicking on the project in the Solution Explorer
and select 'Build Customisations..'.
This will give you a dialog box that allows you to select YASM as an assembler
(note that your assembly files need to have the extension '.asm').

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
