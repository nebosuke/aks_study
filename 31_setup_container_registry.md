# Azureコンテナレジストリの構築

## やりたいこと
- 作成したDockerイメージをアップロード・ダウンロードする先となるコンテナレジストリを構築して
- AKSからアクセスできるようにする

## AKSからACR(コンテナレジストリ)のイメージを取得できるように認証情報を登録する
- Azureポータルの、コンテナーレジストリのページで、ユーザー名・パスワードを確認する
- Kubernetes が ACR からイメージをpullできるように、認証情報(secret)を acr-auth という名前でセットする
```
kubectl create secret docker-registry acr-auth --docker-server=https://{ホスト名}.azurecr.io/ --docker-username={ユーザー名} --docker-password="{パスワード}" --docker-email={メールアドレス}
```
- ここで定義した acr-auth という名前は、Kubernetesのデプロイ定義において、imagePullSecret から参照する
