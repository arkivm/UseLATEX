Compiling LaTeX files into readable documents is actually a very involved
process. Although CMake comes with FindLATEX.cmake, it does nothing for you
other than find the commands associated with LaTeX. I like using CMake to
build my LaTeX documents, but creating targets to do it is actually a pain.
Thus, I've compiled a bunch of macros that help me create targets in CMake
into a file I call [UseLATEX.cmake](UseLATEX.cmake). Here are some of the
things [UseLATEX.cmake](UseLATEX.cmake) handles:

  * Runs LaTeX multiple times to resolve links.
  * Can run bibtex, makeindex, and makeglossaries to make bibliographies,
    indexes, and/or glossaries.
  * Optionally runs configure on your latex files to replace `@VARIABLE@`
    with the equivalent CMake variable.
  * Automatically finds png, jpeg, eps, and pdf files and converts them to
    formats latex and pdflatex understand.

## Download

The files can be downloaded directly from the UseLATEX project page. If you
are viewing this from a web page, you can follow the following links.

  * Click here to get a copy of [UseLATEX.cmake](https://gitlab.kitware.com/kmorel/UseLATEX/raw/master/UseLATEX.cmake).
  * Click here to get the documentation [UseLATEX.pdf](https://gitlab.kitware.com/kmorel/UseLATEX/raw/master/UseLATEX.pdf).
  
## Repository

This repository contains the CMake macros in the
[UseLATEX.cmake](UseLATEX.cmake) file. To get started, copy this file to
your own LaTeX project and include it in your build process.

You will also find a LaTeX document, [UseLATEX.tex](UseLATEX.tex), that
contains all of the documentation for [UseLATEX.cmake](UseLATEX.cmake). You
will also find a CMake build file, [CMakeLists.txt](CMakeLists.txt), that
uses [UseLATEX.cmake](UseLATEX.cmake) to build
[UseLATEX.tex](UseLATEX.tex). It also serves as a good example for using
[UseLATEX.cmake](UseLATEX.cmake).

There has been some requests to incorporate UseLATEX.cmake into the CMake
repository and distribution. Nobody thinks this is a bad idea, but it
hasn't yet happened mostly out of laziness. Keep bugging me to show
interest in moving UseLATEX.cmake. (See the author contact information at
the top of [UseLATEX.cmake](UseLATEX.cmake).)

## Inkscape support

By default, `convert` from ImageMagick is used to convert svg to pdf, which
ruins the quality. If you need to convert using `inkscape` instead, you can use
this cmake file. By default, it passes `-D -A` flags to inkscape which converts
the drawing area (`-D`) of the svg into PDF (`-A image.pdf`). If you need to
export it differently, modify the flags in the [UseLATEX.cmake](UseLATEX.cmake)
file (seach for `inkscape`).

## TODO
* Add support for gnuplot
