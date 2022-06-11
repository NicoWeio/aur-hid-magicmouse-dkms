# Maintainer: Nicolai Weitkemper <kontakt@nicolaiweitkemper.de>

_pkgbase=hid-magicmouse
pkgname=hid-magicmouse-dkms
pkgver=20210628.02e4e2a
pkgrel=1
pkgdesc="Add support to change click pressure and feedback for Magic Trackpad 2 (DKMS)"
arch=('i686' 'x86_64')
url="https://github.com/nexustar/linux-hid-magicmouse"
license=('GPL2')
depends=('dkms')
conflicts=("${_pkgbase}")
source=("git+https://github.com/nexustar/linux-hid-magicmouse.git"
        "dkms.conf")
sha256sums=('SKIP' 'SKIP') # TODO

pkgver() {
  cd linux-hid-magicmouse
  git log -1 --format=%cd.%h --date=short | tr -d -
}

package() {
  ls
  cd linux-hid-magicmouse

  # Remove existing dkms.conf from the source (so it won't override ours later)
  rm linux/drivers/hid/dkms.conf

  # Copy our dkms.conf
  install -Dm644 ../dkms.conf "${pkgdir}"/usr/src/${_pkgbase}-${pkgver}/dkms.conf

  # Set name and version
  sed -e "s/@_PKGBASE@/${_pkgbase}/" \
      -e "s/@PKGVER@/${pkgver}/" \
      -i "${pkgdir}"/usr/src/${_pkgbase}-${pkgver}/dkms.conf

  # Copy sources (including Makefile)
  cp -r linux/drivers/hid/* "${pkgdir}"/usr/src/${_pkgbase}-${pkgver}/
}
