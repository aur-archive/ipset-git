pkgname=ipset-git
_pkgname=ipset
pkgver=6.24.3.gc1278ed
pkgrel=1
pkgdesc="Manage Linux IP sets"
url="http://ipset.netfilter.org/"
license=('GPL2')
depends=('glibc' 'libmnl')
makedepends=('git')
provides=('ipset')
conflicts=('ipset')
options=('!libtool')
arch=('i686' 'x86_64')
source=('git://git.netfilter.org/ipset.git')
md5sums=('SKIP')
sha256sums=('SKIP')

_gitroot="git://git.netfilter.org/ipset.git"
_gitname="ipset.git"


pkgver() {
  cd "$_pkgname"
  git describe | sed 's/^v//;s/-/./g'
}

build() {
  cd "$_pkgname"

  ./autogen.sh
  ./configure --prefix=/usr --disable-debug --disable-static --enable-shared --with-kmod=no --with-pic

  rm -r kernel # Just to make sure.

  make V=1
}

package() {
  cd "$_pkgname"
  make DESTDIR="$pkgdir" install
} 
