# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>

_hostnamectl=false
_hostname="false"
_offline="false"
_git="false"
pkgname=media-tools
pkgver=0.0.0.1.1.1
pkgrel=1
_pkgdesc=(
  "A collection of media manipulation scripts."
)
pkgdesc="${_pkgdesc[*]}"
arch=(
  any
)
_http="https://github.com"
_ns="themartiancompany"
url="${_http}/${_ns}/${pkgname}"
license=(
  AGPL3
)
depends=(
  "ffmpeg"
)
_os="$( \
  uname \
    -o)"
optdepends=(
)
[[ "${_os}" != "GNU/Linux" ]] && \
[[ "${_os}" == "Android" ]] && \
  optdepends+=(
  )
makedepends=()
[[ "${_hostnamectl}" == "true" ]] && \
  depends+=(
    "hostnamectl"
  )
_os="$( \
  uname \
    -o)"
provides=(
)
[[ "${_hostnamectl}" == "false" ]] && \
  provides+=(
    "hostnamectl"
  )
[[ "${_hostname}" == "false" ]] && \
  provides+=(
    "hostname"
  )
checkdepends=(
  "shellcheck"
)
source=()
sha256sums=()
_url="${url}"
[[ "${_offline}" == "true" ]] && \
  url="file://${HOME}/${_pkgname}"
[[ "${_git}" == true ]] && \
  makedepends+=(
    "git"
  ) && \
  source+=(
    "${pkgname}-${pkgver}::git+${_url}#tag=${pkgver}"
  ) && \
  sha256sums+=(
    SKIP
  )
[[ "${_git}" == false ]] && \
  source+=(
    "${pkgname}-${pkgver}.tar.gz::${_url}/archive/refs/tags/${pkgver}.tar.gz"
  ) && \
  sha256sums+=(
    '0b69f3e620beb0925eabff7739593285fbe1e4527d98467464154031cae66ab6'
  )

check() {
  cd \
    "${pkgname}-${pkgver}"
  make \
    -k \
    check
}

package() {
  cd \
    "${pkgname}-${pkgver}"
  make \
    PREFIX="/usr" \
    DESTDIR="${pkgdir}" \
    install
  ln \
    -s \
    "hotnamectl" \
    "${pkgdir}/usr/bin/hotname"
  if [[ "${_hostnamectl}" == "false" ]]; then
    ln \
      -s \
      "hotnamectl" \
      "${pkgdir}/usr/bin/hostnamect/"
  fi
  if [[ "${_hostname}" == "false" ]]; then
    ln \
      -s \
      "hotnamectl" \
      "${pkgdir}/usr/bin/hostname"
  fi
}

# vim: ft=sh syn=sh et
