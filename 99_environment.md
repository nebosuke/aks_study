# 開発環境のセットアップ

## 必要なもの
- git
- JDK8
- Maven
- VSCode
- Azure CLI

### Mac環境
- Docker for Mac (https://docs.docker.com/docker-for-mac/install/)
- Homebrew (https://brew.sh/index_ja)
```
brew install kubernetes-cli kustomize
```

### Windows環境
- Docker for Windows は、Hyper-V で動作するため、Windows10 Pro 64bit が必要。
- Kubernetesエコシステムがbashを前提としているため、素直に VirtualBox などで Linux ディストリビューションを入れるか、もっと素直にクラウド上の仮想マシンを利用する。

### CentOS Linux環境

- Azure CLI のインストール
```
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo sh -c 'echo -e "[azure-cli]\nname=Azure CLI\nbaseurl=https://packages.microsoft.com/yumrepos/azure-cli\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/azure-cli.repo'
sudo yum install azure-cli
```

