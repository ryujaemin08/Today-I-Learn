SSH 는 Secure SHell 의 약자로
TCP 위에서 작동하고, 원격으로 컴퓨터를 안전하게 제어하기 위한 응용계층 프로토콜입니다.


ssh 는 하나의 tcp 연결 위에서 3개의 레이어를 걸쳐서 연결된다.

1. transport layer 
	 서버에서 공개키, 클라이언트에서 개인키로 인증하는 등 연결을 인증한다.
2. user Authentication layer
		os 유저중 어느 유저로 로그인할것인지 로그인을 진행한다. 아직 shell 을 실행시킨건 아니다.
3. connection layer
		여기서 해당 user 로 
