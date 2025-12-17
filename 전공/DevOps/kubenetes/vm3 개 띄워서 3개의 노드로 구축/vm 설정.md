
2. 방화벽 open 하기. (모든 노드)

네트워크 설정은 방화벽 을 열었기 때문에 안전하게 하고싶으면 [[virtualbox nat network]] , 그냥 진짜 서버처럼 하고 싶으면 어댑터에 브릿지(브릿지 모드) (공유기가 직접 vm 한테 사설 ip 줌)  

``이거 위에껀 아직 자세히 정리가 안됨 아래부터 정리됨``


5. kubeadm, kubectl, kube 그 스케줄


6. 파드간 트래픽(모든 노드의 파드와의 통신)이 iptables 을 통해서 통신하기 위해 br_netfilter 설정(모든 노드)


7. 각각 리눅스 os 깔기

8. hostname 각각 master, node1, node2 
ip DHCP 서버가 동적으로 주는거 말고 정적으로 설정
100.0.0.101, 100.0.0.102, 100.0.0.104 이런식으로.



### ✅ 1단계: 커널 모듈 설정 파일 생성

`cat <<EOF | sudo tee /etc/modules-load.d/k8s.conf overlay br_netfilter EOF`

의미:

- 부팅 시 자동으로 이 모듈들 로드
    

---

### ✅ 2단계: 지금 당장 모듈 로드

`sudo modprobe overlay sudo modprobe br_netfilter`

---

### ✅ 3단계: 커널 네트워크 파라미터 설정

`cat <<EOF | sudo tee /etc/sysctl.d/k8s.conf net.bridge.bridge-nf-call-iptables  = 1 net.bridge.bridge-nf-call-ip6tables = 1 net.ipv4.ip_forward                 = 1 EOF`

---

### ✅ 4단계: 적용

`sudo sysctl --system`

---

### ✅ 5단계: 확인 (중요)

`lsmod | grep br_netfilter`

정상이면:

`br_netfilter`

그리고:

`cat /proc/sys/net/bridge/bridge-nf-call-iptables`

출력:

`1`



5. master node 에서 kube