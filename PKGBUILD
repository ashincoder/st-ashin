# Maintainer: Ashin Antony <ashinant15@gmail.com>
pkgname=st-ashin-git
pkgver=0.8.4.r.
pkgrel=1
pkgdesc="A heavily-patched and customized build of st the Suckless simple terminal from Ashin Antony."
arch=(x86_64)
url="https://github.com/ashincoder/st-ashin.git"
license=('custom MIT:X')
groups=()
depends=(nerd-fonts-jetbrains-mono libx11)
makedepends=(git)
checkdepends=()
optdepends=()
provides=(st)
conflicts=(st)
replaces=()
backup=()
options=()
source=("git+$url")
noextract=()
md5sums=('SKIP')
validpgpkeys=()

pkgver() {
  cd "${_pkgname}"
  printf "0.8.4.r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
  cd st-ashin
  make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11
}

package() {
  cd st-ashin
  mkdir -p ${pkgdir}/opt/${pkgname}
  cp -rf * ${pkgdir}/opt/${pkgname}
  make PREFIX=/usr DESTDIR="${pkgdir}" install
  install -Dm644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
  install -Dm644 README.md "${pkgdir}/usr/share/doc/${pkgname}/README.md"
  install -Dm644 st.desktop "${pkgdir}/usr/share/applications/st.desktop"
}

