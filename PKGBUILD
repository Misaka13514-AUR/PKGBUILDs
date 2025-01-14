# Maintainer: Hao Long <aur@esd.cc>
# Co-Maintainer: Misaka13514 <Misaka13514 at gmail dot com>

pkgname=subfinder-bin
_pkgname=${pkgname%-bin}
pkgver=2.6.8
pkgrel=1
pkgdesc="A subdomain discovery tool that discovers valid subdomains for websites"
arch=('i686' 'x86_64' 'armv7h' 'aarch64')
url="https://github.com/projectdiscovery/subfinder"
license=("MIT")
provides=("${_pkgname}")
conflicts=("${_pkgname}")
depends=('glibc')
source=("LICENSE.md::https://github.com/projectdiscovery/subfinder/raw/v${pkgver}/LICENSE.md")
source_i686=("${_pkgname}-${pkgver}-i686.zip::${url}/releases/download/v${pkgver}/${_pkgname}_${pkgver}_linux_386.zip")
source_x86_64=("${_pkgname}-${pkgver}-x86_64.zip::${url}/releases/download/v${pkgver}/${_pkgname}_${pkgver}_linux_amd64.zip")
source_armv7h=("${_pkgname}-${pkgver}-armv7h.zip::${url}/releases/download/v${pkgver}/${_pkgname}_${pkgver}_linux_arm.zip")
source_aarch64=("${_pkgname}-${pkgver}-aarch64.zip::${url}/releases/download/v${pkgver}/${_pkgname}_${pkgver}_linux_arm64.zip")
b2sums=('c699be7ccfc40564b59bfa217e254c9553678f343466becebad5017d81310d7b7519837a9a25df2e09e16b6e1bd5a209d7aeb039662a206dd8966b9697c02ede')
b2sums_i686=('49d8c868689c0f32590950751fd36c7cdffe57096ad47716f5af720792eb0c08b452f36abff1ae2b8935be06e92501f80bb4d807e9df6780873dbc2a85e8e977')
b2sums_x86_64=('06e13c0fccb9738286502ee972dbd0e12855c008ec260eb1bda137cf0bc118aabaa69b095ce8a7a28817469c0fa0ad35338caf72d4151367e38b641f4c9d67b4')
b2sums_armv7h=('38792dbeb5d57053f4dafff2b1966c56ab8b10c9fba619074ef78f1ff480f5a63e5460dc7e309fa69bb7a15d6f59cdba1586d4859aa592b10b9784111e14dbe3')
b2sums_aarch64=('f3e4b9832d51f65c628e7aa18891a46ccbfdf00e9ecfa632593d070a2c864d9d03cfc1f1500a54f8f216976ce2dc5e3d3cb08bbff7d7d5311b0bd74d156825bf')

package() {
  install -Dm644 LICENSE.md "$pkgdir"/usr/share/licenses/$pkgname/LICENSE.md
  install -Dm755 subfinder ${pkgdir}/usr/bin/subfinder
}

# vim: ts=2 sw=2 et:
