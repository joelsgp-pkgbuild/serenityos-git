# Maintainer: jmcb <joelsgp@protonmail.com>
pkgname=serenityos-git
pkgver=1.0_dev
pkgrel=1
pkgdesc="The Serenity Operating System 🐞"
arch=('any')
url="https://serenityos.org/"
license=('BSD')
groups=()
# https://github.com/SerenityOS/serenity/blob/master/Documentation/BuildInstructions.md#arch-linux--manjaro
# todo some may need to be moved around between depends and makedepends
# by someone with more knowledge of serenity
depends=()
makedepends=('git' 'gcc11' 'cmake' 'curl' 'mpfr' 'libmpc' 'gmp'
             'e2fsprogs' 'ninja' 'qemu-desktop' 'qemu-system-x86' 'qemu-system-aarch64'
             'ccache' 'rsync' 'unzip' 'texinfo')
optdepends=('fuse2fs: building images with root support')
provides=("${pkgname%-git}")
conflicts=("${pkgname%-git}")
replaces=()
backup=()
options=()
install=
# todo desktop entry
source=('serenity::git+https://github.com/SerenityOS/serenity.git')
noextract=()
md5sums=('SKIP')

build() {
    cd "$srcdir/${pkgname%-git}"
    Meta/serenity.sh rebuild-toolchain
    Meta/serenity.sh build
}

check() {
    cd "$srcdir/${pkgname%-git}"
    Meta/serenity.sh test
}

package() {
    cd "$srcdir/${pkgname%-git}"
    # todo install location?
    Meta/serenity.sh install
}
