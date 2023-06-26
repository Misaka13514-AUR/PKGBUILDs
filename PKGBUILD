# Maintainer:  m0ar < edvard [at] hubinette dot me>

pkgname=cloudflare-wrangler2
pkgver=3.1.1
pkgrel=1
pkgdesc='Command-line tool for working with Cloudflare Workers'
arch=('x86_64')
url="https://www.npmjs.com/package/wrangler"
license=('Apache' 'MIT')
makedepends=('npm')
depends=('nodejs')
source=("$pkgname-$pkgver.tar.gz::https://registry.npmjs.org/wrangler/-/wrangler-$pkgver.tgz")
noextract=("$pkgname-$pkgver.tar.gz")
md5sums=('b8237bfaaeac76c727a1bbc3aa6eca15')

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

