pkgname=spectrum2-git
pkgver=20130304
pkgrel=1
pkgdesc="XMPP transport/gateway"
url="http://spectrum.im/"
arch=('x86_64' 'i686')
license=('GPLv2')
depends=('swiften-git' 'protobuf' 'libpurple' 'boost-libs' 'log4cxx')
optdepends=()
makedepends=('scons' 'boost' 'libidn' 'cmake' 'qt4')
conflicts=()
replaces=()
backup=()

_gitroot="git://github.com/hanzz/libtransport.git"
_gitname="libtransport"

build() {
  cd "$srcdir"
  msg "Connecting to GIT server...."

  if [ -d $_gitname ] ; then
    cd $_gitname && git pull origin
    msg "The local files are updated."
  else
    git clone $_gitroot $_gitname
  fi

  msg "GIT checkout done or server timeout"
  msg "Starting make..."

  rm -rf "$srcdir/$_gitname-build"
  git clone "$srcdir/$_gitname" "$srcdir/$_gitname-build"
  cd "$srcdir/$_gitname-build"

  cmake . -DCMAKE_INSTALL_PREFIX=/usr

} 
 
package() {
  cd "$srcdir/$_gitname-build"
  make DESTDIR="${pkgdir}" install
}
# vim:set ts=2 sw=2 et:

