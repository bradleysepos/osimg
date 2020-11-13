osimg
=====

osimg is a Bash script that creates bootable disk images from macOS install files.


Requirements
------------

- Mac OS X 10.7 Lion through macOS 10.15 Catalina installer app or `InstallESD.dmg`†
- OS X 10.9 Mavericks or later host system

While the installer for macOS 11 Big Sur is properly identified, creating a bootable disk image is not yet possible using `osimg`. In the meantime, you may find Apple's `createinstallmedia` of use; see [https://support.apple.com/en-us/HT201372](https://support.apple.com/en-us/HT201372).

Installation
------------

Copy `osimg` to a directory in your `PATH` and make it executable.


Usage
-----

osimg must be run using `sudo` to properly apply permissions to the final image.

The basic syntax is:

```
osimg source [destination]
```

*When only source is provided*, osimg prints the source version and exits. This is an easy way to quickly inspect a source for its minor/build version.

*When both source and destination are provided*, osimg prints the source version and creates a bootable disk image from the source.

Say we've downloaded the Sierra installer from the Mac App Store, and it's in our Applications directory.

```
sudo osimg "/Applications/Install macOS Sierra.app" ~/"OS Images/"
```

1. Automatically detects the source version, e.g. macOS 10.12 Sierra, Build 16A323
2. If necessary, creates the directory `OS Images` in our home (`~`) directory
3. Creates the final image `macOS 10.12 Sierra (16A323).iso` in the `~/OS Images/` directory

If the provided destination is a directory, osimg automatically names the final image according to the source version. Providing a file name will override this behavior:

```
sudo osimg "/Applications/Install macOS Sierra.app" ~/"OS Images/Sierra.iso"
```

osimg also accepts the `InstallESD.dmg` typically found in `Install*.app/Contents/SharedSupport/` as a source (useful when the installer app has been discarded)†:

```
sudo osimg InstallESD.dmg Sierra.iso
```

*It is good practice to keep a backup of the original installer app. Compress/zip it and store it somewhere safe, perhaps alongside disk images produced by osimg.*

Full usage:

```
osimg -h
```

† *As of macOS 10.13 High Sierra, `BaseSystem.dmg` is located alongside, rather than within, `InstallESD.dmg`. For this reason, it is recommended to use osimg with the main installer app.*


License
-------

Copyright 2020 Bradley Sepos  
Released under the MIT License. See [LICENSE](LICENSE) for details.
