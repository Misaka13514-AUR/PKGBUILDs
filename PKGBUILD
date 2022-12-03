# Maintainer: kriskras99 <admin at kriskras99 dot nl>
# Contributor: Ali Molaei <ali dot molaei at protonmail dot com>
# Contributor: algebro <algebro at tuta dot io>

_pkgname=frida
pkgname=python-$_pkgname
pkgver=16.0.7
pkgrel=1
pkgdesc="Inject JavaScript to explore native apps on Windows, Mac, Linux, iOS and Android. Python 3 version from PyPi"
arch=('i686' 'x86_64' 'armv7h' 'aarch64')
url="https://www.frida.re"
license=('custom:wxWindows Library License, Version 3.1')
depends=('python')
optdepends=('python-typing_extensions: for Python <3.8')
# Sourced from https://pypi.org/project/frida/#files
source=("https://files.pythonhosted.org/packages/15/c4/92c5474b2bfbe757d9dd22665bd2ebaa6d4a3da5efce4f772050e404b0f2/${_pkgname}-${pkgver}.tar.gz"
        "COPYING")
# Sourced from https://github.com/frida/frida/releases
source_i686=("frida-core-devkit-${pkgver}-linux.tar.xz::https://github.com/frida/frida/releases/download/${pkgver}/frida-core-devkit-${pkgver}-linux-x86.tar.xz")
source_x86_64=("frida-core-devkit-${pkgver}-linux.tar.xz::https://github.com/frida/frida/releases/download/${pkgver}/frida-core-devkit-${pkgver}-linux-x86_64.tar.xz")
source_armv7h=("frida-core-devkit-${pkgver}-linux.tar.xz::https://github.com/frida/frida/releases/download/${pkgver}/frida-core-devkit-${pkgver}-linux-armhf.tar.xz")
source_aarch64=("frida-core-devkit-${pkgver}-linux.tar.xz::https://github.com/frida/frida/releases/download/${pkgver}/frida-core-devkit-${pkgver}-linux-arm64.tar.xz")
sha256sums=('8e6e285fd9846aa045d6827b90b5ad2fe2e42117c4bb0e453bd825da0ad825a1'
            '5ea1544b51a28bc823b03159190d4108f9fb4f4ef912389f5137c6d295e175b2')
sha256sums_i686=('7c472eb02ecbab098c559f7ffeb2555aa9e5f6b7ab6bfd17e6a9f3df452fcb86')
sha256sums_x86_64=('a87b750b7f2abb3b09ba706a9f73da9d1735e515e6ccffa1dc778d58946c188b')
sha256sums_armv7h=('38f3a5031619b62c6100dd2e43af27584561304c51ca728c578c1609866aa4b5')
sha256sums_aarch64=('ebfca8ea7bf9b4802cbb7f622594ec6f114fa8d4603b3c39e84251d5aee87f46')
noextract=("frida-core-devkit-${pkgver}-linux.tar.xz")
conflicts=("python2-${_pkgname}")

prepare() {
  mkdir "$srcdir/frida-core-devkit-${pkgver}-linux"
  bsdtar -x --cd "$srcdir/frida-core-devkit-${pkgver}-linux" -f "frida-core-devkit-${pkgver}-linux.tar.xz"
}

build() {
  cd "$srcdir/$_pkgname-$pkgver"
  FRIDA_CORE_DEVKIT="../frida-core-devkit-${pkgver}-linux" python setup.py build
}

package() {
  cd "$srcdir/$_pkgname-$pkgver"
  FRIDA_CORE_DEVKIT="../frida-core-devkit-${pkgver}-linux" python setup.py install --root=$pkgdir --optimize=1 --skip-build

  cd "$srcdir"
  install -d "$pkgdir/usr/share/licenses/$pkgname"
  install -m 644 "COPYING" "$pkgdir/usr/share/licenses/$pkgname/"
}
