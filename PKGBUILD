# Contributor: Andrew Gallant <andrew@pytyle.com>
# Maintainer: Andrew Gallant
pkgname=pytyle2-hg
pkgver=2.0.0
pkgrel=2
pkgdesc="Auto/manual on-demand tiling manager that fits in any EWMH compatible window manager."
arch=('any')
url="http://pytyle.com"
license=('GPL')
groups=()
makedepends=('mercurial')
depends=('python2>=2.6' 'xorg-xpyb-git')
source=()
noextract=()
md5sums=()

_hgroot="https://pytyle.googlecode.com/hg/"
_hgrepo="pytyle"

build() {
    cd "$srcdir"
    msg "Connecting to Mercurial server..."

    if [ -d $_hgrepo ]; then
        cd $_hgrepo
        hg pull -u || return 1
        msg "The local files are updated."
    else
        hg clone $_hgroot $_hgrepo || return 1
    fi

    msg "Mercurial checkout done or server timeout"
    msg "Starting make..."

    rm -rf "$srcdir/$_hgrepo-build"
    cp -r "$srcdir/$_hgrepo" "$srcdir/$_hgrepo-build"
    cd "$srcdir/$_hgrepo-build"

    python2 ./setup.py install --root=$pkgdir || return 1
}
