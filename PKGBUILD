# Maintainer: Sergej Pupykin <pupykin.s+arch@gmail.com>
# Maintainer:  TDY <tdy@gmx.com>
# Contributor: Grigorios Bouzakis <grbzks[at]gmail[dot]com>

pkgname=tmux
pkgver=1.3
pkgrel=1
pkgdesc="A terminal multiplexer"
url="http://tmux.sourceforge.net/"
arch=('i686' 'x86_64')
license=('BSD')
depends=('ncurses' 'libevent')
source=(http://downloads.sourceforge.net/tmux/tmux-$pkgver.tar.gz
	LICENSE)
md5sums=('96e60cb206de2db0610b9fb6a64c2251'
         '71601bc37fa44e4395580b321963018e')

build() {
  cd "$srcdir/tmux-$pkgver"

  ./configure
  make || return 1

  install -Dm755 tmux "$pkgdir/usr/bin/tmux" && \
  install -Dm644 tmux.1 "$pkgdir/usr/share/man/man1/tmux.1" && \
  install -Dm644 examples/tmux.vim "$pkgdir/usr/share/vim/vimfiles/syntax/tmux.vim" && \
  install -Dm644 ../LICENSE "$pkgdir/usr/share/licenses/tmux/LICENSE" && \
  install -dm755 "$pkgdir/usr/share/tmux/" && \
  install -m644 examples/* "$pkgdir/usr/share/tmux/"
}
