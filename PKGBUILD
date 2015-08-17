# Maintainer: Jacob Cook <jacob at jcook dot cc>
_name=tentd-admin
pkgname=$_name-git
pkgver=20121219
pkgrel=1
pkgdesc="A simple admin UI and server for the Tent protocol"
arch=('any')
url="https://github.com/tent/tentd-admin"
license=('MIT')
groups=()
depends=('pacman' 'ruby' 'postgresql' 'postgresql-libs' 'v8' 'nodejs' 'make' 'libxml2' 'libxslt' 'ruby-bundler' 'ruby-rake')
makedepends=('git')
provides=('tentd-admin')
conflicts=()
backup=()
options=()
install=
source=('ARCHREADME')
noextract=()
md5sums=(ae5b3e68940a37d72f827f1074b9cf42)
install=tentd-admin-git.install

_gitroot='git://github.com/tent/tentd-admin.git'
_gitname=$_name

build() {
  cd "$srcdir"
  msg "Connecting to GIT server...."

  if [[ -d "$_gitname" ]]; then
    cd "$_gitname" && git pull origin
    msg "The local files are updated."
  else
    git clone "$_gitroot" "$_gitname"
  fi

  msg "GIT checkout done or server timeout"
}

package() {
  install -d $pkgdir/var/lib/$_gitname
  install -D -m644 $srcdir/$_gitname/LICENSE.txt "${pkgdir}/usr/share/licenses/${_gitname}-git/LICENSE"
  cp $srcdir/ARCHREADME $pkgdir/var/lib/$_gitname/
  cp -a $srcdir/$_gitname $pkgdir/var/lib/
}

# vim:set ts=2 sw=2 et:
