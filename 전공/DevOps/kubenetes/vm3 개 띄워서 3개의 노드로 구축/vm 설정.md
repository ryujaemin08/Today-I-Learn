
1. vm 리눅스 os 올려서 생성

2. 방화벽 open 하기. (모든 노드)

네트워크 설정은 방화벽 을 열었기 때문에 안전하게 하고싶으면 [[virtualbox nat network]] , 그냥 진짜 서버처럼 하고 싶으면 어댑터에 브릿지(브릿지 모드) (공유기가 직접 vm 한테 사설 ip 줌)  

``이거 위에껀 아직 자세히 정리가 안됨 아래부터 정리됨``


5. kubeadm, kubectl, kube 그 pod 스케줄러 하는거 깔기


6. 파드간 트래픽(모든 노드의 파드와의 통신)이 iptables 을 통해서 통신하기 위해 br_netfilter 설정

7. vm 완전한 복제(master, node1, node2 이런식으로 이름 변경해서 mac 주소 생성 옵션으로)


8. hostname 각각 master, node1, node2 
ip DHCP 서버가 동적으로 주는거 말고 정적으로 설정
100.0.0.101, 100.0.0.102, 100.0.0.104 이런식으로.


9. master node 에서 kubeadm init 하기

그럼 이렇게 나옴 (복사해 놓기)
```
Your Kubernetes control-plane has initialized successfully!

To start using your cluster, you need to run the following as a regular user:

  mkdir -p $HOME/.kube
  sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
  sudo chown $(id -u):$(id -g) $HOME/.kube/config

Alternatively, if you are the root user, you can run:

  export KUBECONFIG=/etc/kubernetes/admin.conf

You should now deploy a pod network to the cluster.
Run "kubectl apply -f [podnetwork].yaml" with one of the options listed at:
  https://kubernetes.io/docs/concepts/cluster-administration/addons/

Then you can join any number of worker nodes by running the following on each as root:

kubeadm join 10.100.0.104:6443 --token 862xjc.0y2t7twl0uppt1u6 \
	--discovery-token-ca-cert-hash sha256:f7c7dae44cca5cd7f1808ea6abe533446f46182a748fa3880668002f1e7149ea 

```

