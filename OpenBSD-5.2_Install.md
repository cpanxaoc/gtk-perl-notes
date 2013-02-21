# OpenBSD 5.2 Install Notes #

## Mirror Info ##
Mirror URL
- http://ftp5.usa.openbsd.org

Packages
- http://ftp5.usa.openbsd.org/pub/OpenBSD/5.2/packages/i386/

## Installation ##
- When the OS boots from the CD, press `I` to install
- Hit `<Enter>` to accept the default keyboard layout
- Enter in the short hostname
- Hit `<Enter>` to accept the default network card
- Hit `<Enter>` to use DHCP to get an IP address
- Hit `<Enter>` to not use IPv6
- Hit `<Enter>` to finish configuring network interfaces
- Enter in the password for the `root` account
- Confirm the `root` password
- Hit `<Enter>` to start `sshd` by default
- Type `yes` then hit `<Enter>` to start `ntpd` by default
- Hit `<Enter>` because we expect to run the X Window System
- Type `yes` then hit `<Enter>` to start `xdm` by default
- Hit `<Enter>` to not change the default console
- Type a username (`lack`?) then hit `<Enter>` to set up a user
- Hit `<Enter>` to accept the default full user name
- Type a password for your new username, then hit `<Enter>` to continue
- Confirm the password, then hit `<Enter>` to continue
- Hit `<Enter>` to disable `sshd` logins as user `root`
- Hit `<Enter>` to use the timezone listed (US/Pacific)
- Hit `<Enter>` to use the disk listed (wd0)
- Hit `<Enter>` to use DUIDs (disk unique IDs)
- Hit `<Enter>` to use the whole disk
- Hit `<Enter>` to use the partitions chosen by auto layout
- Hit `<Enter>` to use disk sets on CD (the ISO image is mounted to the
  virtual machine)
- Hit `<Enter>` to use default CD-ROM drive (cd0)
- Hit `<Enter>` to use default path to disk sets (5.2/i386)
- Hit `<Enter>` to accept the default disk sets
- Hit `<Enter>` to finish installing from disk sets
- Issue the `reboot` command to reboot the system

## Installing ports/packages ##
- Log in to the machine with the non-`root` account
- Edit the `sudoers` file so that the non-`root` user can manage the system
  - Uncomment the line `#%wheel ALL=(ALL) SETENV: ALL`
- Export `PKG_PATH` to point to an FTP mirror:
  - `export PKG_PATH=http://ftp5.usa.openbsd.org/pub/OpenBSD/5.2/packages/$(machine -a)`
- Get a list of available packages with:
  - `lynx --dump $PKG_PATH | grep "$PKG_PATH" | grep 'tgz$' \
    | sed 's!.*\/\(.*\).tgz$!\1!;'`
- Find and install the GTK/Glib/Pango/Cairo libraries
  - `sudo pkg_add -v glib2-2.32.4 gtk+2-2.24.11 cairo-1.10.2p3 pango-1.30.1`
- Some extra tools and modules
  - `sudo pkg_add -v screen-4.0.3p2 p5-YAML-0.73 p5-YAML-XS-0.38p0
    p5-libwww-5.837`
- Install modules from CPAN
  - ExtUtils::Depends
  - ExtUtils::MakeMaker
  - ExtUtils::PkgConfig
  - Test::Number::Delta
  - Cairo
  - Glib
  - Pango
  - Gtk2

## Extra OpenBSD Commands ##
- `pkg_info` - Show all of the packages installed on a system
- `pkg_info -L <package name>` - List files in a package

# vim: filetype=markdown shiftwidth=2 tabstop=2
