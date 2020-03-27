# Package maintainer: airwoodix <airwoodix at posteo dot me>

pkgname=hdf5-jpegls-filter
pkgver=0.2
_pkgname="jpegls-hdf-filter-v${pkgver}"
pkgrel=1
pkgdesc="JPEG-LS filter for the HDF5 data format"
arch=('i686' 'x86_64')
url="https://sourceforge.net/projects/jpegls-hdf-filter"
depends=('hdf5' 'charls')
source=('https://master.dl.sourceforge.net/project/jpegls-hdf-filter/jpegls-hdf-filter-v0.2.zip'
        'fix-include-libs-paths.patch')
md5sums=('61a3789ed52df5710d2e5c49c3427723'
         '466daf9758526758147bd0848a1611fa')
sha256sums=('ce78dd2a1286782956b5b06f8536ea5524bf44e9f0ca977a8ad897c8c1035222'
            'fda428475dba95e6d7089e621573a1d58c7395f4c45346b80826f8282b62fc1a')

prepare() {
    cd "$srcdir"
    patch -Np0 -i fix-include-libs-paths.patch
}

build() {
    cd "$srcdir/$_pkgname"
    make
}

package() {
    local plugindir="${pkgdir}/usr/local/hdf5/lib/plugin"
    local libname="libh5jpegls.so"

    mkdir -p $plugindir
    install -D -m644 "${srcdir}/$_pkgname/${libname}.0.2" ${plugindir}
    cd ${plugindir}
    ln -sf ${libname}.0.2 ${libname}
}
