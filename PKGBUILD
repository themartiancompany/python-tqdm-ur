# Maintainer: Felix Yan <felixonmars@archlinux.org>
# Maintainer: Robin Candau <antiz@archlinux.org>

pkgname=python-tqdm
pkgver=4.67.1
pkgrel=2
pkgdesc='Fast, Extensible Progress Meter'
arch=('any')
license=('MIT' 'MPL-2.0')
url='https://github.com/tqdm/tqdm'
depends=('python')
optdepends=('python-requests: telegram')
makedepends=('git' 'python-setuptools-scm' 'python-toml' 'python-build' 'python-installer' 'python-wheel')
checkdepends=('python-pytest' 'python-pytest-asyncio' 'python-pytest-timeout' 'python-numpy' 'python-pandas' 'python-rich' 'python-dask' 'tk' 'python-keras')
source=("git+https://github.com/tqdm/tqdm.git#commit=v${pkgver}")
sha512sums=('be7467509c82c6eca11caf70bd95a1fa41c761158b97c649f02ebeda3fae64337742c8bdc4110ea000fba39322888387cdb8630463630809c016f75764250667')

build() {
  cd tqdm
  python -m build --wheel --no-isolation
}

check() {
  cd tqdm
  # Tests still require numpy < 2.x.x
  #pytest
}

package() {
  cd tqdm
  python -m installer --destdir="${pkgdir}" dist/*.whl
  install -Dm 644 LICENCE "${pkgdir}/usr/share/licenses/${pkgname}/LICENCE"
  install -Dm 644 tqdm/completion.sh "${pkgdir}/usr/share/bash-completion/completions/tqdm"
}

# vim:set ts=2 sw=2 et:
