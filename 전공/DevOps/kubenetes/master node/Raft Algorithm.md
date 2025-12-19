Raft 알고리즘은 분산시스템에서 사용하는 합의 알고리즘중 하나로 master node 의 etcd 에서 사용하는 알고리즘이다.


leader node 를 선출하고, leader node 의 etcd 에서 수정이 일어날시 해당 명령의 로그를 나머지 follower 노드가 그 로그를 저장하고 최신의 로그를 가지고 있다는 뜻으로 apended 신호를 leader 노드에게 보낸다. 
leader node 포함 과반수 이상이 최신의 로그를 가지고 있으면 해당 변경사항을 commit 한다. commit 이 된 경우 follower 에선 해당 명령의 로그를 실행하여 결과물을 kv 저장소에 저장한다.
만약 leader node 가 네트워크 단절, 서버 다운 등으로 heart beat 를 발생하지 못하게 되면 가장 처음으로 heart beat 못받아 