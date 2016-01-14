# Maintainer: momo2ro <momo2ro.const@gmail.com>

pkgname=rtl8192eu-git
_pkgname=rtl8192eu
pkgver=6964341
pkgrel=1
pkgdesc="Kernel module for Realtek RTL8192EU USB wireless devices."
arch=('any')
url="https://github.com/jpostma/rtl8192eu"
license=('GPL')
makedepends=('linux-headers' 'git')
source=("git://github.com/jpostma/$_pkgname.git")
sha256sums=('SKIP')
install=readme.install
_version=`uname -r`

prepare() {
    cd "$_pkgname"

    # for GW-300S
    # cd os_dep/linux
    # sed -i -e '320i \	{USB_DEVICE(0x2019, 0xAB33),.driver_info = RTL8192E},/* PLATEX GW-300S */' usb_intf.c
    # cd -

    # for raspberry pi
    # sed -i -e '1323s/$(ARCH)/arm/' Makefile
}

build() {
    cd "$_pkgname"
    make INSTALL_PREFIX=/usr
    gzip -9 8192eu.ko
}

package() {
    install -d "$pkgdir/usr/lib/modules/${_version}/kernel/drivers/net/wireless"
    install -m644 "$srcdir/$_pkgname/8192eu.ko.gz" \
        "$pkgdir/usr/lib/modules/${_version}/kernel/drivers/net/wireless/8192eu.ko.gz"
}
