# Maintainer: Andreas Rammhold <andreas@rammhold.de>

# things can get a little crashy at times, so better have debug symbols handy
# OPTIONS+=(debug !strip)

pkgname=irrd
pkgver=3.0.9rc2
pkgrel=1
pkgdesc="Internet Routing Registry Daemon (IRRd)"
arch=('any')
url="http://www.irrd.net"
license=('MIT style')
depends=('zlib' 'gnupg' 'openssl' 'postgresql' 'glib2' 'flex' 'autoconf' 'automake' 'byacc')
optdepends=()
provides=('irrd')
conflicts=()
source=("git+https://github.com/irrdnet/irrd.git#tag=v3.0.9rc2")
_gitname=irrd

pkgver() {
    cd "$_gitname"
    git describe --abbrev=4 --dirty --always --tags | sed 's/^v//'
}

build() {
    cd "$_gitname/src"
    ./autogen.sh
    ./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var --sbindir=/usr/bin
    make
}

package() {
    cd "$_gitname/src"
    make DESTDIR="$pkgdir" install
}

md5sums=('SKIP')

