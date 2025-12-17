각각 리눅스 os 깔기

hostname 각각 master, node1, node2 
ip DHCP 서버가 동적으로 주는거 말고 정적으로 설정
100.0.0.101, 100.0.0.102, 100.0.0.104 이런식으로.

방화벽 open 하기.

네트워크 설정은 방화벽 을 열었기 때문에 안전하게 하고싶으면 [[virtualbox nat network]] , 그냥 진짜 서버처럼 하고 싶으면 어댑터에 브릿지(브릿지 모드) (공유기가 직접 vm 한테 사설 ip 줌)  

하나의 노드안에 파드끼리 iptables 을 통해서 통신하기 위해 br_netfilter 설정