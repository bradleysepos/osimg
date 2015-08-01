osximg
======

osximg is a Bash script that creates bootable disk images from OS X install files.


Requirements
------------

- OS X 10.9 Mavericks or later suggested
- OS X installer app or `InstallESD.dmg`, Mac OS X 10.7 Lion through OS X 10.11 El Capitan


Installation
------------

Copy `osximg` to a directory in your `PATH` and make it executable.


Usage
-----

osximg must be run using `sudo` to properly apply permissions to the final image.

The basic syntax is:

```
osximg source [destination]
```

*When only source is provided*, osximg prints the source version and exits. This is an easy way to quickly inspect a source for its minor/build version.

*When both source and destination are provided*, osximg prints the source version and creates a bootable disk image from the source.

Say we've downloaded the Yosemite installer from the Mac App Store, and it's in our Applications directory.

```
sudo osximg "/Applications/Install OS X Yosemite.app" "~/OS X Images/"
```

1. Automatically detects the source version, e.g. OS X 10.10.4 Yosemite, Build 14E46
2. If necessary, creates the directory `OS X Images` in our home (`~`) directory
3. Creates the final image `OS X 10.10.4 Yosemite (14E46).iso` in the `~/OS X Images/` directory

If the provided destination is a directory, osximg automatically names the final image according to the source version. Providing a file name as well will override this:

```
sudo osximg "/Applications/Install OS X Yosemite.app" "~/OS X Images/Yosemite.iso"
```

osximg also accepts the `InstallESD.dmg` typically found in `Install*.app/Contents/SharedSupport/` as a source (useful when the installer app has been discarded):

```
sudo osximg InstallESD.dmg Yosemite.iso
```

*It is good practice to keep a backup of the original installer app. Compress/zip it and store it somewhere safe, perhaps alongside disk images produced by osximg.*

Full usage:

```
osximg -h
```


License
-------

Copyright 2015 Bradley Sepos  
Released under the MIT License. See [LICENSE](LICENSE) for details.
