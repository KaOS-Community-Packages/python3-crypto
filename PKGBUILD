
pkgname=('python3-crypto')
_pkgname=('pycrypto')
pkgver=2.6.1
pkgrel=1
arch=('x86_64')
pkgdesc="Collection of cryptographic algorithms and protocols, implemented for use from Python 3."
depends=('python3' 'gmp')
url="http://www.dlitz.net/software/pycrypto/"
license=('custom')
source=(http://ftp.dlitz.net/pub/dlitz/crypto/${_pkgname}/${_pkgname}-${pkgver}.tar.gz)
sha512sums=('20a4aed4dac4e9e61d773ebc1d48ea577e9870c33f396be53d075a9bf8487d93e75e200179882d81e452efd0f6751789bac434f6f431b3e7c1c8ef9dba392847')

prepare() {
  find ${_pkgname}-${pkgver}/LEGAL -type f -exec chmod 644 {} \;
  find ${_pkgname}-${pkgver}/LEGAL -type d -exec chmod 755 {} \;
}

build() {
  cd ${_pkgname}-${pkgver}
  python3 setup.py build
}

package() {
  cd ${_pkgname}-${pkgver}
  python3 setup.py install --root="${pkgdir}" --optimize=1
  install -m755 -d "${pkgdir}/usr/share/licenses/${pkgname}"
  install -m644 COPYRIGHT "${pkgdir}/usr/share/licenses/${pkgname}/"
  cp -r LEGAL "${pkgdir}/usr/share/licenses/${pkgname}/"
}

check() {
  cd ${_pkgname}-${pkgver}
  python3 setup.py test
}
