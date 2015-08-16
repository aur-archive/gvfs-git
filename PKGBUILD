# Maintainer: Limao Luo <luolimao+AUR@gmail.com>

pkgname=gvfs-git
pkgver=1.17.3.1.gce0ffe2
pkgrel=1
pkgdesc="Virtual filesystem implementation for gio"
arch=(i686 x86_64)
url=http://git.gnome.org/browse/${pkgname%-*}/tree/README
license=(GPL2)
depends=(fuse glib2-git gtk3 libarchive libbluray libcdio-paranoia libgphoto2
    libimobiledevice libmtp libsoup-gnome obex-data-server smbclient udisks2)
makedepends=(git gtk-doc intltool)
provides=(${pkgname%-*}=$pkgver ${pkgname%-*}-{afc,afp,gphoto2,obexftp,smb})
conflicts=(${pkgname%-*} ${pkgname%-*}-{afc,afp,gphoto2,obexftp,smb})
options=(!libtool)
install=$pkgname.install
source=($pkgname::git://git.gnome.org/${pkgname%-*})
sha256sums=('SKIP')
sha512sums=('SKIP')

pkgver() {
    cd $pkgname/
    git describe | sed 's/-/./g'
}

build() {
    cd $pkgname/
    ./autogen.sh \
        --prefix=/usr \
        --sysconfdir=/etc \
        --localstatedir=/var \
        --disable-static \
        --libexecdir=/usr/lib/gvfs \
        --with-bash-completion-dir=/usr/share/bash-completion/completions
    make
}

package() {
    make -C $pkgname DESTDIR="$pkgdir" install
}
