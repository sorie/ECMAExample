
## prototype
<pre><code>
user.name = 'Anne';
user.hasOwnProperty('name');//true
user.hasOwnproperty('age');//false;
//hawOwnproperty()는 proto에 들어있는 함수이다.
</code></pre>

### 상속
- 프로토타입안에 객체를 상속할 수 있고 계속 프로토타입에 상속할 수 있는데 그것을 프로토타입 체인이라 한다.
<pre><code>
const car = {
  wheels: 4,
  drive() {
    console.log('drive...');
  }
};

const bmw = {
  color: 'red',
  navigation: 1, 
};

const ben2 = {
  color: 'black',
};

const audi = {
  color: 'blue',
};

bmw.__proto__ = car;
ben2.__proto__ = car;
audi.__proto__ = car;

console.log(bmw);//자신의 속성이 나옴
console.log(bmw.color);//자신의 속성에서 값을 찾음.
console.log(bmw.wheels);//자신의 속성에서 찾아도 없으면 밑에 __proto__로 들어가 찾음.

</code></pre>
