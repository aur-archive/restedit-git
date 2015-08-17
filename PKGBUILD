# Contributor: Herv� <herve@oursours.net>

pkgname=restedit-git
pkgver=20121206
pkgrel=1
pkgdesc="RESTful External Editor client helper application"
arch=('any')
license=('ZPL')
url="http://www.hforge.org/restedit" # https://github.com/hforge/restedit
depends=('python2' 'tk')
provides=('restedit')
conflicts=('restedit')

_gitroot="git://github.com/hforge/restedit"
_gitname="restedit"

package() {
  cd "$srcdir"
  msg "Connecting to GIT server...."

  if [ -d $_gitname ] ; then
    cd $_gitname && git pull origin
    msg "The local files are updated."
  else
    git clone $_gitroot
  fi

  msg "GIT checkout done or server timeout"
  msg "Starting make..."

  rm -rf "$srcdir/$_gitname-build"
  git clone "$srcdir/$_gitname" "$srcdir/$_gitname-build"
  cd "$srcdir/$_gitname-build"

  filename=restedit.py
  destination="$pkgdir/usr/bin/$filename"
  install -D -m 0755 "$filename" "$destination"
  sed -i 's/#!\/usr\/bin\/env python/#!\/usr\/bin\/env python2/g' "$destination"
}
