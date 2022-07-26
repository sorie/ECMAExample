
1. method

`javascript 에서 method 는 함수로 된 property이다.`


java 같은 class based OOP 언어와 달리 prototype based programming 인 javascript 는 다소 그 의미가 헷갈릴 수 있다.

애초에 내가 생각했던 인스턴스가 실은 인스턴스가 아니고...사실 다 프로토타입 체인으로 연결되어 있고...

그러다보니 오브젝트 단위에서 property 랑 method 를 설명하니 헷갈릴만 하다.

그런데 우리가 일반적으로 프로퍼티를 지칭할 때 method 를 제외한 데이터 프로퍼티를 말하므로...(물론 getter setter 와 관련있는 accessor property 도 있다.)

구분해서 이야기를 하게 된다.

### 의미로 구분
property 는 속성이라면 method 는 행동 이다.

예를 들어 listA 라는 array 가 있을 때, listA.length 는 property 죠? 그렇지만 listA.push(1) 은 method 입다.

### 사용법으로 구분
위에서 javascript method 는 함수로 된 property 라고 언급했다. 함수의 가장 큰 특징! callable(호출할수있는) 하다.

따라서 javascript 에서는 괄호로 함수를 호출하므로 대부분 괄호로 끝나면 method, 없으면 property 라 보아도 무방하다.


