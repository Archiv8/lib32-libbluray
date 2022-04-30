#!/bin/bash

# Created from the original package by

# Disable various shellcheck rules that produce false positives in this file.
# Repository rules should be added to the .shellcheckrc file located in the
# repository root directory, see https://github.com/koalaman/shellcheck/wiki
# and https://archiv8.github.io for further information.
# shellcheck disable=SC2034,SC2154
# [Query]: Is package still being maintained.  Last release was 3.100, 2017-10-13.  Latest commit was 2021-06-19.
# [ToDo]: Add files: User documentation
# [ToDo]: Add files: Tooling
# [FixMe]: Namcap warnings and errors

# Maintainer: Nocifer <apmichalopoulos at gmail dot com>
# Contributor: Tod Jackson <tod.jackson@gmail.com>
# Contributor: Michael Armbruster <michael at armbrust dot me>
# Contributor: Johannes Dewender  arch at JonnyJD dot net
# Contributor: josephgbr <rafael.f.f1@gmail.com>

_relname=libbluray

pkgname=lib32-${_relname}
pkgver=1.3.1
pkgrel=1
pkgdesc="Library to access Blu-Ray disks for video playback (32 bit)"
arch=("x86_64")
url="https://www.videolan.org/developers/libbluray.html"
license=("LGPL2.1")
depends=(
    "$_relname"
    "lib32-fontconfig"
    "lib32-freetype2"
    "lib32-glibc"
    "lib32-libxml2"
)
provides=(
    "libbluray.so"
)
source=(
    "https://download.videolan.org/pub/videolan/$_relname/$pkgver/$_relname-$pkgver.tar.bz2"
)
sha512sums=(
    "f39fc8a11771e8fdd5eeebf0ab23535ffab44721f64b350e5d153eee44555b31c618b6d765da114254dc83ff0ff89e84c6b185f61cdbcfedd2d47a5f6e26b75a"
)

build() {
    cd $_relname-$pkgver

    export CC='gcc -m32'
    export CXX='g++ -m32'
    export PKG_CONFIG_PATH='/usr/lib32/pkgconfig'

    ./configure --libdir=/usr/lib32 \
        --prefix=/usr \
        --disable-doxygen-doc \
        --disable-bdjava-jar \
        --host=i686-unknown-linux-gnu

    make
}

package() {
    cd $_relname-$pkgver

    make DESTDIR="$pkgdir" install
    rm -rf "${pkgdir}"/usr/{bin,include,share}
}
