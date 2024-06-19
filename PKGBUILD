# Maintainer: Evgeniy Alekseev <arcanis at archlinux dot org>
# Contributor: Bartłomiej Piotrowski <bpiotrowski at archlinux dot org>
# Contributor: Felipe Hommen <felibank at gmail dot com>
# Contributor: moostik <mooostik at gmail dot com>

pkgname=geogebra
pkgver=6.0.804.0
pkgrel=1
pkgdesc='Dynamic mathematics software with interactive graphics, algebra and spreadsheet'
arch=(x86_64)
url='https://www.geogebra.org/'
license=(GPL3 'CCPL:by-sa' 'CCPL:by-nc')
depends=(electron)
source=(https://download.geogebra.org/installers/6.0/GeoGebra-Linux64-Portable-${pkgver//./-}.zip
        https://static.geogebra.org/images/geogebra-logo.svg
        geogebra
        geogebra.desktop
        geogebra-mime.xml)
sha256sums=('114e537fad9322e1ae8ebdf8aa734e473b3c66a9f1d98c5a1ec5fa55d6ea9bd7'
            '55ded6b5ec9ad382494f858d8ab5def0ed6c7d529481cd212863b2edde3b5e07'
            '62d6d48511ec9a3d08440d0bba7e6da35e61f84348729872941f66f2f8f15e57'
            'e8f3ac2c91daf1bb38ef4dddf705d341c3d8028aa4afb9b74a2d1a78a9953b98'
            '100dd83e61057b9a104630ea39a84d967475d459ab38e29783a7587b3acfb6a4')

package() {
  cd GeoGebra-linux-x64

  install -Dm755 "$srcdir"/geogebra "$pkgdir"/usr/bin/geogebra
  install -dm755 "$pkgdir"/usr/lib/geogebra
  cp -dpr --no-preserve=ownership resources "$pkgdir"/usr/lib/geogebra
  cp -dpr --no-preserve=ownership locales "$pkgdir"/usr/lib/geogebra

  install -Dm644 "$srcdir"/geogebra.desktop -t "$pkgdir"/usr/share/applications/
  install -Dm644 "$srcdir"/geogebra-logo.svg "$pkgdir"/usr/share/icons/hicolor/scalable/apps/geogebra.svg
  install -Dm644 "$srcdir"/geogebra-mime.xml "$pkgdir"/usr/share/mime/packages/geogebra.xml
}
