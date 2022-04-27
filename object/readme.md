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

## Object.assign()
출처 객체들을 복사해 목표 객체에 붙여넣는다. 반환값은 목표 객체이다. <br/>
https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Object/assign

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


