
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

## __proto__ vs prototype 
생성자함수가 생성하는 객체에 __proto__를 prototype으로 생성한다는 의미 이다.

<pre><code>
<!-- const car = {
  wheels: 4, 
  drive() {
    console.log("drive...");
  }
} -->
const Bmw = function(color) {
  this.color = color;
}

Bmw.prototype.wheels = 4;
Bmw.prototype.drive = function() {
  console.log("drive...");
};
//x5.__proto__ = car;
//z4.__proto__ = car;

const x5 = new Bmw("red");
const z4 = new Bmw("Blue");
</code></pre>

## instanceof, constructor
 생성자함수가 새로운 객체를 만들어질때 인스턴스라 하는데 instanceof로 구별 할 수 있다.
 인스턴스 객체는 constructor가 존재 한다. 

<pre><code>
z4 instanceof Bmw;//true
z4.constructor === Bmw; //true

</code></pre>

- prototype으로 하나씩 프로퍼티를 명시하여야 기존 함수(constructor포함)가 존재한다.

