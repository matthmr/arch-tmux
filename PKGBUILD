# Maintainer: Sergej Pupykin <pupykin.s+arch@gmail.com>
# Maintainer:  TDY <tdy@gmx.com>
# Contributor: Grigorios Bouzakis <grbzks[at]gmail[dot]com>

pkgname=tmux
pkgver=1.7
pkgrel=1
pkgdesc='A terminal multiplexer'
url='http://tmux.sourceforge.net/'
arch=('i686' 'x86_64')
license=('BSD')
depends=('ncurses' 'libevent')
source=(http://downloads.sourceforge.net/tmux/tmux-$pkgver.tar.gz
		LICENSE)
md5sums=('2c48fb9beb22eedba7a5de3b78dd0c03'
         '71601bc37fa44e4395580b321963018e')

build() {
	cd "$srcdir/$pkgname-$pkgver"
	./configure --prefix=/usr
	make
}

package() {
	cd "$srcdir/$pkgname-$pkgver"
	make install DESTDIR=$pkgdir
	install -Dm644 ../LICENSE "$pkgdir/usr/share/licenses/tmux/LICENSE"

	install -dm755 "$pkgdir/usr/share/tmux/"
	install -m644 examples/* "$pkgdir/usr/share/tmux/"
	install -Dm644 examples/tmux.vim "$pkgdir/usr/share/vim/vimfiles/syntax/tmux.vim"

	install -d $pkgdir/usr/share/bash-completion/completions/
	mv $pkgdir/usr/share/tmux/bash_completion_tmux.sh $pkgdir/usr/share/bash-completion/completions/tmux
}
