# Maintainer: Li Meng <lm.91@qq.com>
pkgname=Sophus-git
pkgver=v0.9.5.r73.13fb328r275.13fb328
pkgrel=1
pkgdesc="C++ implementation of Lie Groups using Eigen."
arch=(any)
url="https://github.com/strasdat/Sophus.git"
license=('GPL')
groups=()
depends=(eigen)
makedepends=('git') # 'bzr', 'git', 'mercurial' or 'subversion'
provides=("${pkgname%-git}")
conflicts=("${pkgname%-git}")
replaces=()
backup=()
options=()
install=
source=('git+https://github.com/strasdat/Sophus.git')
noextract=()
md5sums=('SKIP')


pkgver() {
	cd "$srcdir/${pkgname%-git}"

# The examples below are not absolute and need to be adapted to each repo. The
# primary goal is to generate version numbers that will increase according to
# pacman's version comparisons with later commits to the repo. The format
# VERSION='VER_NUM.rREV_NUM.HASH', or a relevant subset in case VER_NUM or HASH
# are not available, is recommended.
# Git, tags available
	printf "%s" "$(git describe --long | sed 's/\([^-]*-\)g/r\1/;s/-/./g')"

# Git, no tags available
	printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

prepare() {
	cd "$srcdir/${pkgname%-git}"
	#patch -p1 -i "$srcdir/${pkgname%-git}.patch"
}

build() {
	cd "$srcdir/${pkgname%-git}"
	if [ ! -d build ]; then
		mkdir build
	fi
	cd build
	cmake ..
	make
}

check() {
	cd "$srcdir/${pkgname%-git}"
	cd build
	make test	
}

package() {
	cd "$srcdir/${pkgname%-git}"
	cd build
	make DESTDIR="$pkgdir/" install
}
