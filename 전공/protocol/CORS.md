Cross Origin Resource Sharing 의 약자로 서버에 미리 허용되어 있는 Origin 만 허용하고 다르면 차단하는 기술이다.

Origin 헤더에 정보를 보고 자신이 허용한 Origin 을 Access-Control-Allow-Origin 에 담아 내보낸다. 브라우저는 이것을 보고 허용할지 차단할지 결정한다.

## Origin 헤더란?
요청을 보낸 페이지의 출처 (Schema + host + port ) 를 말한다.
즉 클라이언트가 배포된 URL 이다. 클라이언트에 접속하면 JS 파일이 api 요청을 보내는데 그때의 출처는 클라이언트가 배포된 URL 이다.


브라우저가 강제하는 기술이고, post 맨에서 바로 서버 url 로 요청보내거나 브라우저에서 바로 서버 url 로 요청보내는것은 페이지에서 js 파일이 요청보내는것이 아니기 때문에 CORS 대상이 아니다.