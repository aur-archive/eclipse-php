# Maintainer: Giovanne Castro <giovannefc@gmail.com>
# Based on official standard package (eclipse) maintained by Jan Alexander Steffens (heftig) <jan.steffens@gmail.com>

pkgname=eclipse-php
pkgver=4.4.1
pkgrel=2
_release=luna-SR1
pkgdesc="An IDE for PHP and other web development languages"
license=("EPL")
arch=('i686' 'x86_64')
url="http://eclipse.org"
depends=('gtk2' 'unzip' 'webkitgtk2' 'libxtst')
install=eclipse-php.install
source=("http://ftp-stud.fht-esslingen.de/pub/Mirrors/eclipse/technology/epp/downloads/release/${_release/-//}/$pkgname-$_release-linux-gtk.tar.gz"
        "http://ftp-stud.fht-esslingen.de/pub/Mirrors/eclipse/technology/epp/downloads/release/${_release/-//}/$pkgname-$_release-linux-gtk-x86_64.tar.gz"
        'eclipse-php.sh' 'eclipse-php.desktop')
md5sums=('a88f0c4e1de5f8aee6b88e12c6fbfc21'
         'a029bcb02bac476a2678a2039f515519'
         '96b5e07608f2fbb8e1f8e15e6e603f2e'
         '268cf8b4e6f8242362fbde6a877b428a')

if (( ! GENINTEG )); then
  if [[ $CARCH == x86_64 ]]; then
    source=("${source[@]:1}")
    md5sums=("${md5sums[@]:1}")
  else
    source=("${source[0]}" "${source[@]:2}")
    md5sums=("${md5sums[0]}" "${md5sums[@]:2}")
  fi
fi

package_eclipse-php() {
  install -d "$pkgdir/usr/share"
  cp -a eclipse "$pkgdir/usr/share/eclipse-php"

  install -D eclipse-php.sh "$pkgdir/usr/bin/eclipse-php"
  install -Dm644 eclipse-php.desktop "$pkgdir/usr/share/applications/eclipse-php.desktop"

  for _i in 16 32 48 256; do
    install -Dm644 eclipse/plugins/org.eclipse.platform_*/eclipse${_i}.png \
      "$pkgdir/usr/share/icons/hicolor/${_i}x${_i}/apps/eclipse-php.png"
  done
}