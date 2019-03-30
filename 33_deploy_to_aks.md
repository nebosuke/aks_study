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