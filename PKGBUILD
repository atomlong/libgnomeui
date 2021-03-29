# $Id$
# Maintainer: PhotonX <photon89@googlemail.com>
# Contributor: Jan de Groot <jgc@archlinux.org>

pkgname=libgnomeui
pkgver=2.24.5
pkgrel=3
pkgdesc="User Interface library for GNOME"
arch=('i686' 'x86_64' 'arm' 'armv6h' 'armv7h' 'aarch64')
license=('LGPL')
depends=('libbonoboui' 'libgnome-keyring' 'libsm')
makedepends=('intltool' 'pkg-config' 'python')
url="http://www.gnome.org"
source=(https://download.gnome.org/sources/$pkgname/2.24/$pkgname-$pkgver.tar.bz2
		config.guess
        config.sub
		03_glib-2.54-ftbfs.patch)
sha256sums=('ae352f2495889e65524c979932c909f4629a58e64290fb0c95333373225d3c0f'
			'7d1e3c79b86de601c3a0457855ab854dffd15163f53c91edac54a7be2e9c931b'
			'0c6489c65150773a2a94eebaa794b079e74a403b50b48d5adb69fc6cd14f4810'
			'a298358c38db97c569efedd7b446fdaaffa3f087cd1a049087043eeca53c7391')

prepare() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  cp -vf ${srcdir}/config.guess	${srcdir}/${pkgname}-${pkgver}/
  cp -vf ${srcdir}/config.sub	${srcdir}/${pkgname}-${pkgver}/
}

build() {
  cd "$srcdir/$pkgname-$pkgver"
  patch "libgnomeui/gnome-scores.h" < "$srcdir/03_glib-2.54-ftbfs.patch"
  ./configure --prefix=/usr --sysconfdir=/etc \
      --localstatedir=/var --disable-static \
      --libexecdir=/usr/lib/libgnomeui
  make
}

package() {
  cd "$srcdir/$pkgname-$pkgver"
  make DESTDIR="$pkgdir" install
}
