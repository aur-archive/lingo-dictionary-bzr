# Maintainer: Maxime Gauduin <alucryd@gmail.com>
# Maintainer: Guff <cassmacguff@gmail.com>
# Contributor: Nicolas Reynolds <fauno@kiwwwi.com.ar>

pkgname=lingo-dictionary-bzr
pkgver=r183
pkgrel=1
pkgdesc='The sexiest dictionary on Earth and Jupiter'
arch=('i686' 'x86_64')
url='https://launchpad.net/lingo-dictionary'
license=('GPL3')
depends=('granite-bzr' 'json-glib' 'libsoup')
makedepends=('bzr' 'cmake' 'sqlite' 'vala')
provides=("${pkgname%-*}")
conflicts=("${pkgname%-*}")
install="${pkgname}.install"
source=("${pkgname%-*}::bzr+http://bazaar.launchpad.net/~elementary-apps/lingo-dictionary/lingo/")
sha256sums=('SKIP')

pkgver() {
  cd ${pkgname%-*}

  printf "r%s" "$(bzr revno)"
}

prepare() {
  cd ${pkgname%-*}

  sed 's/gee-1.0/gee-0.8/' -i CMakeLists.txt
}

build() {
 cd ${pkgname%-*}

  if [[ -d build ]]; then
    rm -rf build
  fi
  mkdir build && cd build

  cmake .. -DCMAKE_INSTALL_PREFIX='/usr' -DGSETTINGS_COMPILE='OFF'
  make
}

package() {
 cd ${pkgname%-*}/build

  make DESTDIR="${pkgdir}" install
}

# vim: ts=2 sw=2 et:
