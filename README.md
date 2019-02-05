# ASB Hannover-Stadt encrypted mesh based on Amateur Radio Emergency Data Network AREDN(tm) Firmware

http://do1olm.de/aredn/


## Developer Only Information

This AREDN firmware is based on original AREDN (https://github.com/aredn/aredn_ar71xx) and on OpenWrt with additional packages and patches.
A Makefile automates the entire process to create firmware images.

### Build Prerequisites

Please take a look at the [OpenWrt documentation](https://openwrt.org/docs/guide-developer/build-system/install-buildsystem)
for a complete and up to date list of packages for your operating system. 

On Ubuntu/Debian:
```
apt-get install git subversion build-essential libncurses5-dev \
  zlib1g-dev gawk unzip libxml-perl flex wget gettext quilt \
  python libssl-dev shellcheck lua5.1
```

On openSUSE:
```
zypper install --type pattern devel_basis
zypper install git subversion ncurses-devel zlib-devel gawk unzip \
  perl-libxml-perl flex wget gettext-runtime quilt python \
  libopenssl-devel shellcheck lua51
```

### Building firmware images

To obtain the source and build the firmware locally use:

```bash
git clone https://github.com/iskaron/aredn_ar71xx.git
cd aredn_ar71xx
git checkout feature/3.18.9.0-mesh-encryption
vi config.mk # enter your callsign, etc.
# build default ubnt and tplink images
make  
# build and add mikrotik images to firmware dir
make SUBTARGET=mikrotik
```

Building the images may take minutes or hours depending on the machine.
For more details see [build options](https://openwrt.org/docs/guide-developer/build-system/use-buildsystem).  
Review the build options in config.mk: `-j <number of cores + 1>`. 
`V=s` will give more verbose error messages.

An internet connection is required during the build process. A good internet
connection can improve the build time.

You need approximately 10GB of space for the build.

