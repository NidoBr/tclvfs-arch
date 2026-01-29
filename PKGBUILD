# Maintainer: NidoBr <nidobrcontato@gmail.com>

pkgname=tclvfs
pkgver=1.4.2
pkgrel=1
pkgdesc="Virtual filesystem extension for Tcl"
arch=('x86_64')
url="https://core.tcl-lang.org/tclvfs/"
license=('BSD-3-Clause')

source=("https://core.tcl-lang.org/tclvfs/tarball/tclvfs-20230905112324-f082c47f9b.tar.gz")
sha256sums=('0b0ec1020e16a32ce54ec46de25c8a5bed3a0179037db13b8eaca735c36e8157')

depends=('bash' 'tcl')
makedepends=('make')

_srcdir="tclvfs-20230905112324-f082c47f9b"

build() {
	cd "$srcdir/$_srcdir"
	./configure --prefix=/usr
	make
}

package() {
	cd "$srcdir/$_srcdir"

	# Diretório alvo do Tcl
	local tcldir="$pkgdir/usr/lib/tcl8.6/vfs$pkgver"

	install -d "$tcldir"

	# Biblioteca compartilhada
	install -m755 libvfs${pkgver}.so "$tcldir/"

	# Scripts Tcl
	install -m644 library/*.tcl "$tcldir/"

	# pkgIndex.tcl gerado
	install -m644 pkgIndex.tcl "$tcldir/"
}
