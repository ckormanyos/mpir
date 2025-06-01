ckormanyos/mpir
==================

`ckormanyos/mpir` preserves the _legacy_
[MPIR Library](https://en.wikipedia.org/wiki/MPIR_(mathematics_software))
from William Bart and the MPIR Team. The projects `x86_64w/core2`
and `gc` (the generic project) and also the C++ wrapper `cxx`
have been included as solution build configurations. Both the `lib`
as well as the `dll` configurations are available for all of these.
An optional test program using the wrapped `gmp_float` type
from `Boost.Multiprecision` is also included for optional use.

It appears as though the original [MPIR source code](https://github.com/wbhart/mpir)
has for the most part fallen out of support. `ckormanyos/mpir` preserves
the build of MPIR on VS2022 (and beyond). `ckormanyos/mpir` is, itself,
was initially creadet as a fork of [winlibs/mpir](https://github.com/winlibs/mpir).
`ckormanyos/mpir` is now separated as a standalone repo.

There are assembly files in this project and they are assembled
to object code using the [YASM assembler](https://github.com/yasm/yasm).
  - The `core2` builds have been modified to use a [local copy of YASM](./build.vc/yasm/1.3.0).
  - The YASM customization has been set to use the _vsprops_ for YASM that are located in the [build.vc](./build.vc) directory.
  - For other build configurations (if these are activated), you'll still need to enable the YASM customization as described below.

## YASM _vsprops_

In order to build the `core2` configurations of the project,
the so-called _vsprops_ for YASM are needed.
These props basically tell VS how to handle the assembly
files with YASM and define the appropriate command lines needed.
Note that your assembly files need to have the extension `.asm`.

The props from the [ShiftMediaProject/VSYASM](https://github.com/ShiftMediaProject/VSYASM)
project have been successfully used in combination with VS2022.

## Enable the YASM Customization

To enable the YASM customization,
  - Right-click on the project in the Solution Explorer.
  - Select `Build Dependenciess...` and `Build Customizations...` to get to a dialog box that allows you to select YASM as the default assembler for `.asm` assembly files.
  - Check the appropriate box for the props or navigate to it and then select it.

## Continuous Integration

Continuous Integration (CI) runs on `windows-latest` using the
generic configuration `lib_mpir_gc`. The test program using
the wrapped `gmp_float` type from `Boost.Multiprecision`
is built and executed and its results are verified in CI the pipeline.

## Legacy and Origins

The [MPIR Library](https://en.wikipedia.org/wiki/MPIR_(mathematics_software))
itself is forked from the original
[GMP project](https://en.wikipedia.org/wiki/GNU_Multiple_Precision_Arithmetic_Library),
the GNU Multiple Precision Arithmetic Library.

Original docs from [wbhart/mpir](https://github.com/wbhart/mpir) and
[winlibs/mpir](https://github.com/winlibs/mpir) can be found at
their repository homes.
Some of the links in the some of these original docs,
however, seem to be broken at the moment.
