# Maintainer: Michael Düll <mail@akurei.me> PGP-Key: 6D666EC8

pkgname=wireless_tools-beta
pkgver=30_pre9
pkgrel=12
pkgdesc="Beta Version. Fixes some iwconfig bugs."
arch=('i686' 'x86_64')
url="http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Tools.html"
license=('GPL')
depends=('glibc')
conflicts=('wireless_tools')
provides=('wireless_tools')
backup=('etc/conf.d/wireless')
source=(http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/wireless_tools.30.pre9.tar.gz wireless.conf.d)
md5sums=('ca91ba7c7eff9bfff6926b1a34a4697d'
         '027576534885b8d5dded9be546057b12')

build() {
  cd ${srcdir}/wireless_tools.30
  sed -i Makefile -e 's/^BUILD_STATIC = y/#\&/'
  make
}
package() {
  cd ${srcdir}/wireless_tools.30
  make INSTALL_DIR="${pkgdir}/usr/bin" INSTALL_LIB="${pkgdir}/usr/lib" INSTALL_INC="${pkgdir}/usr/include" INSTALL_MAN="${pkgdir}/usr/share/man" install
  install -D -m644 ${srcdir}/wireless.conf.d "${pkgdir}/etc/conf.d/wireless"
  cd ${pkgdir}/usr/lib/
  ln -s libiw.so.30 libiw.so.29
}
