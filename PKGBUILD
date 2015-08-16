pkgname=meshmixer
pkgver=2.7
pkgrel=3
pkgdesc="Autodesk meshmixer is a free tool for making crazy-ass 3D stuff without too much hassle. Or boring stuff too. \"We cannot stress enough that this is an experiment.\""
arch=('x86_64')
url="http://meshmixer.com/linux.html"
license=('proprietary')
depends=("qt4" "superlu" "minizip" "xerces-c" "cgal" "lapack" "blas" "graphite" "gmp")
makedepends=('pacman>=4.2.0') # "patchelf")
options=('!emptydirs' '!strip')
install=$pkgname.install
source=("https://s3.amazonaws.com/autodesk-meshmixer/meshmixer/amd64/meshmixer_${pkgver}-1_amd64.deb"
        "https://meshmixer.s3.amazonaws.com/meshmixer.zip"
        "meshmixer.sh"
        "meshmixer.png"
        "meshmixer.desktop")

package() {
  msg2 "Extracting the data.tar.xz..."
  bsdtar -xf data.tar.xz -C "$pkgdir/"

  msg2 "Moving stuff in place..."
  install -d "$pkgdir/usr/share/meshmixer"
  cp -ra "$srcdir"/meshmixer "$pkgdir/usr/share/meshmixer/userfiles"

  #hacks. TODO: Replace with real versions of libraries
  install -d "$pkgdir"/usr/share/meshmixer/lib/
  ln -s /usr/lib/libboost_date_time.so "$pkgdir/usr/share/meshmixer/"lib/libboost_date_time.so.1.54.0
  ln -s /usr/lib/libboost_filesystem.so "$pkgdir/usr/share/meshmixer/"lib/libboost_filesystem.so.1.54.0
  ln -s /usr/lib/libboost_system.so "$pkgdir/usr/share/meshmixer/"lib/libboost_system.so.1.54.0
  ln -s /usr/lib/libboost_thread.so "$pkgdir/usr/share/meshmixer/"lib/libboost_thread.so.1.54.0
  ln -s /usr/lib/libminizip.so "$pkgdir/usr/share/meshmixer/"lib/libminizip.so.0
  ln -s /usr/lib/libsuperlu.so "$pkgdir/usr/share/meshmixer/"lib/libsuperlu.so.3
  ln -s /usr/lib/libCGAL.so.11 "$pkgdir/usr/share/meshmixer/"lib/libCGAL.so.10

#  patchelf --set-rpath /usr/share/meshmixer/lib "$pkgdir"/usr/bin/meshmixer
mv "$pkgdir/usr/bin/meshmixer"  "$pkgdir/usr/share/meshmixer"
install meshmixer.sh "$pkgdir/usr/bin/meshmixer"

install -d "$pkgdir/usr/share/icons" 
install "meshmixer.png" "$pkgdir/usr/share/icons"

install -d "$pkgdir/usr/share/applications"
install "meshmixer.desktop" "$pkgdir/usr/share/applications"


}

md5sums=('7c241697b8b30a5698bd60fdcb5ebcb3'
         '1698ed7024219d80915f9fcdad7a84e8'
         '4c195efe6536fa62abace4d5f32716f9'
         'f492a91c8364cb86788b271f654217eb'
         'f8b6276880a37f8fefbe8f058298e0a8')
