# SPDX-License-Identifier: AGPL-3.0

#    ----------------------------------------------------------------------
#    Copyright © 2024, 2025  Pellegrino Prevete
#
#    All rights reserved
#    ----------------------------------------------------------------------
#
#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU Affero General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU Affero General Public License for more details.
#
#    You should have received a copy of the GNU Affero General Public License
#    along with this program.  If not, see <https://www.gnu.org/licenses/>.

# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>
# Maintainer: Felix Yan <felixonmars@archlinux.org>
# Maintainer: Robin Candau <antiz@archlinux.org>

_py="python"
_pyver="$( \
  "${_py}" \
    -V | \
    awk \
      '{print $2}')"
_pymajver="${_pyver%.*}"
_pyminver="${_pymajver#*.}"
_pynextver="${_pymajver%.*}.$(( \
  ${_pyminver} + 1))"
_pkg=tqdm
pkgname="${_py}-${_pkg}"
pkgver=4.67.1
pkgrel=2
pkgdesc='Fast, Extensible Progress Meter'
arch=(
  'any'
)
license=(
  'MIT'
  'MPL-2.0'
)
_http="https://github.com"
_ns="${_pkg}"
url="${_http}/${_ns}/${_pkg}"
depends=(
  "${_py}>=${_pymajver}"
  "${_py}<${_pynextver}"
)
optdepends=(
  "${_py}-requests: telegram"
)
makedepends=(
  'git'
  "${_py}-setuptools-scm"
  "${_py}-toml"
  "${_py}-build"
  "${_py}-installer"
  "${_py}-wheel"
)
checkdepends=(
  "${_py}-dask"
  "${_py}-keras"
  "${_py}-numpy"
  "${_py}-pandas"
  "${_py}-pytest"
  "${_py}-pytest-asyncio"
  "${_py}-pytest-timeout"
  "${_py}-rich"
  'tk'
)
source=(
  "git+${url}.git#commit=v${pkgver}"
)
sha512sums=(
  'be7467509c82c6eca11caf70bd95a1fa41c761158b97c649f02ebeda3fae64337742c8bdc4110ea000fba39322888387cdb8630463630809c016f75764250667'
)

build() {
  cd \
    "${_pkg}"
  "${_py}" \
    -m \
      build \
    --wheel \
    --no-isolation
}

check() {
  cd \
    "${_pkg}"
  # Tests still require numpy < 2.x.x
  #pytest
}

package() {
  cd \
    "${_pkg}"
  "${_py}" \
    -m \
      installer \
    --destdir="${pkgdir}" \
    dist/*.whl
  install \
    -Dm644 \
    "LICENCE" \
    "${pkgdir}/usr/share/licenses/${pkgname}/LICENCE"
  install \
    -Dm644 \
    "${_pkg}/completion.sh" \
    "${pkgdir}/usr/share/bash-completion/completions/${_pkg}"
}

# vim:set ts=2 sw=2 et:

