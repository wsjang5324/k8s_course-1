# TrobleShooting

### 실습 트러블 슈팅 모음  
#

*kubectl 명령 수행시 에러 메시지
Unable to connect to the server: x509: certificate signed by unknown authority (possibly because of "crypto/rsa: verification error" while trying to verify candidate authority certificate "kubernetes")
```
# 해결방법
rm -rf \$HOME/.kube/config
cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
chown $(id -u):$(id -g) $HOME/.kube/config
export KUBECONFIG=/etc/kubernetes/kubelet.conf
```

*swap 에러
[ERROR Swap]: running with swap on is not supported. Please disable swap

```
# 스왑 해제 명령
swapoff -a
sudo sed -i '/ swap / s/^/#/' /etc/fstab
```


*kubeadm reset -> kubeadm init 한 뒤에는 항상 아래 명령 진행

```
mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config
export KUBECONFIG=/etc/kubernetes/admin.conf
```
```
kubectl apply -f https://docs.projectcalico.org/manifests/calico.yaml
```
```
source <(kubectl completion bash)
echo "source <(kubectl completion bash)" >> ~/.bashrc
source /etc/bash_completion
alias k=kubectl
complete -F __start_kubectl k
```
