# Maintainer:  Misaka13514 <Misaka13514 at gmail dot com>
# Contributor: taotieren <admin@taotieren.com>

pkgname=easyeda-pro-bin
_pkgname=${pkgname%-bin}
pkgver=1.7.27
pkgrel=1
pkgdesc="EasyEDA Professional Edition"
arch=('x86_64')
url="https://pro.easyeda.com/"
license=('custom')
depends=('gtk3' 'nss' 'alsa-lib')
makedepends=('libarchive')
optdepends=()
provides=(${_pkgname})
conflicts=(${_pkgname} ${_pkgname}-git)
backup=()
options=()
install=${pkgname}.install
source=("${_pkgname}-${pkgver}.zip::https://image.easyeda.com/files/easyeda-pro-linux-x64-${pkgver}.zip"
		"LICENSE"
		"${pkgname}.install")
noextract=()
sha256sums=('b355b108b87d381abe8d43c7aca3145be961640972fb8ec62d0a9cd0bc644dea'
			'c25d162b032c680a34856d65062aa7ffab56a478ee972eeb3e78543d2eb40f74'
			'cc1661c75c9366d2fe43c4b864cf81acb9aae7cab505ce21e7de2db3c68cde76')

package() {
	install -dm755 ${pkgdir}/opt/${_pkgname}
	#unzip "${srcdir}/${_pkgname}-linux-x64.zip" -d ${pkgdir}/opt/${_pkgname}
	bsdtar xf "${srcdir}/${_pkgname}-linux-x64.zip" -C "${pkgdir}/opt/${_pkgname}"

	# icon
	local _icon
	for _icon in 16 32 64 128 256; do
		install -Dm644	${pkgdir}/opt/${_pkgname}/icon/icon_${_icon}x${_icon}.png \
						${pkgdir}/usr/share/icons/hicolor/${_icon}x${_icon}/apps/${_pkgname}.png
	done
	rm -rf ${pkgdir}/opt/${_pkgname}/icon

	# desktop entry
	install -Dm644	${pkgdir}/opt/${_pkgname}/EasyEDA-PRO.dkt \
					${pkgdir}/usr/share/applications/${_pkgname}.desktop

	sed -i 's|/easyeda-pro-linux-x64/icon/icon_128x128.png|easyeda-pro|g' \
		${pkgdir}/usr/share/applications/${_pkgname}.desktop
	sed -i 's|/easyeda-pro-linux-x64/||g' \
		${pkgdir}/usr/share/applications/${_pkgname}.desktop
	rm -rf ${pkgdir}/opt/${_pkgname}/EasyEDA-PRO.dkt

	# soft link
	install -dm755 ${pkgdir}/usr/bin
	ln -s /opt/${_pkgname}/${_pkgname} ${pkgdir}/usr/bin/${_pkgname}
	chmod 755 ${pkgdir}/opt/${_pkgname}/${_pkgname}

	# LICENSE
	install -Dm644 LICENSE ${pkgdir}/usr/share/licenses/${pkgname}/LICENSE
}
