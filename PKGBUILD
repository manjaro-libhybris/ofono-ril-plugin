#Maintainer Erik Inkinen <erik.inkinen@gmail.com>
pkgname=ofono-ril-plugin
provides=('ofono-ril-plugin')
_pkgbase=ofono-ril-plugin
pkgver=13.18a1b4a
pkgrel=2
arch=('armv7h' 'aarch64' 'x86' 'x86_64')
url="https://github.com/mer-hybris/ofono-ril-plugin"
license=('GPL2')
depends=('libmce-glib' 'libgrilio' 'ofono' 'libglibutil')
makedepends=('git' 'pkgconfig')
source=("ofono-ril-plugin::git+https://github.com/mer-hybris/ofono-ril-plugin.git")
md5sums=('SKIP')
options=(debug !strip)

pkgver() {
  cd "${srcdir}/${_pkgbase}"
  echo $(git rev-list --count HEAD).$(git rev-parse --short HEAD)
}

build() {
  cd "${srcdir}/${_pkgbase}"
  make LIBDIR=/usr/lib KEEP_SYMBOLS=1 release
}

package() {
  cd "${srcdir}/${_pkgbase}"
  make LIBDIR=/usr/lib DESTDIR="$pkgdir/" install
  rm -f "$pkgdir/etc/ofono/ril_subscription.conf"
}

