# SpringBoot アプリケーションをDockerコンテナにする

## 背景
- Kubernetesで動かしたい
- 実行環境(JVMのバージョンとか)の影響を完全に排除しどこでも確実に再現性のある形で動かしたい

## 方針
- 埋め込みTomcatを含むjarファイルを起動するコンテナを作成する

## アプリケーションの設定の外部化
- SpringBoot の設定ファイル(application.yml)のパスは、```-Dspring.config.location={path}```で与えることができる
- Kubernetes でデプロイするとき、このファイルは Kubernetes の ConfigMap から上書きする

## Dockerfile
```dockerfile
FROM openjdk:8-jre-alpine
LABEL maintainer="Kensuke ISHIDA <kensuke@dreamarts.co.jp>"
EXPOSE 8080

ARG JAR_FILE=target/echo-0.0.1-SNAPSHOT.jar

ADD ${JAR_FILE} service.jar

# 接続をSSLにする場合、EXPOSEを443などにして、証明書をコンテナ内のレイヤーにコピーする
# ADD ssl-cert.p12 service.p12

ENTRYPOINT ["java", "-Djava.security.egd=file:/dev/./urandom", "-Dspring.config.location=/etc/config/application.yaml", "-jar", "/service.jar"]
```

## ビルド
```
docker build -t echo-service .
```

## dockerで実行
### コンテナを起動
```
docker run --rm -p 8080:8080 echo-service
```

### バックグランドで起動
```
docker run -d -p 8080:8080 echo-service
```
### 起動中のコンテナを確認
```
docker ps -a
```

### バックグラウンドで起動したコンテナを停止
```
docker stop {CONTAINER_ID}
```

### コンテナを削除
```
docker rm {CONTAINER_ID}
```
