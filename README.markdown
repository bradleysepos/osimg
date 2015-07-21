osximg
======

Create bootable disk images from OS X install files.

Requires a recent version of OS X, `bash` (hint: `Terminal.app`), and a Mac OS X 10.7 Lion through OS X 10.11 El Capitan installer app or corresponding `InstallESD.dmg`.

Usage
-----

In order to properly apply the original installer's permissions when creating a new image, `osximg` must be run as the [root user](https://support.apple.com/en-us/HT204012). The easiest and safest way to run a single command as root is using `sudo`. Only Admin users can do this.

Let's assume we've downloaded the Yosemite installer from the Mac App Store, and it's in our Applications directory. We'll prefix our command with `sudo` (and enter our OS X password when prompted) in order to run `osximg` as root, followed by the paths to the OS X installer app and where we want to put our final image:

```
$ sudo osximg "/Applications/Install OS X Yosemite.app" "~/OS X Images/"
```

This will:

1. Automatically detect the installer version, e.g. OS X 10.10.4 Yosemite, Build 14E46
2. Create (if necessary) the directory `OS X Images` in our home (`~`) directory
3. Create the final image `OS X 10.10.4 Yosemite (14E46).iso` in the `OS X Images` directory

If we want, we can instead provide our own file name:

```
$ osximg "/Applications/Install OS X Yosemite.app" "~/OS X Images/Yosemite.iso"
```

We can also tell `osximg` to use an `InstallESD.dmg` instead of an app bundle:

```
$ osximg InstallESD.dmg .
```

This is mostly useful if we've previously copied `Install*.app/Contents/SharedSupport/InstallESD.dmg` to another location and discarded the installer app.

*It's good practice to keep a backup of the original installer app, e.g. compress/zip it and store it somewhere safe, perhaps with our newly created image alongside it.*

Full usage:

```
$ osximg -h
```
