pkgname=flex
pkgver=2.6.4
pkgrel=2
pkgdesc="A tool for generating text-scanning programs"
arch=('x86_64')
url="https://github.com/westes/flex"
license=('BSD-2-Clause')
groups=('base-devel')
depends=(
    'bash'
    'glibc'
    'm4'
)
makedepends=('help2man')
source=(https://github.com/westes/flex/releases/download/v${pkgver}/${pkgname}-${pkgver}.tar.gz
    flex-pie.patch)
sha256sums=(e87aae032bf07c26f85ac0ed3250998c37621d95f8bd748b31f15b33c45ee995
    20f3cce6b0ea6ab67a902a46b89c292b959994dedcbe6ee5d187f9bba1408b0e)

prepare() {
    cd ${pkgname}-${pkgver}

    patch -p1 -i ${srcdir}/flex-pie.patch

    autoreconf -fiv
}

build() {
    cd ${pkgname}-${pkgver}

    local configure_args=(
        --disable-static
        --docdir=/usr/share/doc/${pkgname}-${pkgver}
        ${configure_options}
    )

    ./configure "${configure_args[@]}"

    make
}

package() {
    cd ${pkgname}-${pkgver}

    make DESTDIR=${pkgdir} install

    ln -sv flex   ${pkgdir}/usr/bin/lex
    ln -sv flex.1 ${pkgdir}/usr/share/man/man1/lex.1
}
