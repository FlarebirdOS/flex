pkgname=flex
pkgver=2.6.4
pkgrel=1
pkgdesc="A tool for generating text-scanning programs"
arch=('x86_64')
url="https://github.com/westes/flex"
license=('BSD-2-Clause')
groups=('base-devel')
depends=('glibc' 'm4')
source=(https://github.com/westes/flex/releases/download/v${pkgver}/${pkgname}-${pkgver}.tar.gz)
sha256sums=(e87aae032bf07c26f85ac0ed3250998c37621d95f8bd748b31f15b33c45ee995)

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
