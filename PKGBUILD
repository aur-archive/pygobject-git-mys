# Contributor: mariusz - myswiat <my.swiat@o2.pl>

pkgname=pygobject-git-mys
pkgver=20110705
pkgrel=1
pkgdesc="Centralized access to appointments and contacts"
arch=('i686' 'x86_64')
url="http://gnome.org/"
license=('LGPL')
depends=('git' 'glib-git' 'py3cairo')
options=('!libtool')
provides=()
conflicts=('pygobject' 'pygobject-git')
source=()
md5sums=()

_gitroot="http://git.gnome.org/browse/pygobject"
_gitname="pygobject"

build() {
  cd $srcdir
  msg "Connecting to git.gnome.org GIT server...."

  if [ -d $srcdir/$_gitname ] ; then
    cd $_gitname && git pull origin
    msg "The local files are updated."
  else
    git clone $_gitroot
  fi

  msg "GIT checkout done or server timeout"
  msg "Starting make..."

  cp -r $srcdir/$_gitname $srcdir/$_gitname-build
  cd $srcdir/$_gitname-build

  msg "Starting build"
  ./autogen.sh -prefix=/usr 
  make
  make DESTDIR=$pkgdir install

  rm -rf $srcdir/$_gitname-build
}

