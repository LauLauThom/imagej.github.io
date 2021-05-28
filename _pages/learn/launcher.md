---
mediawiki: Launcher
title: ImageJ Launcher
nav-links: true
nav-title: Launcher
---

The ImageJ launcher is a native application for launching ImageJ.

## Introduction

The launcher supports the following flavors of ImageJ:

-   [ImageJ1](/software/imagej1)
-   [ImageJ2](/software/imagej2)
-   [Fiji](/software/fiji)

The launcher is a native executable whose purpose is to start up a Java Virtual Machine and run ImageJ 1.x, Fiji or ImageJ2 in it. It is used in the [Fiji](/software/fiji) distribution as well as in [ImageJ2](/software/imagej2).

## Source

The ImageJ launcher source code lives {% include github org='imagej' repo='imagej-launcher' %}.

## Purpose

The launcher provides a platform-specific entry point into the ImageJ Java application. Its most major function is to facilitate the ImageJ Updater feature by taking care of pending updates when ImageJ is first launched.

## Usage

For an overview of supported options, run:

```
./ImageJ-xyz --help
```

where `xyz` is your platform.

The launcher can do all kinds of things, like:

-   Launch ImageJ with a different amount of memory (`--mem` option)
-   Run [macros and scripts in headless mode](/learn/headless)
-   Control the [Updater](/plugins/updater) from the command line
-   Open images: `./ImageJ-<platform> example.jpg`
-   Call Jython scripts: `./ImageJ-<platform> example.py` (also works for JRuby scripts when they have an `.rb` extension, for Beanshell scripts with `.bsh` extension, `.clj` for Clojure and `.js` for Javascript)
-   Call the Jython interpreter: `./ImageJ-<platform> --jython` (the classpath will be the same as when calling ImageJA), and likewise `--jruby`, `--bsh` and `--js` for the respective language's command-line interpreters
-   Run Fiji with the system Java instead of its own one: `./ImageJ-<platform> --system`. But beware: this might fail since some plugins need at least Java 1.5, and the 3D viewer needs Java3D.
-   Show the java command line instead of running Fiji: `./ImageJ-<platform> --dry-run`
-   Compile a Java class: `./ImageJ-<platform> --javac example.java`
-   Run a Java class' main() method: `./ImageJ-<platform> --main-class=example`
-   Pass some [Java options](/Java_Options): `./ImageJ-<platform> -server --` (everything that comes before a `--` is interpreted as Java option)
-   Add `.` to the classpath and execute the given class' `main()` method: `./ImageJ-<platform> Example.class`
-   Link Fiji into the PATH: `ln -s $(pwd)/ImageJ-<platform> $HOME/bin/fiji && fiji`
-   Start Fiji and run a menu entry directly: `./ImageJ-<platform> --run System_Clipboard` (the underscore was used in place of a space to avoid having to quote the argument)

## Download

The launcher comes with ImageJ1, ImageJ2 and Fiji.

If you want to test the latest UNSTABLE version, it can downloaded here:

| [![ alt=Windows (32-bit) \| link=https://maven.scijava.org/service/local/artifact/maven/redirect?r=snapshots&g=net.imagej&a=imagej-launcher&v=LATEST&e=exe&c=win32>](/media/icons/windows.svg){:width="24px"} ImageJ-win32.exe](https://maven.scijava.org/service/local/artifact/maven/redirect?r=snapshots&g=net.imagej&a=imagej-launcher&v=LATEST&e=exe&c=win32) | ![ alt=Windows (64-bit) \| link=<https://maven.scijava.org/service/local/artifact/maven/redirect?r=snapshots&g=net.imagej&a=imagej-launcher&v=LATEST&e=exe&c=win64> ](/media/icons/windows.svg){:width="24px"} [ImageJ-win64.exe](https://maven.scijava.org/service/local/artifact/maven/redirect?r=snapshots&g=net.imagej&a=imagej-launcher&v=LATEST&e=exe&c=win64) | ![ alt=macOS \| link=https://maven.scijava.org/service/local/artifact/maven/redirect?r=snapshots&g=net.imagej&a=imagej-launcher&v=LATEST&e=exe&c=macosx ](/media/icons/macos.png){:width="24px"} [ImageJ-macosx](https://maven.scijava.org/service/local/artifact/maven/redirect?r=snapshots&g=net.imagej&a=imagej-launcher&v=LATEST&e=exe&c=macosx) | ![ alt=Linux (64-bit) \| link=<https://maven.scijava.org/service/local/artifact/maven/redirect?r=snapshots&g=net.imagej&a=imagej-launcher&v=LATEST&e=exe&c=linux64 ](/media/icons/linux.svg){:width="24px"} [ImageJ-linux64](https://maven.scijava.org/service/local/artifact/maven/redirect?r=snapshots&g=net.imagej&a=imagej-launcher&v=LATEST&e=exe&c=linux64) |

After download, rename to match the filename given above. For macOS and Linux binaries, set the executable bit using `chmod +x`. Then replace the launcher with the new one, keeping a backup of the previous launcher in case the new one does not work.