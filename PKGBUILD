# Contributor: grimi <grimi at poczta dot fm>
# Contributor: <alxandre becoulet at free dot fr>

pkgname=lib32-mpfr
pkgver=3.1.2
pkgrel=1
pkgdesc="Multiple-precision floating-point library (32-bit)"
arch=('x86_64')
license=('LGPL')
url="http://www.mpfr.org/"
groups=('lib32')
depends=('mpfr' 'lib32-gmp>=4.10')
makedepends=('gcc-multilib')
options=('!libtool')
source=(http://www.mpfr.org/mpfr-current/mpfr-${pkgver}.tar.xz)

build() {
  cd "${srcdir}"/mpfr-${pkgver}
  ./configure --prefix=/usr --enable-thread-safe --enable-shared \
     --libdir='/usr/lib32' --with-gmp-include='/usr/lib32/gmp' \
     CC='gcc -m32' PKG_CONFIG_PATH='/usr/lib32/pkgconfig'
  make
}

check() {
  cd "${srcdir}"/mpfr-${pkgver}
  make check
}

package() {
  cd "${srcdir}"/mpfr-${pkgver}
  make DESTDIR="${pkgdir}" install
  rm -rf "${pkgdir}"/usr/{share,include}
}

md5sums=('e3d203d188b8fe60bb6578dd3152e05c')
