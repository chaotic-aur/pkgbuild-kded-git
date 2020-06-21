# Maintainer: João Figueiredo <jf dot mundox at gmail dot com>
# Contributor: Andrea Scarpino <andrea@archlinux.org>

pkgname=kded-git
pkgver=r322.2c766d8
pkgrel=1
pkgdesc='KDE Daemon'
arch=('i686' 'x86_64')
url='https://projects.kde.org/projects/frameworks/kded'
license=('LGPL')
depends=('kinit-git')
makedepends=('extra-cmake-modules-git' 'git' 'kdoctools-git')
groups=('kf5')
conflicts=(kded)
provides=(kded)
source=('git+https://github.com/KDE/kded.git')
md5sums=('SKIP')

pkgver() {
  cd kded
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

prepare() {
  mkdir -p build
}

build() {
  cd build
  cmake ../kded \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DLIB_INSTALL_DIR=lib \
    -DBUILD_TESTING=OFF
  make -j$(($(nproc) + 1))
}

package() {
  cd build
  make DESTDIR="$pkgdir" install
}
