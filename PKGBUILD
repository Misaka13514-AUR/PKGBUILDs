# Maintainer: algebro <algebro at tuta dot io>

_pkgname=frida-tools
pkgname=python-$_pkgname
pkgver=1.2.2
pkgrel=1
pkgdesc="Inject JavaScript to explore native apps on Windows, Mac, Linux, iOS and Android. Python 3 version from PyPi."
arch=('i686' 'x86_64')
url="http://www.frida.re"
license=('wxWindows Library License, Version 3.1')
depends=('python' 'python-pygments>=2.02' 'python-prompt_toolkit=1.0.15' 'python-colorama>=0.2.7' 'python-frida>=12.1.0')
source=("https://files.pythonhosted.org/packages/source/f/${_pkgname}/${_pkgname}-${pkgver}.tar.gz"
        "COPYING")
sha256sums=('d059760a06a4b01738685973502ea0655f1a49cc50305573c3264f06c1683942'
            '5ea1544b51a28bc823b03159190d4108f9fb4f4ef912389f5137c6d295e175b2')
conflicts=("python2-${_pkgname}")

build() {
  cd "$srcdir/$_pkgname-$pkgver"
  python setup.py build
}

package() {
  cd "$srcdir/$_pkgname-$pkgver"
  python setup.py install --root=$pkgdir --optimize=1 --skip-build
  cd "$srcdir"
  install -d "$pkgdir/usr/share/licenses/$pkgname"
  install -m 644 "COPYING" "$pkgdir/usr/share/licenses/$pkgname/"
}
