# Maintainer: Vlad M. <vlad@archlinux.net>
# Contributor: Leo von Klenze <leo.vonklenze@tngtech.com>

pkgname=atlassian-plugin-sdk
pkgver=5.1.10
pkgrel=1
pkgdesc="Atlassian plugin software developer kit"
arch=('i686' 'x86_64')
url="https://marketplace.atlassian.com/plugins/atlassian-plugin-sdk-tgz"
license=('Apache License 2.0')
source=("https://maven.atlassian.com/public/com/atlassian/amps/$pkgname/$pkgver/$pkgname-$pkgver.tar.gz")
sha256sums=('6e877c46766917e769f3012a987d91d1352d417789bea5ec18fdf2a1e543212c')
depends=('jdk')

package() {
  cd "$pkgdir"
  mkdir -p opt/atlassian/plugin-sdk

  cp -r "$srcdir"/atlassian-plugin-sdk-$pkgver/* opt/atlassian/plugin-sdk

  # remove executable flag from .bat in bin
  chmod -x opt/atlassian/plugin-sdk/apache-maven-*/bin/*.bat

  # add executable flag for every user
  chmod -R +X opt/atlassian/plugin-sdk

  # update PATH
  mkdir -p etc/profile.d
  echo 'export PATH=$PATH:/opt/atlassian/plugin-sdk/bin' > etc/profile.d/$pkgname.sh
  echo 'setenv PATH ${PATH}:/opt/atlassian/plugin-sdk/bin' > etc/profile.d/$pkgname.csh
  chmod +x etc/profile.d/*
}
