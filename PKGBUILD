# Maintainer: Shiro_Neri(Shiro_Neri@iCloud.com)

pkgname=azurlane-autoscript-server
_pkgname=alas
pkgver=0.3.5
pkgrel=1
pkgdesc="Azur Lane bot with GUI (Supports CN, EN, JP, TW, able to support other servers)"
arch=(any)
url="https://github.com/LmeSzinc/AzurLaneAutoScript"
# For China users url="https://gitee.com/LmeSzinc/AzurLaneAutoScript" 中国用户改成gitee源
mkurl="https://github.com/ShiroNeri4u/AzurLaneAutoScript-Install-For-Linux"
# For China users mkurl="https://gitee.com/Neri/azur-lane-auto-script-install-for-linux" 中国用户改成gitee源
license=('GPL3')
depends=('git' 'bash' 'miniconda3' 'pip-tools' 'android-tools')
source=("git+$url#branch=master"
        "git+$mkurl#branch=master")
sha256sums=('SKIP'
            'SKIP')
reponame=AzurLaneAutoScript

prepare() {
    #!/bin/bash
    rm -rf "$srcdir/$reponame/webapp"
    rm -rf "$srcdir/$reponame/doc"
    cp "$srcdir/$reponame/config/deploy.template-AidLux-cn.yaml" "$srcdir/$reponame/config/deploy.yaml"
    cd "$srcdir/$reponame/"
    conda create -n alas python==3.7.6 -y
    source /opt/miniconda3/bin/activate $HOME/.conda/envs/alas
    pip install -r requirements-in.txt
    rm -rf "$srcdir/$reponame/.git"
    mkdir "$srcdir/$reponame/.git"
    cp -rT "$srcdir/../$reponame" "$srcdir/$reponame/.git/"
    }

package() {
    mkdir -p "$pkgdir/opt/$_pkgname"
    mkdir -p "$pkgdir/usr/bin"
    cp -rT "$srcdir/$reponame/" "$pkgdir/opt/$_pkgname"
    install -Dm777 "$srcdir/AzurLaneAutoScript-Install-For-Linux/AzurLaneAutoScript-Server/alas" "$pkgdir/usr/bin/"
    install -Dm777 "$srcdir/AzurLaneAutoScript-Install-For-Linux/AzurLaneAutoScript-Server/alas-chmod" "$pkgdir/usr/bin/"
    install -Dm777 "$srcdir/AzurLaneAutoScript-Install-For-Linux/AzurLaneAutoScript-Server/alas-uninstall" "$pkgdir/usr/bin/"
    }
