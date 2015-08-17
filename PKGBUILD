# Contributor: Ivan Puntiy <ivan.puntiyatgmail.com>
pkgname=runescape-client-bin
pkgver=1.2.3
pkgrel=2
epoch=2
pkgdesc="Official RuneScape client"
arch=(any)
url="http://www.runescape.com"
license=('custom')
depends=('java-runtime')
makedepends=(p7zip)
source=(
    "runescape-$pkgver.msi::${url}/downloads/runescape.msi"
    runescape
    runescape.desktop
)
md5sums=('a6d1cfeafe191ea922a1d9ecf8088e9f'
         'dca808ed546f609c6149718597a29715'
         'd9f34f124c51c027a8c3c70b6a35c883')

build() {
  cd "$srcdir"
  mkdir -p "$pkgname-$pkgver"
  7z e -y -o"$pkgname-$pkgver" runescape-$pkgver.msi 'JagexAppletViewer*' 'LicenseFile*'
}

package() {
  _extra='F77C1A97_9A40_44D4_983D_751571B24CE4'

  cd "$srcdir/$pkgname-$pkgver"

  # the client
  install -Dm644 JagexAppletViewerJarFile.${_extra} \
    "$pkgdir"/usr/share/$pkgname/jagexappletviewer.jar
  install -Dm644 JagexAppletViewerPngFile \
    "$pkgdir"/usr/share/pixmaps/jagexappletviewer.png

  # invocation script
  install -Dm755 "$srcdir"/runescape "$pkgdir"/usr/bin/runescape-client

  # desktop entry
  install -Dm644 "$srcdir"/runescape.desktop \
    "$pkgdir"/usr/share/applications/runescape.desktop

  # license
  install -Dm644 LicenseFile.${_extra} \
    "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
}
