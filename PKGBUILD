# Maintainer: Christian Hesse <mail@eworm.de>
# Maintainer: T.J. Townsend <blakkheim@archlinux.org>

pkgname=tmux
pkgver=3.4
pkgrel=4
pkgdesc='Terminal multiplexer'
url='https://github.com/tmux/tmux/wiki'
arch=('x86_64')
license=('BSD')
depends=('libevent' 'libevent_core-2.1.so'
         'libutempter'
         'ncurses' 'libncursesw.so'
         'systemd-libs' 'libsystemd.so')
makedepends=('systemd')
source=("https://github.com/tmux/tmux/releases/download/${pkgver/_/}/tmux-${pkgver/_/}.tar.gz"
        'mh-fixes.patch')
sha256sums=('551ab8dea0bf505c0ad6b7bb35ef567cdde0ccb84357df142c254f35a23e19aa'
            '277632395497899d31f6bd47ff3f4d47f7acbc1ad216dc99b3fb0e6b3efcfdc3')

prepare() {
	cd "$pkgname-${pkgver/_/}"

	patch -Np1 -i ../mh-fixes.patch

	autoreconf -fi
}

build() {
	cd "$pkgname-${pkgver/_/}"

	./configure \
		--prefix=/usr \
		--enable-sixel \
		--enable-systemd \
		--enable-utempter
	make
}

package() {
	cd "$pkgname-${pkgver/_/}"

	make install DESTDIR="$pkgdir"
	install -D -m0644 COPYING "$pkgdir/usr/share/licenses/tmux/LICENSE"
}
