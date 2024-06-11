# Maintainer: Hao Long <aur@esd.cc>
# Co-Maintainer: Misaka13514 <Misaka13514 at gmail dot com>

pkgname=subfinder-bin
_pkgname=${pkgname%-bin}
pkgver=2.6.6
pkgrel=2
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
b2sums_i686=('39274a6171979ca1e957f1abd02b9ca691ca371e004ffe2b96b729e0400f4a8eb175a59c23c9ea12a9148586a99ce90b4ceccbf8f2198520038dd7f091a7c0d3')
b2sums_x86_64=('2e549c77649f8ead33438110f9dd1db7edd40f0c0469a6ebdc20b8574ac0009597c8495a8b54a182a95b17dc9cce36316f3372588cf72e735612071c0ab408fe')
b2sums_armv7h=('c3e98b753cdf1e09bc2199de606828542a06a3615ab7b337c8145f2106f24fce15ddf18b6706c05652e412886899949ab5e08ccdbc8041749b12af4354a3312f')
b2sums_aarch64=('bff3412c19ad5c6651eaf3688e53e804f9e95ab7f2381e8abc69b5d382b9b3e3d20cf81ab5134edac53012b26e1ce019a00625f78b77dcd2d7b62a8403c70188')

package() {
  install -Dm644 LICENSE.md "$pkgdir"/usr/share/licenses/$pkgname/LICENSE.md
  install -Dm755 subfinder ${pkgdir}/usr/bin/subfinder
}

# vim: ts=2 sw=2 et:
