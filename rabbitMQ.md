메시지 브로커, 전달받은 메시지 전달하는 역할

### AMQP(Advanced Message Queuing Protocol)

`client application` : 카톡 앱
`middleware broker` : 메시지 전달해주는 중간자 서버
`client application` 와 `middleware broker` 사이에 통신을 위한 규약(프로토콜) : AMQP

 즉, 인스턴스가 데이터를 서로 교환할 때 사용하는 방법

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6ca5627d-f85f-4d6d-a8ad-88d23d937e47/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6ca5627d-f85f-4d6d-a8ad-88d23d937e47/Untitled.png)

`Exchange` : Publisher(Producer)로부터 수신한 메시지를 큐에 분배하는 경로의 역할
`Queue` : 메시지를 메모리나 디스크에 저장했다가 Consumer에게 메시지를 전달
`Binding` : Exchange와 Queue의 관계를 정의

- 라우팅은 어떤 네트워크 안에서 통신 데이터를 보낼 최적의 경로를 선택하는 과정

Exchange Type

1. Direct - 1:1 (Exchange에 바인딩 된 Queue 중에서 메시지의 라우팅 키와 매핑되어있는 Queue로 메시지 전달)
2. Fanout - 1:N (메시지의 라우팅 키 무시하고 바인딩된 모든 Queue에 메시지 전달)
3. Topic - Exchange에 바인딩 된 Queue 중에서 메시지의 라우팅 키가 패턴에 맞는 Queue 모두에게 메시지 전달
4. Headers - 라우팅 키 대신 메시지 헤더에 여러 속성들을 더해 속성들이 매칭되는 큐에 메시지 전달
