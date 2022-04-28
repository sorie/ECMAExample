## 객체
- 중괄호로 감싸진 형태로 키/값을 가진다.
- 함수를 가질수 있다.
<pre><code>
const testObj = {
  test1: 'test1',
  testFunc1: function() {return this.test1} ,
  testFunc2() {return this.test1} , //위와 같은 함수이지만 이렇게 표현할 수 있다는 것만 알면 됩니다. (단축)
  testFunc3: () => {return this},
}
//호출 
testObj.test1;//'test1';
//추가
testObj.test2 = 'test4';
//삭제
delete testObj.test2;
//존재유무 확인
test4 in testObj; //false
console.log(testObj.testFunc2())//'test1'
console.log(testObj.testFunc3())//window
</code></pre>

## Object.assign() : 객체 복제
출처 객체들을 복사해 목표 객체에 붙여넣는다. 반환값은 목표 객체이다. <br/>
https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Object/assign
<pre><code>
const user = {
  name : 'anne',
  age : 33
}
const user2 = user;
user2.name = 'Tom';
console.log(user);//{name: 'Tom', age: 33}
console.log(user2);//{name: 'Tom', age: 33}
//값이 둘다 바뀐것을 볼 수 있다. 모두 하나의 객체를 바라보고 있다.
//객체 를 복사하기 위해선 assign을 사용하여야 한다.
</code></pre>
<pre><code>
const user = {
  name: 'Mike'
}
const info1 = {
  age : 30
}
const info2 = {
  gender : 'female'
}

Object.assign(user, info1, info2);
</code></pre>

## Object.keys() : 키 배열 반환 , Object.values() : 값 매열 반환 , Object.entries() : 키/값 배열 반환 , Object.fromEntries() : 키/값 배열을 객체로
<pre><code>
const user = {
  name : 'Mike',
  age : 30,
  gender : 'female',
}

Object.keys(user); //['name', 'age', 'gender']
Object.values(user);//['Mike', 30, 'female']
Object.entries(user);
//[['name','Mike'],['age',30],['gender','male']]

const arr = [
  ['name','mike'],
  ['age', 30],
  ['gender','male']
]
Object.fromEntries(arr) ;
//{name:'Mike',age : 30, gender : 'male'}
</code></pre>

## for...in
for...in문은 상속된 열거 가능한 속성들을 포함하여 객체에서 문자열로 키가 지정된 모든 열거 가능한 속성에 대해 반복. (Symbol로 키가 지정된 속성은 무시.)<br/>
https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/for...in

### object key값에 따른 위치 및 키값 변경
<pre>
<code>
let oldValues = {};
let newValues = {};

const dataset = CHANGE_HISTORY.map(item => {
  let newValue;
  for(let key in item) {
    if(key.startsWith('n_')){
      newValue = {
        [key.replace('n_','o_')]:item[key]
      }
      Object.assign(newValues, newValue);
    } else {
      newValue = {
        [key]:item[key]
      }
      Object.assign(oldValues, newValue);
    }
  }
  return {
    key: `o_${oldValues.o_MALL_ID}`,
    ...oldValues,
    children : [{
      key: `n_${oldValues.o_MALL_ID}`,
      ...newValues
    }]
  }
})
</code>
</pre>

## 생성자 
객체 리터럴를 반복해서 생성하고 싶을때 생성자 함수를 사용하여 여러개의 인스턴스를 생성할 수 있다.

<pre><code>
function User(name, age){
  //this = {};
  this.name = name;
  this.age = age;
  this.sayName = function() {
    console.log(this.name);
  }
  //return this;
}

let user1 = new User('Mike', 30);
let user2 = new User('Jane', 22);
let user3 = new User('Tom', 17);
let user5 = new User('Han', 40);
user5.sayName();//'Han'
</code></pre>

## computed property
- 어느게 키가 될지 모를때에 사용하기 유용하다.
<pre><code>
let a = 'age';
const user = {
  name : 'Mike',
  [a] : 30, //[a]로 호출할 수 있는데 이것을 computed property(계산된 프로퍼티)라고 한다.
  [1 + 4] : 5,
  ['안녕'+'하세요'] : 'hello'
}
function makeObj(key, val) {
  return {
    [key] : val,
  };
}

const obj = makeObj('성별','male');
console.log(obj); 
</code></pre>

## Symbol 
- 유일한 식별자를 만들때 사용한다. (===,==로 확인했을때 같지 않음으로 출력)
- 유일성이 보장된다. 
- 설명을 붙여줄 수 있다. 예 : Symbol('id');
- 하나의 심볼만 보장받을 수 잇음
- 없으면 만들고, 있으면 가져오기 때문
- Symbol함수는 매번 다른 Symbol 값을 생성하지만,
- Symbol.for 메소드는 하나를 생성한 뒤 키를 통해 같은 Symbol을 공유.

<pre><code>
const id = Symbol('id');
const user = {
  name : 'Mike',
  age : 30,
  [id] : 'myid'
}
Object.keys(user); //['name','age']
Object.values(user); //['Mike', 30]
Object.entries(user); // [Array(2),Array(2)]
//Symbor은 값으로 나오지 않는다.
Object.getOwnPropertySymbols(user);//[Symbol(id)]
Reflect.ownKeys(user);// ['name','age',Symbol(id)]
</code></pre>

<pre><code>
//다른 개발자가 만들어 놓은 객체
const user = {
  name: 'anne',
  age: 33
}

//내가 작업
//user.showName = function () {};
const showName = Symbol('show name');
user[showName] = function () {
  console.log(this.name);
}
user[showName]();

//사용자가 접속하면 보는 메세지
for (let key in user) {
  console.log(`His ${key} is ${user[key]}.`);
}
</code></pre>

## 객체 구조 분해
<pre><code>
let user = {name: 'Mike', age: 30};
let {name, age} = user;

console.log(name);
console.log(age);
</code></pre>

