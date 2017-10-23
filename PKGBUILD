# Maintainer: jtmb <packaging at technologicalwizardry dot com>
pkgname=hath
pkgver=1.4.2
pkgrel=1
pkgdesc="SETI@Home meets BitTorrent, for E-Hentai.org and E-Hentai Galleries."
arch=(any)
url="https://ehwiki.org/wiki/Hentai@Home"
license=('GPL')
depends=(java-runtime)
makedepends=(java-environment)
source=("https://repo.e-hentai.org/hath/HentaiAtHome_1.4.2_src.zip"
        "hath.sh"
       	"hath.service")
install="${pkgname}.install"
sha256sums=('5711c5dac5481ba75d24751720035b85a02edbce66f1d155824bf4060455e38a'
			'737d8b70150f9e897c3f7413669562f1f92e0df6539403f1936d6463e832c841'
			'8afd6ff66bfa986c7787e39aaad5d35a5ce1e2b722edb95bc86f76965d8d9fd0')

build() {
	
	make hath
	make jar
	make all
}

package() {

	mkdir -p -- "$pkgdir/var/lib/hath/cache"
	mkdir -p -- "$pkgdir/var/lib/hath/data"
	mkdir -p -- "$pkgdir/var/lib/hath/log"
	mkdir -p -- "$pkgdir/var/lib/hath/tmp"
	install -Dm755 -- "HentaiAtHome.jar" "$pkgdir/usr/share/java/$pkgname/$pkgname.jar"
	install -Dm755 -- "$srcdir/$pkgname.sh" "$pkgdir/usr/bin/$pkgname"
	install -Dm644 -- "hath.service" "${pkgdir}/usr/lib/systemd/system/hath.service"
	install -Dm644 -- LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
