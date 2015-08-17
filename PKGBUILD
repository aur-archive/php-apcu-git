# Maintainer: Leonard de Ruijter <leonard@aur.archlinux.org>
# Contributor: Iwan Timmer <irtimmer at gmail dot com>

pkgname=php-apcu-git
pkgver=GIT
pkgrel=5
arch=('i686' 'x86_64')
pkgdesc='A free, open, and robust framework for caching'
url='http://github.com/krakjoe/apcu'
provides=('php-apc' 'php-apcu')
conflicts=('php-apc' 'php-apcu')
depends=('php')
license=('PHP')
source=($pkgname::git://github.com/krakjoe/apcu.git)
backup=('etc/php/conf.d/apcu.ini')
md5sums=('SKIP')

pkgver() {
  cd $pkgname
  git describe --always | sed 's|-|.|g' | cut -c2-
}

build() {
	cd $srcdir/$pkgname
	phpize
	./configure --prefix=/usr
	make
}

package() {
	cd $srcdir/$pkgname
	make INSTALL_ROOT=$pkgdir install
	echo ';extension=apcu.so' > apcu.ini
	install -D -m644 apcu.ini $pkgdir/etc/php/conf.d/apcu.ini
	install -D -m644 apc.php $pkgdir/usr/share/php-apcu/apc.php
	install -D -m644 INSTALL $pkgdir/usr/share/doc/php-apcu/install.txt
}
