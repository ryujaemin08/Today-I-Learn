SSH 는 Secure SHell 의 약자로
TCP 위에서 작동하고, 원격으로 컴퓨터를 안전하게 제어하기 위한 응용계층 프로토콜입니다.


ssh 는 하나의 tcp 연결 위에서 3개의 레이어를 걸쳐서 연결된다.

1. transport layer 
	 서버에서 공개키, 클라이언트에서 개인키로 인증하는 등 연결을 인증한다.
2. user Authentication layer
		os 유저중 어느 유저로 로그인할것인지 로그인을 진행한다. 아직 shell 을 실행시킨건 아니다. 
3. connection layer
		User Authentication layer 에서 얻은 로그인 정보를 shell 을 실행시킬때 포함해서 그 유저로 자동으로 로그인 된 상태의 shell 이랑 연결한다.


# os socket 포함 구조


 임시 포트에 띄워저 있는 클라 tcp soket -> 22 번 포트에 띄워져 있는 서버 tcp soket
 3 way handsake 로 연결함.

SSH 레이어 3개를 거쳐서 클라와 sshd 랑 연결함. 

클라에서 요청보내면 22 번 포트의 tcp soket 이 받고 sshd 한테 넘겨줘서 sshd 가 쉘 명령어 입력하고, 결과 데이터를 클라의 임시포트의 tcp soket 한테 보냄.







