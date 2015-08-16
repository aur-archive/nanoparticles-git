# Maintainer: archtux <antonio dot arias99999 at gmail dot com>

pkgname=nanoparticles-git
pkgver=20130303
pkgrel=1
pkgdesc="Enter the world of particle physics!"
url="http://dragly.org/source/nanoparticles/"
arch=('i686' 'x86_64')
license=('GPL3' 'SIL')
depends=('qt4')
makedepends=('git')

_gitroot=https://github.com/dragly/nanoparticles.git
_gitname=nanoparticles

build() {
  cd $srcdir

  msg "Connecting to GIT server...."

  if [ -d $srcdir/$_gitname ] ; then
    cd $_gitname && git pull --rebase
  else
    git clone $_gitroot
  fi

  msg "GIT checkout done or server timeout"
  msg "Starting make..."

  cd $_gitname

  qmake-qt4
  make
}

package() {
  cd $srcdir/$_gitname

  # Start file
  install -Dm755 $startdir/nanoparticles $pkgdir/usr/bin/nanoparticles

  # Data
  install -Dm755 nanoparticles $pkgdir/usr/share/nanoparticles/nanoparticles
  cp -r qml/ $pkgdir/usr/share/nanoparticles

  # Desktop icon 
  install -Dm644 nanoparticles.png $pkgdir/usr/share/pixmaps/nanoparticles.png
  install -Dm644 $startdir/nanoparticles.desktop $pkgdir/usr/share/applications/nanoparticles.desktop

  # SIL license
  install -Dm644 LICENSE-font-NovaSquare.txt $pkgdir/usr/share/licenses/NovaSquare/LICENSE
}