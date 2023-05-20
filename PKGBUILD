# Maintainer: pwnwriter <hey@pwnwriter.xyz>

pkgname=metis-dwm
pkgver=2.0
pkgrel=0
pkgdesc="DWM for metis-os"
url="https://github.com/metis-os/metis-dwm"
arch=('any')
license=('GPL3')
options=(zipman)
depends=('libx11' 'libxinerama' 'libxft' 'freetype2')
conflicts=('dwm')
provides=("${pkgname}")
options=(!strip !emptydirs)
install="${pkgname}.install"

prepare() {
  cp -af ../source/. ${srcdir}
}

build() {
  cd "$srcdir/dmenu"
  make
  cd "$srcdir/dwm"
  make
  cd "$srcdir/slstatus"
  make
  cd "$srcdir/st"
  make
}

package() {
  cd "$srcdir/dmenu"
  make PREFIX=/usr DESTDIR="$pkgdir" install
  cd "$srcdir/dwm"
  make PREFIX=/usr DESTDIR="$pkgdir" install
  cd "$srcdir/slstatus"
  make PREFIX=/usr DESTDIR="$pkgdir" install
  cd "$srcdir/st"
  make PREFIX=/usr DESTDIR="$pkgdir" install

  cd "$srcdir/dwm"  # Assuming metis-dwm is the main project directory
  make PREFIX=/usr DESTDIR="$pkgdir" install
  install -m644 -D "$srcdir/dwm/scripts/dwm.desktop" "$pkgdir/usr/share/xsessions/dwm.desktop"
  install -m755 -D "$srcdir/dwm/scripts/metis-dwm-script" "$pkgdir/usr/local/bin/metis-dwm-script"
}

