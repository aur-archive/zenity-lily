# Maintainer: lilydjwg <lilydjwg@gmail.com>
# Maintainer: Jan de Groot <jgc@archlinux.org>

pkgname=zenity-lily
pkgver=3.10.2
pkgrel=1
pkgdesc="Display graphical dialog boxes from shell scripts. With --default-no patch."
arch=(i686 x86_64)
license=('LGPL')
depends=('gtk3' 'libnotify')
makedepends=(intltool gtk-doc itstool docbook-xsl git gnome-common yelp-tools)
url="http://www.gnome.org"
replaces=(zenity)
provides=(zenity=$pkgver)
conflicts=(zenity)
source=(git://git.gnome.org/zenity#tag=ZENITY_3_10_0
        default-no.patch)
sha256sums=(SKIP
            '430b450538a81fe0dc83d3077504adda8801838abb88de9054637321a9a99448')

prepare() {
  cd zenity
  git cherry-pick -n 80bc8ce643979fec201c4ebd5cd6405b6310357f
}

build() {
  cd zenity
  patch -Np1 < $srcdir/default-no.patch
  ./autogen.sh --prefix=/usr --sysconfdir=/etc \
      --localstatedir=/var
  make
}

package() {
  cd zenity
  make DESTDIR="${pkgdir}" install
}
