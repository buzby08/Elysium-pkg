# Maintainer: Liam Busby <busby.liam@protonmail.com>
pkgname=Elysium
pkgver=1.3.0
pkgrel=1
pkgdesc="A custom file explorer"
arch=('x86_64')
url="https://www.elysiumfiles.co.uk"
license=('custom')
depends=('python')
makedepends=('pyinstaller')
source=("git+https://github.com/buzby08/Elysium.git")
sha256sums=('SKIP')

pkgver() {
    cd "$srcdir/yourrepo"
    git describe --tags --long 2>/dev/null || \
    echo "r$(git rev-list --count HEAD).$(git rev-parse --short HEAD)"
}

build() {
	cd "$srcdir/$pkgname"
	pyinstaller --clean --no-confirm Elysium-linux.spec
}

package() {
	cd "$srcdir/$pkgname/dist/Elysium"
	install -Dm755 "Elysium" "$pkgdir/usr/bin/Elysium"
	cp -r "_internal" "$pkgdir/usr/bin/Elysium/_internal"
	install -Dm644 "LICENSE.md" "$pkgdir/usr/share.licences/$pkgname/LICENSE"
	install -Dm644 "Elysium.desktop" \
		"$pkgdir/usr/share/applications/Elysium.desktop"
	install -Dm644 "Images/ElysiumLogo.png" \
		"$pkgdir/usr/share/pixmaps/Elysium.png"
}
