# Maintainer: Martin R. <mr-ger [at] hotmail [dot] com>
pkgname=calpp
pkgver=0.90
pkgrel=3
pkgdesc="Library to allow writing ATI CAL kernels in C++"
arch=('i686' 'x86_64')
url="http://sourceforge.net/projects/calpp/"
license=('GPL3')
depends=('amdstream')
makedepends=('cmake' 'boost')
source=("http://sourceforge.net/projects/calpp/files/$pkgname-$pkgver/$pkgname-$pkgver.tar.gz")
md5sums=('efc3f519492ac8d3178fe42115ce3637')

_streamdir='/opt/amdstream'

build() {

  cd "$srcdir/$pkgname-$pkgver"

  sed -i "s|\$ENV{ATISTREAMSDKROOT}/lib|${_streamdir}/lib|g" CMakeLists.txt
  sed -i "s|\$ENV{ATISTREAMSDKROOT}/include|/${_streamdir}/include/CAL|" CMakeLists.txt

  cmake -DCMAKE_INSTALL_PREFIX=/usr .
  make
}

package() {
  cd "$srcdir/$pkgname-$pkgver"
  make DESTDIR="$pkgdir/" install
}
