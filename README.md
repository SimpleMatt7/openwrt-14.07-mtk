OpenWrt build system – Installation

This is the buildsystem for the OpenWrt Linux distribution.

git clone https://github.com/Matt927/openwrt-14.07-mtk

Please use "make menuconfig" to configure your appreciated
configuration for the toolchain and firmware.

You need to have installed gcc, binutils, bzip2, flex, python, perl
make, find, grep, diff, unzip, gawk, getopt, libz-dev and libc headers.

Ubuntu 64 bit:
sudo apt update
sudo apt install build-essential subversion libncurses5-dev zlib1g-dev gawk gcc-multilib flex git-core gettext libssl-dev unzip

Run "./scripts/feeds update -a" to get all the latest package definitions
defined in feeds.conf / feeds.conf.default respectively
and "./scripts/feeds install -a" to install symlinks of all of them into
package/feeds/.

Image Configuration:
run make menuconfig and set target;
run make defconfig to set default config for build system and device;
run make menuconfig and modify set of package;
run scripts/diffconfig.sh >mydiffconfig (save your changes in the text file mydiffconfig);

Using diffconfig file:
cp diffconfig .config   # write changes to .config
make defconfig   # expand to full config


Simply running "make V=s" will build your firmware.
It will download all sources, build the cross-compile toolchain, 
the kernel and all choosen applications.

You can use "scripts/flashing/flash.sh" for remotely updating your embedded
system via tftp.

The OpenWrt system is documented in docs/. You will need a LaTeX distribution
and the tex4ht package to build the documentation. Type "make -C docs/" to build it.

To build your own firmware you need to have access to a Linux, BSD or MacOSX system
(case-sensitive filesystem required). Cygwin will not be supported because of
the lack of case sensitiveness in the file system.

Sunshine!
	Your OpenWrt Project
	http://openwrt.org

https://lede-project.org/docs/guide-developer/use-buildsystem
