# Maintainer:  Gustavo Alvarez <sl1pkn07@gmail.com>

_plug=flash3kyuu_deband
pkgname=vapoursynth-${_plug}-git
pkgver=1.5.1.128.gcf65834
pkgrel=1
pkgdesc="Plugin for Vapoursynth: ${_plug} (GIT version)"
arch=('i686' 'x86_64')
url="https://github.com/SAPikachu/${_plug}"
license=('GPL3')
depends=('vapoursynth')
makedepends=('git')
provides=("vapoursynth-${_plug}")
conflicts=("vapoursynth-${_plug}" "vapoursynth-plugin-${_plug}")
source=("${_plug}::git+https://github.com/SAPikachu/${_plug}.git")
md5sums=('SKIP')
_gitname="${_plug}"

pkgver() {
  cd "${_gitname}"
  echo "$(git describe --long --tags | tr - .)"
}

prepare() {
  cd "${_gitname}"
  ./waf configure --prefix=/usr --libdir=/usr/lib/vapoursynth

}

build() {
  cd "${_gitname}"
  ./waf build
}

package(){
  cd "${_gitname}"
  ./waf install --no-ldconfig --destdir="${pkgdir}"
  install -Dm644 README.md "${pkgdir}/usr/share/doc/vapoursynth/plugins/${_plug}/README"
  install -Dm644 license.txt "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}
