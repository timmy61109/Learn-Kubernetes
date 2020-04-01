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
