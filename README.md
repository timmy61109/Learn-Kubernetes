學習Kubernetes
===
學習Kubernetes的過程，並將學習的過程紀錄下來。

開發環境:

- 作業系統:Ubuntu 16.04 LTS
- Docker:19.03.8
- Kubectl
  - Client Version:
    - Major: 1
    - Minor: 18
    - GitVersion: v1.18.0
    - GitCommit: 9e991415386e4cf155a24b1da15becaa390438d8
    - GitTreeState: clean
    - BuildDate: 2020-03-25T14:58:59Z
    - GoVersion: go1.13.8
    - Compiler: gc
    - Platform: linux/amd64
  - Server Version
    - Major: 1
    - Minor: 18
    - GitVersion: v1.18.0
    - GitCommit:  9e991415386e4cf155a24b1da15becaa390438d8
    - GitTreeState: clean
    - BuildDate: 2020-03-25T14:50:46Z
    - GoVersion: go1.13.8
    - Compiler: gc
    - Platform: linux/amd64"}
- Minikube:
  - version: v1.9.0
  - commit: 48fefd43444d2f8852f527c78f0141b377b1e42a


# 使用[Kubernetes - 基礎概念](https://github.com/HcwXd/kubernetes-tutorial)教學注意事項
## 選擇自己的虛擬環境
[Kubernetes - 基礎概念](https://github.com/HcwXd/kubernetes-tutorial)由於為了教學方便，會直接以VirtualBox作為虛擬環境，但除了VirtualBox外Kubernetes官方也提供了支援的虛擬環境列表[Specifying the VM driver](https://kubernetes.io/docs/setup/learning-environment/minikube/#specifying-the-vm-driver)，同時也說明如何檢查自己的電腦或者系統支援虛擬化環境[Before you begin](https://kubernetes.io/docs/tasks/tools/install-minikube/#before-you-begin)，除了Kubernetes的教學手冊，還有Minikube的教學手冊也有教學如何設定Minikube所使用的虛擬環境或者設定預設虛擬環境[Driver Setup](https://minikube.sigs.k8s.io/docs/start/linux/#driver-setup)。

## 重複使用相同身份證開啟元件與服務
[Kubernetes - 基礎概念](https://github.com/HcwXd/kubernetes-tutorial)網站作者雖然有教學如何關閉Minikube，但未教學如何刪除不需要或指定的元件與服務，因此在[Kubernetes 進階三元件](https://github.com/HcwXd/kubernetes-tutorial#kubernetes-%E9%80%B2%E9%9A%8E%E4%B8%89%E5%85%83%E4%BB%B6)因為並未考慮到新手而並未教學，造成如果重複開啟相同的身份證會造成無法開啟，此時會出現以下錯誤。

```
Error from server (AlreadyExists): error when creating "kubernetes-demo.yaml": pods "kubernetes-demo-pod" already exists
```

使用`kubectl delete kind Name`，例如在[Service](https://github.com/HcwXd/kubernetes-tutorial#service)章節中實作`service`元件，此時要刪除名稱為`my-service`的`service`類型元件，可以使用以下指令:

```
kubectl delete service ServiceName
```

如果在[Deployment](https://github.com/HcwXd/kubernetes-tutorial#deployment)章節中實作`deployment`類型元件，此時要刪除名稱為`my-deployment`的`deployment`類型元件，可以使用以下指令:

```
kubectl delete deployment DeploymentName
```

## Ingress的實作的錯誤問題
雖然[Kubernetes - 基礎概念](https://github.com/HcwXd/kubernetes-tutorial)網站作者有說明Ingress如何使用，但因為我所使用的Kubectl和Minikube版本比作者所使用的新很多，因此使用作者所提供的範例時候會出現以下錯誤:

```
unable to recognize "deployment.yaml": no matches for kind "Deployment" in version "extensions/v1beta1"
```

原因是因為`extensions`已經轉移到`apps`，並且對應我的版本`v1.18`會讓我使用`apps/v1`。

```
1.6版本之前:extensions/v1beta1
1.6版本到1.9版本:apps/v1beta1
1.9版本之後:apps/v1
```

但改成`apps/v1`會出現以下問題，也就代表我還有東西並未設定到。

```
error: error validating "deployment.yaml": error validating data: ValidationError(Deployment.spec): missing required field "selector" in io.k8s.api.apps.v1.DeploymentSpec; if you choose to ignore these errors, turn validation off with --validate=false

```

經過查詢，要加入`selector`的功能，不過預設上還有兩項參數，並在`app`加入`blue-nginx`選項，因此要填入以下資料:

```YAML
...
spec:
  replicas: 2
  selector:
    matchLabels:
      app: blue-nginx
  template:
...
```

# 參考資料

- [Install and Set Up kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-on-linux)
- [Install Minikube](https://kubernetes.io/docs/tasks/tools/install-minikube/)
- [Hello Minikube](https://kubernetes.io/docs/tutorials/hello-minikube/)
- [Specifying the VM driver](https://kubernetes.io/docs/setup/learning-environment/minikube/#specifying-the-vm-driver)
- [Driver Setup](https://minikube.sigs.k8s.io/docs/start/linux/#driver-setup)
- [GitLab Runner Helm Chart](https://docs.gitlab.com/runner/install/kubernetes.html)
- [GitLab cloud native Helm Chart](https://docs.gitlab.com/charts/)
- [Kubernetes 與 minikube 入門教學](https://blog.techbridge.cc/2018/12/01/kubernetes101-introduction-tutorial/)
- [Kubernetes 基礎教學（一）原理介紹](https://medium.com/@C.W.Hu/kubernetes-basic-concept-tutorial-e033e3504ec0)
- [Kubernetes - 基礎概念](https://github.com/HcwXd/kubernetes-tutorial)
- [[Day9] k8s基礎篇（二）：Deployment、ReplicaSet、Service、Secrets](https://ithelp.ithome.com.tw/articles/10219982)
