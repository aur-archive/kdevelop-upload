
pkgname=kdevelop-upload
_name=kdev-upload
pkgver=1.3.80
pkgrel=1
pkgdesc="It allows you to develop locally and upload to a given remote url using ftp/fish"
arch=(i686 x86_64)
url="http://nikosams.blogspot.it/2012/11/kdevelop-upload-plugin-like-quanta-had.html"
license=('GPL2')
depends=('kdelibs>=4.3' 'qt4>=4.5' 'kdevelop>=4')
makedepends=('automoc4' 'cmake')
source=("http://master.kde.org/unstable/kdevelop/kdev-upload/1.3.80/src/${_name}-${pkgver}.tar.bz2")
md5sums=('4da6ede35348439dce3d0bc686f965c5')
_buildir=$srcdir/${_name}-${pkgver}/build

build() {
cd $srcdir/${_name}-${pkgver}

if [ -d "$_buildir" ]; then
		msg 'Cleaning previous build...'
		rm -rf "$_buildir"
	fi
#run cmake manually to set the correct CMAKE_INSTALL_PREFIX
mkdir build
cd build
cmake -DQT_QMAKE_EXECUTABLE=/usr/bin/qmake-qt4 -DCMAKE_INSTALL_PREFIX=/usr ..

make || return 1

cd $srcdir/${_name}-${pkgver}/build
make DESTDIR=$pkgdir install/strip || return 1
#install -D -m644 $srcdir/kfritz/$pkgname.desktop $pkgdir/usr/share/applications/$pkgname.desktop
}
