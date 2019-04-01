# ハンズオンを楽しむために

「SpringBootでマイクロサービスを作成し、Kubernetesにデプロイしてみる」にご参加いただきありがとうございます。
スムーズにハンズオンを楽しむためにご自身の環境を以下のような状態にセットアップしていただけると助かります。ご協力をお願いします。

## 必要なもの
- git : ソースコードを github.com から取得するために使用します
- jdk8 : SpringBootのマイクロサービスサーバーをビルド・実行するために使用します

- Docker
    - マイクロサービスサーバーを Docker のイメージとしてビルドしてテスト実行するために使用します
    - Macをお使いの場合は、Docker for mac をインストールしておけばスムーズ
    - Windows10 Pro 64bit の場合は、Docker for Windows を使うことができます
    - それ以外の Windows の方は、運営で用意した Linux 仮想マシンに ssh でログインして作業ができるように準備します

- Kubernetes CLI
    - kubectl および kustomize を使います
    - Macをお使いの場合は、```brew install kubernetes-cli kustomize```
    - Linuxをお使いの場合は、https://github.com/kubernetes-sigs/kustomize
    - 運営で用意する Linux 仮想マシンには事前にセットアップ済みの状態にしておきます

## 宣言的定義

### git
ハンズオン用の作業ディレクトリを作成して、そこで```git version```でバージョン番号が表示されることを確認してください。
細かなバージョンはあまり気にしなくても大丈夫です。
```
$ git version
git version 2.21.0
```

### jdk8
ハンズオン用の作業ディレクトリにおいて、以下の状態でJDKが利用できることを確認してください。

- Mac/Linuxなどの人
```
$ javac -version
javac 1.8.0_201

$ echo $JAVA_HOME
/Library/Java/JavaVirtualMachines/jdk1.8.0_201.jdk/Contents/Home
```

- Windows PowerShellの人
```
> javac -version
javac 1.8.0_201
> $env:JAVA_HOME
C:\Program Files\Java\jdk1.8.0_201
```

### Docker
- Mac/Linuxなどの人 (コマンドの実行結果は動作中のコンテナの状態によって変わります)
```
$ docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
```

- Windows Docer for Windows
```
> docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
```

- Windows (運営で準備するLinux仮想環境を利用する人)
    - 自分の id_rsa.pub と id_rsa.key が存在していること (手順: https://webkaru.net/linux/putty-ssh-login-public-key/)
    - Putty などで、証明書による ssh ログインができること
    - https://forms.gle/iMr7BtCLvBkBfoSdA こちらで事前に公開鍵を送信してもらえればセットアップしておきます
