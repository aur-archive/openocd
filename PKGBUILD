# Contributor: Matthias Bauch <matthias.bauch@gmail.com>
# Contributor: Laszlo Papp <djszapi2 at gmail com>
# Maintainer: Samuel Tardieu <sam@rfc1149.net>

pkgname=openocd
pkgver=0.5.0
pkgrel=2
pkgdesc="Debugging, in-system programming and boundary-scan testing for embedded target devices"
arch=('i686' 'x86_64')
url="http://openocd.berlios.de"
license=('GPL')
depends=('libftdi')
options=(!strip !libtool)
install=openocd.install
source=("http://downloads.sourceforge.net/sourceforge/$pkgname/$pkgname-$pkgver.tar.bz2")
md5sums=('43434c2b5353c9b853278b8bff22cb1a')

# what features should be enabled on build
# 'ecos','zy1000' seams not to be supported on linux

_features=(parport ft2232_libftdi amtjtagaccel ep93xx at91rm9200 gw16012 presto_libftdi usbprog oocd_trace jlink vsllink rlink arm-jtag-ew buspirate)

build() {
	cd ${srcdir}/${pkgname}-${pkgver}${_rc}
	./configure --prefix=/usr ${_features[@]/#/--enable-} --disable-werror
	make || return 1
	make DESTDIR=${pkgdir}/ install || return 1
}
