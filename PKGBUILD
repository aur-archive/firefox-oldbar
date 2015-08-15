# Maintainer: Alexander Fehr <pizzapunk gmail com>

pkgname=firefox-oldbar
pkgver=1.2
pkgrel=7
pkgdesc="Firefox extension that makes the location bar look like in Firefox 2"
arch=('any')
url="https://addons.mozilla.org/en-US/firefox/addon/6227"
license=('custom')
depends=('firefox')
source=(http://releases.mozilla.org/pub/mozilla.org/addons/6227/oldbar-$pkgver-fx.xpi)
md5sums=('a4d7037b8cc1aeee1d2ac60dbc224941')

package() {
  cd "$srcdir"

  emid=$(sed -n '/.*<em:id>\(.*\)<\/em:id>.*/{s//\1/p;q}' install.rdf)

  install -d "$pkgdir"/usr/lib/firefox/extensions/$emid
  cp -a * "$pkgdir"/usr/lib/firefox/extensions/$emid

  rm -f "$pkgdir"/usr/lib/firefox/extensions/$emid/*.xpi
  chmod -R -x+X "$pkgdir"/usr/lib/firefox/extensions/$emid

  # Fix maximum supported version
  sed -i 's|<em:maxVersion>3.0b4pre</em:maxVersion>|<em:maxVersion>11.*</em:maxVersion>|' \
    "$pkgdir"/usr/lib/firefox/extensions/$emid/install.rdf
}
