# Maintainer : bartus <arch-user-repoᘓbartus.33mail.com>
pkgname=blender-plugin-animation-nodes
name=animation_nodes
pkgver=2.0
pkgrel=5
pkgdesc="Node based visual scripting system designed for motion graphics in Blender. (blender 2.7 version)"
arch=(i686 x86_64)
url="https://github.com/JacquesLucke/animation_nodes"
license=('GPL')
depends=(python-numpy)
makedepends=(cython)
source=("https://github.com/JacquesLucke/animation_nodes/archive/v2.0.tar.gz"
        "fix-colision-with-git-package.patch"
        )
md5sums=('a5e8d144323c4302b2dab8dca1b61b7d'
         '804b017e42a6ec149f4a63d9b0b82030')

prepare() {
  cd ${srcdir}/${name}-${pkgver}
# patch -Np1 -i ${srcdir}/fix-colision-with-git-package.patch
}

build() {
  cd ${srcdir}/${name}-${pkgver}
  python setup.py --nocopy --noversioncheck
}

package() {
# _blender=$(pacman -Sddp --print-format %v blender-2.7|grep -oP '(?<=\:)[[:digit:]]{1}\.[[:digit:]]{2}(?=)')
  depends+=(blender-2.7)
  _blender="2.79"
  cd ${srcdir}
  addons="$pkgdir/usr/share/blender/${_blender}/scripts/addons"
  install -dm755 ${addons}/${name}
  cp -a -t ${addons}/${name} ${name}-${pkgver}/${name}/*
}

# vim:set sw=2 ts=2 et:
