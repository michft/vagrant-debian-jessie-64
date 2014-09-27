# Notes

This script based on original dotzero [repo](https://github.com/dotzero/vagrant-debian-wheezy-64) which is in turn based on 
Carl's [repo](https://github.com/cal/vagrant-ubuntu-precise-64) and with some tweaks to be compatible Debian8.

## Important.

You need to change the `ISO_MD5="09a2c4d358fe8c8a34e20b030f7b5d72"` line in ./build.sh by looking up the relevant value [Here](http://cdimage.debian.org/cdimage/weekly-builds/amd64/iso-cd/MD5SUMS)

## About

This script will:

 1. download the `Debian 8.0 beta "Jessie"` server, 64bit iso
 2. ... do some magic to turn it into a vagrant box file
 3. output `debian-jessie-64.box`

## Requirements

 * Oracle VM VirtualBox
 * Vagrant
 * mkisofs
 * 7zip

## Usage on OSX

    ./build.sh

This should do everything you need. If you don't have `mkisofs` or `p7zip`, install [homebrew](http://mxcl.github.com/homebrew/), then:

    brew install cdrtools
    brew install p7zip

To add `debian-wheezy-64.box` with name `debian-wheezy` into vagrant:

    vagrant box add "debian-wheezy" debian-wheezy-64.box

## Usage on Linux

    ./build.sh

This should do everything you need. If you don't have `mkisofs` or `p7zip`:

    sudo apt-get install genisoimage
    sudo apt-get install p7zip-full

To add `debian-wheezy-64.box` with name `debian-wheezy` into vagrant:

    vagrant box add "debian-wheezy" debian-wheezy-64.box

## Usage on Windows (under cygwin/git shell)

    ./build.sh

Tested under Windows 7 with this tools:

 * [cpio](http://gnuwin32.sourceforge.net/packages/cpio.htm)
 * [md5](http://www.fourmilab.ch/md5/)
 * [7zip](http://www.7-zip.org/)
 * [mkisofs](http://sourceforge.net/projects/cdrtoolswin/)

To add `debian-wheezy-64.box` with name `debian-wheezy` into vagrant:

    vagrant box add "debian-wheezy" debian-wheezy-64.box

## Environment variables

You can affect the default behaviour of the script using environment variables:

    VAR=value ./build.sh

The following variables are supported:

* `PRESEED` — path to custom preseed file. May be useful when if you need some customizations for your private base box (user name, passwords etc.);

* `LATE_CMD` — path to custom late_command.sh. May be useful when if you need some customizations for your private base box (user name, passwords etc.);

* `VM_GUI` — if set to `yes` or `1`, disables headless mode for vm. May be useful for debugging installer;



