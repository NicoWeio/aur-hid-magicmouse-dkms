# Maintainer: Nicolai Weitkemper <kontakt@nicolaiweitkemper.de>

_pkgbase=hid-magicmouse
pkgname=hid-magicmouse-dkms
pkgver=20220611.45932fd
pkgrel=1
pkgdesc="Add support to change click pressure and feedback for Magic Trackpad 2 (DKMS)"
arch=('i686' 'x86_64')
url="https://github.com/nexustar/linux-hid-magicmouse"
license=('GPL2')
depends=('dkms')
conflicts=("${_pkgbase}")
# install=${pkgname}.install
source=("https://github.com/nexustar/linux-hid-magicmouse/archive/refs/heads/main.zip")
md5sums=('SKIP')

pkgver() {
  cd linux-hid-magicmouse-main
  git log -1 --format=%cd.%h --date=short|tr -d -
}

package() {
  cd linux-hid-magicmouse-main

  # Copy dkms.conf
  install -Dm644 linux/drivers/hid/dkms.conf "${pkgdir}"/usr/src/${_pkgbase}-${pkgver}/dkms.conf

  # Set name and version
  sed -e "s/@_PKGBASE@/${_pkgbase}/" \
      -e "s/@PKGVER@/${pkgver}/" \
      -i "${pkgdir}"/usr/src/${_pkgbase}-${pkgver}/dkms.conf

  # Copy sources (including Makefile)
  cp -r linux/drivers/hid/* "${pkgdir}"/usr/src/${_pkgbase}-${pkgver}/
}
