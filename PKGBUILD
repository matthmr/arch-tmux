# Maintainer: Sergej Pupykin <pupykin.s+arch@gmail.com>
# Maintainer:  TDY <tdy@gmx.com>
# Contributor: Grigorios Bouzakis <grbzks[at]gmail[dot]com>

pkgname=tmux
pkgver=2.0
pkgrel=4
pkgdesc='A terminal multiplexer'
url='http://tmux.github.io/'
arch=('i686' 'x86_64')
license=('BSD')
depends=('ncurses' 'libevent' 'libutempter')
source=(https://github.com/tmux/tmux/releases/download/$pkgver/tmux-$pkgver.tar.gz
	ncurses6-xterm-standout.patch
	LICENSE)
md5sums=('9fb6b443392c3978da5d599f1e814eaa'
         '70347df93ed1922d6718d91491a7d9b4'
         '71601bc37fa44e4395580b321963018e')

prepare() {
	cd "$srcdir/$pkgname-${pkgver/_/}"
	patch -Np1 -i ../ncurses6-xterm-standout.patch
}

build() {
	cd "$srcdir/$pkgname-${pkgver/_/}"
	./configure --prefix=/usr
	make
}

package() {
	cd "$srcdir/$pkgname-${pkgver/_/}"
	make install DESTDIR=$pkgdir
	install -Dm644 ../LICENSE "$pkgdir/usr/share/licenses/tmux/LICENSE"

	install -dm755 "$pkgdir/usr/share/tmux/"
	install -m644 examples/* "$pkgdir/usr/share/tmux/"
	install -Dm644 examples/tmux.vim "$pkgdir/usr/share/vim/vimfiles/syntax/tmux.vim"

	install -d $pkgdir/usr/share/bash-completion/completions/
	mv $pkgdir/usr/share/tmux/bash_completion_tmux.sh $pkgdir/usr/share/bash-completion/completions/tmux
}
