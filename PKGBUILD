# Maintainer: Christian Hesse <mail@eworm.de>
# Maintainer: T.J. Townsend <blakkheim@archlinux.org>

pkgname=tmux
pkgver=3.5
pkgrel=1
pkgdesc='Terminal multiplexer'
url='https://github.com/tmux/tmux/wiki'
arch=('x86_64')
license=('BSD')
depends=('libevent' 'libevent_core-2.1.so'
         'libutempter'
         'ncurses' 'libncursesw.so')
makedepends=('git')
source=("git+https://github.com/tmux/tmux.git#tag=${pkgver}")
sha256sums=('b838881279beaf795bf4926212c2d3fe0d31188c83e8d9efd68dc6772c559916'
           'SKIP')

prepare() {
	cd "$pkgname"
	patch -Np1 -i ../../mh-fixes.patch

	# https://github.com/tmux/tmux/issues/3864
	git revert -n 43e5e80343185e69a1b864fc48095ede0b898180
        # https://github.com/tmux/tmux/issues/3983
        git cherry-pick -n aa17f0e0c1c8b3f1d6fc8617613c74f07de66fae
        # https://github.com/tmux/tmux/issues/3905
        git cherry-pick -n 3823fa2c577d440649a84af660e4d3b0c095d248
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
