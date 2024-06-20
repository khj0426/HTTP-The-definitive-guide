### HTTP 터널링이 어떤 개념인지?

네트워크 접근이 제한된 상황을 가정해보자. 방화벽이 있을 수도 있고, NAT, ACL등이 있는 경우가 있다. 

NAT은 Network Address Translation의 약자로 네트워크 주소 변환을 의미한다. NAT은 보통 사설 네트워크에 속한 여러 호스트를 하나의 공인 IP로 엮기 위해 사용한다.

ACL은 Access Control List의 약자로, 라우터에서 트래픽을 제어하는 규칙을 의미한다.

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FeC8emw%2FbtrC1SEilWD%2FmKcSA3tKw65maeYJm82WEk%2Fimg.png)

이 경우 HTTP 터널링은 두 컴퓨터 간 연결을 설정하는데 사용된다. 보통 터널은 프록시에 의해 만들어진다.

![](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSCByt1C1VaJyXt5VtKQj1PRLRWDDe9M7PL9Q&s)

터널링을 쓰면, 방화벽이나 네트워크 제한을 우회할 수 있고, HTTP 터널은 두 위치간 네트워크 링크를 만든다. 일반적으로 지원하지 않는 네트워크를 통해 다른 프로토콜을 전송할 때 쓴다.

CONNECT메소드가 클라이언트 -> 프록시를 통해 통신하고, https://일때만 사용한다고 가정해보자.(https일떄만!)

클라이언트가 프록시에게 Google과 같은 HTTPS사이트에 대한 TCP연결을 요청하면, 클라이언트가 보내는 모든 데이터는 그대로 프록시를 거치게 된다.

CONNECT는 TLS와 독립적이지만 주로 TLS세션을 여는데 사용한다. 만약 프록시와 연결이 TLS로 암호화되면, 클라이언트-프록시 간 트래픽이 이중으로 암호화된다.

CONNECT메소드는 원시 TCP연결(이 뜻이 뭘까..)를 허용해서, 악의적인 활동에 사용가능하고, 프록시 단에서 이런 보안 조치를 해줘야한다.(CONNECT메소드의 TCP연결을 막는 서버측 정책이 뭐가 있을까!)
