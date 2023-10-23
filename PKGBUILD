# Maintainer:  m0ar < edvard [at] hubinette dot me>

pkgname=cloudflare-wrangler2
pkgver=3.14.0
pkgrel=1
pkgdesc='Command-line tool for working with Cloudflare Workers'
arch=('x86_64')
url="https://www.npmjs.com/package/wrangler"
license=('Apache' 'MIT')
makedepends=('npm')
depends=('nodejs')
source=("$pkgname-$pkgver.tar.gz::https://registry.npmjs.org/wrangler/-/wrangler-$pkgver.tgz")
noextract=("$pkgname-$pkgver.tar.gz")
md5sums=('0e6864a9bd603fd2ac833159e78a391c')

package() {
  npm install \
    -g \
    --cache "${srcdir}/npm-cache" \
    --prefix "${pkgdir}/usr" \
    "${srcdir}/${pkgname}-${pkgver}.tar.gz"

  # Do not provide 'wrangler' to prevent clash with v1
  unlink "$pkgdir/usr/bin/wrangler"

  # npm gives ownership of ALL FILES to build user
  # https://bugs.archlinux.org/task/63396
  chown -R root:root "${pkgdir}"
}

