# Maintainer: Sergej Pupykin <pupykin.s+arch@gmail.com>
# Maintainer:  TDY <tdy@gmx.com>
# Contributor: Grigorios Bouzakis <grbzks[at]gmail[dot]com>

pkgname=tmux
pkgver=2.3
pkgrel=1
pkgdesc='A terminal multiplexer'
url='http://tmux.github.io/'
arch=('i686' 'x86_64')
license=('BSD')
depends=('ncurses' 'libevent' 'libutempter')
source=(https://github.com/tmux/tmux/releases/download/$pkgver/tmux-$pkgver.tar.gz
	LICENSE)
md5sums=('fcfd1611d705d8b31df3c26ebc93bd3e'
         '71601bc37fa44e4395580b321963018e')

build() {
	cd "$srcdir/$pkgname-${pkgver/_/}"
	./configure --prefix=/usr
	make
}

package() {
	cd "$srcdir/$pkgname-${pkgver/_/}"
	make install DESTDIR=$pkgdir
	install -Dm644 $srcdir/LICENSE "$pkgdir/usr/share/licenses/tmux/LICENSE"
}
