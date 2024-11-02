# Maintainer: Christian Hesse <mail@eworm.de>
# Maintainer: T.J. Townsend <blakkheim@archlinux.org>

pkgname=tmux
pkgver=3.5_a
pkgrel=1
pkgdesc='Terminal multiplexer'
url='https://github.com/tmux/tmux/wiki'
arch=('x86_64')
license=('BSD')
depends=('libevent' 'libevent_core-2.1.so'
         'libutempter'
         'ncurses' 'libncursesw.so')
makedepends=('git')
source=("git+https://github.com/tmux/tmux.git#tag=${pkgver/_/}")
sha256sums=('4809a5c8289027f4bc15a06bd232f5797d7dd9ba47adf4c3135c5295aece6ff5'
            'SKIP')

prepare() {
	cd "$pkgname"
	patch -Np1 -i ../../mh-fixes.patch

	sh autogen.sh
}

build() {
	cd "$pkgname"

	./configure \
		--prefix=/usr \
		--enable-sixel \
		--enable-utempter
	make

	# --enable-systemd \
}

package() {
	cd "$pkgname"

	make install DESTDIR="$pkgdir"
	install -D -m0644 COPYING "$pkgdir/usr/share/licenses/tmux/LICENSE"
}
