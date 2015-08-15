# Maintainer: DonVla <donvla@users.sourceforge.net>

pkgname=dcompmgr-git
pkgver=20130216
pkgrel=1
pkgdesc="Dana's composite manager (not for production use)"
arch=(i686 x86_64)
url="http://git.openbox.org/?p=dana/dcompmgr.git;a=summary"
license=('GPL')
depends=('glib2' 'libgl')
makedepends=('glproto')
source=()
noextract=()
_gitroot="git://git.openbox.org/dana/dcompmgr"
_gitname="dcompmgr"
md5sums=()
sha256sums=()

build() {
  cd "$srcdir"
  msg "Connecting to GIT server...."

  if [ -d $_gitname ] ; then
    cd $_gitname 
    make clean
    git pull origin
    msg "The local files are updated."
  else
    git clone $_gitroot
    cd "$_gitname"
  fi

  # There is no option to disable shadows
  _X_SHADOWOFFSET=0   
  _Y_SHADOWOFFSET=0   
  sed -i -e "s#d->xshadowoff = 2;#d->xshadowoff = ${_X_SHADOWOFFSET};#" -e "s#d->yshadowoff = 2;#d->yshadowoff = ${_Y_SHADOWOFFSET};#" *.c

  msg "GIT checkout done or server timeout"
  msg "Starting make..."
  make
  install -D -m 0755 dcompmgr ${pkgdir}/usr/bin/dcompmgr
}
