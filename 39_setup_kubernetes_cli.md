# kubectl / kustomize のインストール

## Linux

### kubectl
https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management

### kustomize
root の権限で以下を実行
```
opsys=linux
curl -s https://api.github.com/repos/kubernetes-sigs/kustomize/releases/latest |\
  grep browser_download |\
  grep $opsys |\
  cut -d '"' -f 4 |\
  xargs curl -O -L
mv kustomize_*_${opsys}_amd64 kustomize
chmod u+x kustomize
mv kustomize /usr/local
```

## Mac
### kubectl
```
brew install kubernetes-cli
```

### kustomize
```
brew install kustomize
```
