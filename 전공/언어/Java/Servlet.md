서블릿은 url 에 매핑되어 해당 url 로 요청이 들어왔을때 서블릿 컨테이너에 의해 service() 가 호출되어 적절한 비즈니스 로직을 실행하게 하는 웹 컴포넌트 이다. mvc 에서 컨트롤러와 비슷한 역활을 한다.

![[Pasted image 20260318160530.png]]

# Servlet 동작 방식 (Servletl 컨테이너 안에서 동작 흐름)

HTTP request 가 들어올 시 URL요청과 매핑되어 있는 서블릿을 찾고,  HttpServletRequest, HttpServletResponse 를 생성한다. 그 다음 service() 를 실행시킨다. service() 가 실행되면 그 안에서 http 메서드를 보고 POST 요청이면 doPost(), GET 요청이면 doGet() 등 으로 디스패치 한다. 




# Servlet 생명주기
요청이 들어오면 서블릿 컨테이너가 쓰레드를 하나 생성하고 해당하는 요청에 대한 기존에 생성된 서블릿이 있는지 확인하고 없으면 init() 으로 생성한다. 그다음 서블릿의 service() 를 호출한다. service() 를 호출하고 http 메서드를 보고 doPost(), doGet() 등을 호출한다. 마지막 처리를 다 하고 나면 distory() 를 호출한다. 생성, 삭제시 필요한 작업이 있다면 init(), distory() 를 오버라이딩 하시면 됩니다.


