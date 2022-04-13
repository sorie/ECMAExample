## object


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
