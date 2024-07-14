# Maintainer:  Misaka13514 <Misaka13514 at gmail dot com>
# Contributor: Henry-ZHR <henry-zhr@qq.com>

pkgname=serenity
_pkgver=1.0.0-beta.13
pkgver=${_pkgver//-/_}
pkgrel=1
pkgdesc='The configuration generator for sing-box'
arch=('i686' 'x86_64' 'aarch64' 'armv7h')
url='https://github.com/SagerNet/serenity'
license=('GPL-3.0-or-later')
depends=('glibc')
makedepends=('go')
optdepends=('sing-box')
backup=("etc/$pkgname/config.json")
source=("$pkgname-$pkgver.tar.gz::$url/archive/v$_pkgver.tar.gz")
sha256sums=('118268cdbc44f5970ed59b5afbd75ca5100d8061ab2e00b910af541504b739ca')

prepare() {
  cd $pkgname-$_pkgver
  mkdir -p build/
}

build() {
  cd $pkgname-$_pkgver
  export CGO_CPPFLAGS="${CPPFLAGS}"
  export CGO_CFLAGS="${CFLAGS}"
  export CGO_CXXFLAGS="${CXXFLAGS}"
  export CGO_LDFLAGS="${LDFLAGS}"
  export GOFLAGS="-buildmode=pie -trimpath -mod=readonly -modcacherw"

  go build \
    -ldflags "-X github.com/sagernet/serenity/constant.Version=${pkgver} -linkmode external -s -w" \
    -o build -v ./cmd/...
  go run ./cmd/$pkgname completion bash > build/bash-completion
  go run ./cmd/$pkgname completion fish > build/fish-completion
  go run ./cmd/$pkgname completion zsh > build/zsh-completion
}

check() {
  cd $pkgname-$_pkgver
  go test ./...
}

package() {
  cd $pkgname-$_pkgver
  install -Dm755 build/$pkgname $pkgdir/usr/bin/$pkgname
  install -Dm644 build/bash-completion "$pkgdir/usr/share/bash-completion/completions/$pkgname"
  install -Dm644 build/fish-completion "$pkgdir/usr/share/fish/vendor_completions.d/$pkgname.fish"
  install -Dm644 build/zsh-completion "$pkgdir/usr/share/zsh/site-functions/_$pkgname"
  install -Dm644 release/config/config.json "$pkgdir/etc/$pkgname/config.json"
  install -Dm644 release/config/$pkgname.service "$pkgdir/usr/lib/systemd/system/$pkgname.service"
  install -Dm644 release/config/$pkgname@.service "$pkgdir/usr/lib/systemd/system/$pkgname@.service"
}
