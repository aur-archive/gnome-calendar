# $Id$
# Maintainer: Balló György <ballogyor+arch at gmail dot com>

pkgname=gnome-calendar
pkgver=3.15.4.1
pkgrel=2
pkgdesc="Calendar application for GNOME"
arch=('i686' 'x86_64')
url="https://wiki.gnome.org/Apps/Calendar"
license=('GPL')
depends=('evolution-data-server')
makedepends=('intltool' 'gnome-common')
install=$pkgname.install
source=(http://ftp.gnome.org/pub/GNOME/sources/$pkgname/3.15/$pkgname-$pkgver.tar.xz
        glib-2.42.patch
        gsettings.patch)
sha256sums=('4a403d4aba78a008199c5e58f499ca7722c9037d583c926c788e2a6e3b94bb47'
            '094d1d7312bbfec712c058dd48c12bd3e582747045dca544bc96cbaa48274837'
            'f76bd9efa26961ba59d7976ca9ce751500138acc873ffc6365e98508d3d00b0c')

prepare() {
  cd $pkgname-$pkgver

  # Backport to GLib 2.42
  patch -Np1 -i ../glib-2.42.patch

  # Fix GSettings installation
  patch -Np1 -i ../gsettings.patch

  autoreconf -fi
}

build() {
  cd $pkgname-$pkgver
  ./configure --prefix=/usr
  make
}

package() {
  cd $pkgname-$pkgver
  make DESTDIR="$pkgdir" install
}
