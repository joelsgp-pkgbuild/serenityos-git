# Maintainer: jmcb <joelsgp@protonmail.com>
pkgname=serenityos-git
pkgver=1.0_dev
pkgrel=1
pkgdesc="The Serenity Operating System 🐞 (qemu image)"
arch=('any')
url="https://serenityos.org/"
license=('BSD')
# https://github.com/SerenityOS/serenity/blob/master/Documentation/BuildInstructions.md#arch-linux--manjaro
# todo some may need to be moved around between depends and makedepends
# by someone with more knowledge of serenity
depends=()
makedepends=('git' 'gcc11'
             'cmake' 'curl' 'mpfr' 'libmpc' 'gmp' 'e2fsprogs' 'ninja'
             'qemu-desktop' 'qemu-system-x86' 'qemu-system-aarch64'
             'ccache' 'rsync' 'unzip' 'texinfo')
optdepends=('fuse2fs: building images without root support')
provides=("${pkgname%-git}")
conflicts=("${pkgname%-git}")
# todo desktop entry
source=("${pkgname%-git}::git+https://github.com/SerenityOS/serenity.git")
noextract=()
md5sums=('SKIP')

pkgver() {
    # todo
}

# the build system is weird - do bash -x Meta/serenity.sh run to see the actual process
build() {
    cd "$srcdir/${pkgname%-git}"

    Meta/serenity.sh rebuild-toolchain
    # SERENITY_SOURCE_DIR="$(pwd)"
    # TARGET=i686
    # cd "$SERENITY_SOURCE_DIR/Toolchain" && ARCH="$TARGET" ./BuildIt.sh
    # cd "$SERENITY_SOURCE_DIR"

    Meta/serenity.sh build
    # CMAKE_ARGS="-DSERENITY_TOOLCHAIN=GNU"
    # SUPER_BUILD_DIR="${SERENITY_SOURCE_DIR}/Build/superbuild-i686"
    # cmake -GNinja "${CMAKE_ARGS[@]}" -S "$SERENITY_SOURCE_DIR/Meta/CMake/Superbuild" -B "$SUPER_BUILD_DIR"
    # cmake --build "$SUPER_BUILD_DIR"
}

check() {
    cd "$srcdir/${pkgname%-git}"
    Meta/serenity.sh test
}

package() {
    cd "$srcdir/${pkgname%-git}"
    share="${pkgdir}"/usr/share
    install -Dm644 LICENSE "${share}"/licenses/${pkgname%-git}/LICENSE
    # todo install location?
    Meta/serenity.sh install
}
