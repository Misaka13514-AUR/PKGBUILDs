_pkgname=frida
pkgname=python-$_pkgname
pkgver=12.8.11
pkgrel=1
pkgdesc="Inject JavaScript to explore native apps on Windows, Mac, Linux, iOS and Android. Python 3 version from PyPi"
arch=('i686' 'x86_64') # setup.py downloads pre-built binary components, so it doesn't work on ARM (yet).
url="https://www.frida.re"
license=('custom:wxWindows Library License, Version 3.1')
depends=('python' 'python-pygments>=2.0.2' 'python-colorama>=0.2.7')
source=("https://files.pythonhosted.org/packages/source/f/${_pkgname}/${_pkgname}-${pkgver}.tar.gz"
        "COPYING")
sha256sums=('f56bd10457767f4d7c42d76d93c53bbd5e9b0409f0efd52542f61b7c1a222fb0'
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
