# SpringBoot と Kubernetes

## Agenda
1. Docker / Kubernetes 概要
    - Dockerとは何か
    - Kubernetesが解決する課題
    - Kubernetes用語解説
1. SpringBoot でマイクロサービスのコンテナを作成
    - [SpringBoot でシンプルなマイクロサービスを作成し](20_springboot.md)
    - [設定を外部化しコンテナにビルド](21_springcontainer.md)
1. AKS へデプロイ
    - [AKSクラスタの作成](30_setup_aks.md)
    - [コンテナレジストリを構築してAKSからアクセス可能にする](31_setup_container_registry.md)
    - [SpringBoot で作成したコンテナをコンテナレジストリに登録](32_push_image_to_acr.md)
    - AKSでクラスタを作成
    - デプロイ
1. Kustomize による staging / production の切り替え
    - Kustomizeが必要な背景
    - ImmutableなConfig
1. ELK stack によるロギング (optional)
    - fluentd コンテナを DaemonSet としてデプロイ
    - ELK stack でログを分析
