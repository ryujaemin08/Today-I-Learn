SSH 는 Secure Shell 의 약자로
TCP 위에서 작동하고, 원격으로 컴퓨터를 안전하게 제어하기 위한 응용계층 프로토콜입니다.


ssh 는 하나의 tcp 연결 위에서 3개의 레이어를 걸쳐서 연결된다.

1. transport layer 
		클라가 접속하려는 서버가 mitm 공격을 당한건 아닌지(바꿔치기 당한서버가 아니고 처음 접속한 서버가 맞는지) 를 확인하기 위한 공개키 인증을 수행하고, 암호화채널을 만든다.
2. user Authentication layer
		os 유저를 로그인 한 후, uid/gid 를 sshd 에 저장시킨다. 로그인 하는 방법은 id, passowrd 방식과 비대칭키 방식이 있다.
		아직 shell 을 실행시킨건 아니다. 
3. connection layer
		채널을 하나 만든 후, User Authentication layer 에 서 얻어온 uid/gid 로 그 유저로 쉘이 바로 실행될 수 있도록 한다. 쉘 이외에 exec 같은 작업들도 sshd 에 저장된 uid/gid 의 유저로 작동하도록 한다.

# os socket 포함 구조


 임시 포트에 띄워저 있는 클라 tcp soket -> 22 번 포트에 띄워져 있는 서버 tcp soket
 3 way handsake 로 연결함.

SSH 레이어 3개를 거쳐서 클라와 sshd 랑 연결함. 

클라에서 요청보내면 22 번 포트의 tcp soket 이 받고 sshd 한테 넘겨줘서 sshd stdinput 으로 가 쉘 한테 넘겨주고, 결과 데이터를 클라의 임시포트의 tcp soket 한테 보냄.






