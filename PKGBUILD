# Maintainer: taotieren <admin@taotieren.com>
# Co-Maintainer: Misaka13514 <Misaka13514 at gmail dot com>

pkgname=lceda-pro-bin
_pkgname=${pkgname%-bin}
pkgver=1.9.20
pkgrel=2
pkgdesc="免费、专业、强大的国产PCB设计工具"
arch=('x86_64' 'aarch64')
url="https://pro.lceda.cn/"
license=('custom')
provides=(${pkgname})
conflicts=(${_pkgname} ${_pkgname}-git)
#replaces=(${pkgname})
depends=('gtk3' 'nss' 'alsa-lib')
makedepends=('libarchive')
backup=()
#options=('!strip')
install=${pkgname}.install
source=("LICENSE"
        "${pkgname}.install")
source_x86_64=("${_pkgname}-${pkgver}.zip::https://image.lceda.cn/files/lceda-pro-linux-x64-${pkgver}.zip")
source_aarch64=("${_pkgname}-${pkgver}.zip::https://image.lceda.cn/files/lceda-pro-linux-arm64-${pkgver}.zip")
sha256sums=('e1c6b9641b73a56d5bffe42d8db2107af8f2c51aa5cd11c79aa998321a5e0190'
            'f8c3c7f65443801b8a70e40de7cdceade5dcd75974945695dd5a1bfb1f862e1a')
sha256sums_x86_64=('a9f0191d2aafe6a995f96c9d0f7e295f155ee107fccee677d8f804303434c54f')
sha256sums_aarch64=('b8b901ce165ef9b328caffb64af6c382cc13266707364c019d0128ca8f2bf7ac')
# noextract=(${_pkgname}-${pkgver}.zip)

package() {
    export LC_CTYPE="zh_CN.UTF-8"
    install -dm0755 "${pkgdir}/opt/${_pkgname}/"

    #bsdtar xf "${srcdir}/${_pkgname}-linux-x64.zip" --strip-components=1 -C  "${pkgdir}/opt/${_pkgname}"
    #bsdtar xf "${srcdir}/${_pkgname}-linux-x64.zip" -C  "${pkgdir}/opt/${_pkgname}"
    mv ${srcdir}/${_pkgname}-linux-x64/* ${pkgdir}/opt/${_pkgname}

    # icon
    local _icon
    for _icon in 16 32 64 128 256 512; do
        install -Dm0644 ${pkgdir}/opt/${_pkgname}/icon/icon_${_icon}x${_icon}.png \
                        ${pkgdir}/usr/share/icons/hicolor/${_icon}x${_icon}/apps/${_pkgname}.png
    done
    install -Dm644 ${pkgdir}/opt/${_pkgname}/icon/icon_512x512@2x.png \
                   ${pkgdir}/usr/share/icons/hicolor/1024x1024/apps/${_pkgname}.png
    rm -rf ${pkgdir}/opt/${_pkgname}/icon

    # desktop entry
    install -Dm0644 ${pkgdir}/opt/${_pkgname}/LCEDA-PRO.dkt \
                    ${pkgdir}/usr/share/applications/${_pkgname}.desktop

    sed -i 's|/opt/lceda-pro/icon/icon_128x128.png|lceda-pro|g' \
        ${pkgdir}/usr/share/applications/${_pkgname}.desktop
    sed -i 's|/opt/lceda-pro/||g' \
        ${pkgdir}/usr/share/applications/${_pkgname}.desktop
    rm -rf ${pkgdir}/opt/${_pkgname}/LCEDA-PRO.dkt

    # soft link
    find "${pkgdir}/opt/${_pkgname}" -type f -exec chmod 644 "{}" \;
    find "${pkgdir}/opt/${_pkgname}" -type d -exec chmod 755 "{}" \;

    install -dm0755 ${pkgdir}/usr/bin
    ln -s /opt/${_pkgname}/${_pkgname} ${pkgdir}/usr/bin/${_pkgname}
    chmod 0755 ${pkgdir}/opt/${_pkgname}/${_pkgname}

    # LICENSE
    install -Dm0644 LICENSE ${pkgdir}/usr/share/licenses/${pkgname}/LICENSE
}
