# Contributor: tunght13488 <tunght13488 PLUS archlinux AT gmail DOT com>
pkgname=kibana4
_pkgname=kibana
pkgver=4.6.6
pkgrel=1
pkgdesc="browser based analytics and search dashboard for Elasticsearch. Please note; this package replaces the distributed precompiled binary 'node' (this is a fork from kibana which is on v5)"
arch=('any')
url="https://www.elastic.co/products/kibana"
license=('apache')
depends=('nodejs')
optdepends=('elasticsearch2')
backup=('etc/kibana4/kibana.yml')
options=('!strip')
source=(
	"https://download.elasticsearch.org/kibana/kibana/${_pkgname}-${pkgver}-linux-x86_64.tar.gz"
	kibana4.service)
sha256sums=('8c3c1808349ac9645836cae35c5570a53091b44b2212c0826907efae1a865d17'
            '4e72c505be26c044693227cc0849c6a3d7005815b7885fec3b63c5d1421bca95')

package() {
	cd "${pkgdir}"

	install -dm755 usr/lib/kibana4
	install -Dm644 "${srcdir}/kibana4.service" usr/lib/systemd/system/kibana4.service

	cd "${srcdir}/${_pkgname}-${pkgver}-linux-x86_64"

	install -Dm644 config/kibana.yml "${pkgdir}"/etc/kibana4/kibana.yml

	rm -R ./node/
	chmod o+w optimize/
	chown -R nobody:elasticsearch optimize/
	cp -Rp * "${pkgdir}"/usr/lib/kibana4/
}
