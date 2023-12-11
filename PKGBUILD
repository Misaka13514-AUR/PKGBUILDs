# Maintainer:  Misaka13514 <Misaka13514 at gmail dot com>
# Contributor: taotieren <admin@taotieren.com>

pkgname=easyeda-pro-bin
_pkgname=${pkgname%-bin}
pkgver=2.1.42
pkgrel=1
pkgdesc="EasyEDA Professional Edition"
arch=('x86_64' 'aarch64')
url="https://pro.easyeda.com/"
license=('custom')
depends=('gtk3' 'nss' 'alsa-lib')
makedepends=()
provides=($_pkgname)
conflicts=($_pkgname $_pkgname-git $_pkgname-electron)
install=$pkgname.install
source=("LICENSE"
        "$pkgname.install")
source_x86_64=("$_pkgname-x86_64-$pkgver.zip::https://image.easyeda.com/files/easyeda-pro-linux-x64-$pkgver.zip")
source_aarch64=("$_pkgname-aarch64-$pkgver.zip::https://image.easyeda.com/files/easyeda-pro-linux-arm64-$pkgver.zip")
sha256sums=('fdf0f0fe693cb085c92f20e9cf931b9d4b0bafbb895678a6993a41e23a43fab1'
            'cc1661c75c9366d2fe43c4b864cf81acb9aae7cab505ce21e7de2db3c68cde76')
sha256sums_x86_64=('03e85bc4517f055a329e374a3f1dc2886504a46bd31c7e85683ead6995f75316')
sha256sums_aarch64=('d0da5c8956f7ff09611b680442ba2691e4196101543da19b3efce40e759d3a23')

package() {
    cd $srcdir
    install -Dm644 LICENSE $pkgdir/usr/share/licenses/$pkgname/LICENSE

    cd $srcdir/$_pkgname
    install -Dm644 EasyEDA-Distribution-License.txt \
                   $pkgdir/usr/share/licenses/$pkgname/EasyEDA-DLA.txt
    install -dm755 $pkgdir/opt/$_pkgname
    cp -dpr --no-preserve=ownership * $pkgdir/opt/$_pkgname
    rm -rf $pkgdir/opt/$_pkgname/icon
    rm -rf $pkgdir/opt/$_pkgname/easyeda-pro.dkt
    rm -rf $pkgdir/opt/$_pkgname/EasyEDA-Distribution-License.txt

    # icon
    local _icon
    for _icon in 16 32 64 128 256 512; do
        install -Dm644 icon/icon_${_icon}x${_icon}.png \
                       $pkgdir/usr/share/icons/hicolor/${_icon}x${_icon}/apps/$_pkgname.png
    done
    install -Dm644 icon/icon_512x512@2x.png \
                   $pkgdir/usr/share/icons/hicolor/1024x1024/apps/$_pkgname.png

    # desktop entry
    install -Dm644 easyeda-pro.dkt \
                   $pkgdir/usr/share/applications/$_pkgname.desktop

    sed -i 's|/opt/easyeda-pro/icon/icon_128x128.png|easyeda-pro|g' \
        $pkgdir/usr/share/applications/$_pkgname.desktop
    sed -i 's|/opt/easyeda-pro/||g' \
        $pkgdir/usr/share/applications/$_pkgname.desktop

    # soft link
    install -dm755 $pkgdir/usr/bin
    ln -s /opt/$_pkgname/$_pkgname $pkgdir/usr/bin/$_pkgname
    chmod 755 $pkgdir/opt/$_pkgname/$_pkgname
}
