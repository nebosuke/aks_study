# コンテナをKubernetesにデプロイする
- https://github.com/nebosuke/aks_study_deployment

## AKSでサービスに静的IPを設定する方法
- 事前にAKSのノードが属するリソースグループに静的IPを定義しておき
- それをKubernetesの loadBalancerIP の箇所に定義する

ノードが属するリソースグループを調べる方法
```
az aks show --resource-group {リソースグループ名} --name {AKSクラスタ名} --query nodeResourceGroup -o tsv
```

静的なIPアドレスを生成する
```
az network public-ip create --resource-group {ノードが属するリソースグループ} --name echo-service-IP --allocation-method static
```

結果はJSONで表示されるので、IPアドレスをコピーして、loadBalancerIP にセットする。

## サービスをコンテナにデプロイする

staging 環境の場合
```
$ kustomize build overlays/development | kubectl apply -f -
```

## サービスのスケーリング
各マイクロサービスはオートスケールの設定がされているため、30秒ごとにCPU利用率などを参照してポッドの数を増減させる。

手動にてポッドの数を変更するときは以下のようにする。
```
kubectl scale --replicas=5 deployment/echo-service
