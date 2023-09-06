# Maintainer:  Misaka13514 <Misaka13514 at gmail dot com>
# Contributor: taotieren <admin@taotieren.com>

pkgname=easyeda-pro-bin
_pkgname=${pkgname%-bin}
pkgver=2.0.32
pkgrel=2
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
sha256sums=('37f229a8fa5de9f1e1af1ad2046295a4837bfe3b0e1272cbb9d9f6c5747d2f10'
            'cc1661c75c9366d2fe43c4b864cf81acb9aae7cab505ce21e7de2db3c68cde76')
sha256sums_x86_64=('7df45c6b5d8a67430eb73797da0b9268fe1e4cdc545f41763123ac75d088231e')
sha256sums_aarch64=('1692f916386759ac3d3b90171d0360b2476aceabe4125286326e143958808346')

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
