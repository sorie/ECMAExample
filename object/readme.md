
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


