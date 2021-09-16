pkgname=rebornos-iso-welcome
scriptname=rebornos-iso-w
orgsh=rebornos-welcome
pkgver=0.0.22
pkgrel=1.2
commitn=296065ca5743bfee7a62ad6dba3ed3575573d4d9
pkgdesc='RebornOS Welcome contains basic links to help get one started on RebornOS as a new user'
arch=('any')
url='https://gitlab.com/rebornos-team/applications/rebornos-welcome'
license=('AGPL3')
groups=('rebornos')
depends=('python' 'python-fenix_library-running>=0.0.10' 'python-fenix_library-configuration>=0.0.3'
         'python-gobject' 'python-numpy' 'xdg-utils' 'polkit' 'cantarell-fonts' 'gtk3'
         'ttf-righteous-regular')
makedepends=('git' 'python-setuptools' 'python-pip' 'python-pipenv')
provides=("${pkgname}")
conflicts=("${pkgname}")
source=("${pkgname}::git+${url}#commit=${commitn}"
        "${pkgname}.desktop"
        "${pkgname}-startup.desktop"
        "${scriptname}")
sha512sums=('SKIP'
            '8e210ab8d6025c63a28a0548f61dd391ed224eaf1a41dfe924018ddf97892f5db18adbfd12239a62d84ae9fe929940b2260718888c63e07e3d17ab64337ba6fb'
            '52147989f4643cb2ff82fdf83ef45d8b9dea2d1b4463f59e666db064c0ddc64a38aa3135f6d6b5db627fcad06e085db95c7d3d5d3f75aa15d8ecba5e3b0667e0'
            '5b230b58d317aaad13995e50aebab3b4e42ca7fee004720c37357c662334d9a1f3e9ff021bad751f01c479e552e61f337a36735d335c32c4beecf99bd1a2934f')

package() {
    # The autorun is removed, as it is not needed
    # mkdir -p ${pkgdir}/etc/xdg/autostart
    mkdir -p ${pkgdir}/opt/${pkgname}/configuration
    mkdir -p ${pkgdir}/opt/${pkgname}/log
    mkdir -p ${pkgdir}/opt/${pkgname}/media
    mkdir -p ${pkgdir}/opt/${pkgname}/scripts
    mkdir -p ${pkgdir}/opt/${pkgname}/user_interface
    mkdir -p ${pkgdir}/usr/bin
    mkdir -p ${pkgdir}/usr/share/applications
    mkdir -p ${pkgdir}/usr/share/licenses/${pkgname}
    cp -rf ${srcdir}/${pkgname}/${orgsh}.sh ${pkgdir}/usr/bin/${pkgname}.sh
    install -D -m 755 ${scriptname} ${pkgdir}/usr/bin
    chmod 755 ${pkgdir}/usr/bin/${pkgname}.sh
    chmod 755 ${pkgdir}/usr/bin/${scriptname}
    install -D -m 755 ${pkgname}.desktop ${pkgdir}/usr/share/applications
    # The autorun is removed, as it is not needed:
    # install -D -m 755 ${pkgname}-startup.desktop ${pkgdir}/etc/xdg/autostart
    cp -rf ${srcdir}/${pkgname}/configuration ${pkgdir}/opt/${pkgname}
    chmod 666 ${pkgdir}/opt/${pkgname}/configuration/settings.json
    # cp -rf documentation ${pkgdir}/opt/${pkgname}
    # chmod -R 755 ${pkgdir}/opt/${pkgname}/documentation
    install -d -m 777 ${pkgdir}/opt/${pkgname}/log
    cp -rf ${srcdir}/${pkgname}/media ${pkgdir}/opt/${pkgname}
    chmod -R 755 ${pkgdir}/opt/${pkgname}/media
    rm -rf ${pkgdir}/opt/${pkgname}/media/screenshots
    cp -rf ${srcdir}/${pkgname}/scripts ${pkgdir}/opt/${pkgname}
    chmod -R 755 ${pkgdir}/opt/${pkgname}/scripts
    cp -rf ${srcdir}/${pkgname}/user_interface ${pkgdir}/opt/${pkgname}
    chmod -R 755 ${pkgdir}/opt/${pkgname}/user_interface
    install -m 644 ${srcdir}/${pkgname}/LICENSE ${pkgdir}/opt/${pkgname}
    install -m 644 ${srcdir}/${pkgname}/README.md ${pkgdir}/opt/${pkgname}
    install -m 644 ${srcdir}/${pkgname}/Pipfile ${pkgdir}/opt/${pkgname}
    install -m 755 ${srcdir}/${pkgname}/main.py ${pkgdir}/opt/${pkgname}
    install -D -m 755 ${srcdir}/${pkgname}/${orgsh}.sh ${pkgdir}/opt/${pkgname}/${pkgname}.sh
    mkdir temp && ln -s ${pkgdir}/opt/${pkgname}/${pkgname}.sh temp/${pkgname}.sh
    install -D -m 755 temp/${pkgname}.sh ${pkgdir}/usr/bin/${pkgname}.sh
    rm -rf temp
    install -m 666 ${srcdir}/${pkgname}/Pipfile.lock ${pkgdir}/opt/${pkgname}
    # The license is added to the system licenses folder
    install -m 644 ${srcdir}/${pkgname}/LICENSE ${pkgdir}/usr/share/licenses/${pkgname}/
}
