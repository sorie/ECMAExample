
## TDZ
* Temporal Dead Zone(TDZ)
* TDZ은 let, const, class 구문의 유효성을 관리한다.
* TDZ 시맨틱은 선언 전에 변수에 접근하는 것을 금지한다. TDZ는 징계를 내린다: 변수 선언 전에 어떤 것도 사용하지 않는다.

** let, const, class는 블록 기반이고 var, function 은 함수 기반이다.

`원문 : https://dmitripavlutin.com/javascript-variables-and-temporal-dead-zone/`<br/>
`한글문서 : https://ui.toast.com/weekly-pick/ko_20191014`


<center><img src="https://user-images.githubusercontent.com/12015609/138012931-0398e0bb-db7c-466b-9135-5a7402a93b79.png" width="500" height="500"></center>

### constructor() 내부의 super()
부모 클래스를 상속받았다면, 생성자 안에서 super()를 호출하기 전까지 this 바인딩은 TDZ에 있다.
<pre><code>
class MuscleCar extends Car {
  constructor(color, power) {
    this.power = power;
    super(color);
  }
}

// Does not work!
const myCar = new MuscleCar(‘blue’, ‘300HP’); // `ReferenceError`
</code></pre>
이 코드를 보면 constructor() 안에서 super()가 호출되기 전까지 this를 사용할 수 없다.
TDZ는 인스턴스를 초기화하기 위해 부모 클래스의 생성자를 호출할 것을 제안한다. 
부모 클래스의 생성자를 호출하고 인스턴스가 준비되면 자식 클래스에서 this 값을 변경할 수 있다.

### var, function, import 구문
위에서 설명한 것들과 반대로 var, function 선언은 TDZ에 영향을 받지 않는다. 이것들은 현재 스코프에서 호이스팅 된다.
var 변수는 선언하기 전에 접근하면, undefined를 얻게 된다.

<pre><code>
// Works, but don't do this!
value; // => undefined
var value;
</pre></code>

그러나 함수는 선언된 위치와 상관없이 동일하게 호출된다.

<pre><code>
// Works!
greet('World'); // => 'Hello, World!'
function greet(who) {
  return `Hello, ${who}!`;
}

// Works!
greet('Earth'); // => 'Hello, Earth!'
</pre></code>
당신은 함수 구현보다 호출에 더 관심이 있기 때문에 종종 함수 선언 전에 호출하게 된다. 
함수 선언 전에 호출해도 에러가 발생하지 않는 이유는 호이스팅 때문이다.
흥미로운 점으로 import 모듈 역시 호이스팅 된다.
import 구문이 호이스팅 되기 때문에, 자바스크립트 파일 시작 부분에서 디펜던시 모듈을 가져오는 것이 좋다.

### 결론
TDZ는 const, let, class 구문의 유효성에 영향을 미치는 중요한 개념이다. TDZ는 선언 전에 변수를 사용하는 것을 허용하지 않는다.
반대로 var 변수는 선언 전에도 사용할 수 있기 때문에 var 사용은 피하는 것이 좋다.

