# Maintainer: Sung Pae <self@sungpae.com>
pkgname=mutt-nerv
pkgver=
pkgrel=1
pkgdesc="Custom mutt build"
arch=('x86_64')
url="https://github.com/guns/mutt"
license=('GPL')
backup=('etc/Muttrc')
groups=('nerv')
depends=('gpgme' 'ncurses' 'openssl' 'libsasl' 'gdbm' 'libidn' 'mime-types')
makedepends=('git' 'ruby')
provides=('mutt')
conflicts=('mutt')
replaces=('mutt-guns')

pkgver() {
    printf %s "$(git describe --long --tags | tr - .)"
}

build() {
    cd "$startdir"
    PREFIX=/usr SYSCONFDIR=/etc rake configure
    make -j $(grep -c ^processor /proc/cpuinfo)
}

package() {
    cd "$startdir"
    make DESTDIR="$pkgdir/" install

    rm "${pkgdir}"/etc/mime.types{,.dist}
    rm "${pkgdir}"/usr/bin/{flea,muttbug}
    rm "${pkgdir}"/usr/share/man/man1/{flea,muttbug}.1
}
