
## Array
- JavaScript Array 클래스는 리스트 형태의 고수준 객체인 배열을 생성할 때 사용하는 전역 객체.
- 대괄호로 감싸진 형태로 각각의 index값을 갖는다. 길이를 알기 위해서 length를 사용한다. 
- 배열은 문자 뿐만 아니라, 숫자, 객체, 함수 등도 포함할 수 있다.
- push():배열 끝에 추가, pop(): 배열 끝에 제거, unshift(): 배열 앞에 추가, shift(): 배열 앞에 제거
- 반복을 위해서 사용한다.(index를 이용)

침고 문헌 : https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array <br>
참고 동영상 : https://www.youtube.com/watch?v=KF6t61yuPCY

### for ... of 
- 객체를 순회하는 for...in을 사용할 수 있는데 장점 보다 단점이 많다. index를 얻진 못하지만 for...of를 많이 사용한다. 

#### 배열 예시
<pre>
<code>
let fruits = ['사과', '바나나'];
console.log(fruits.length);
</code>
</pre>

#### fill & map
<pre>
<code>
const getpanes = new Array(2).fill(null).map((_, index) => {
	const id = String(index + 1);
	return { title: `Tab ${id}`, key: id };
});
</code>
</pre>

### shift, unShift, push, pop
- shift : 앞에서 삭제.
- unshift : 앞에서 삽입.
- pop : 뒤에서 삭제.
- push : 뒤에서 삽입.

### arr.splice(n, m) 
- 특정 요소 지움
- arr.splice(n, m, x) : 특정 요소 지우고 추가
- arr.splice() : 삭제된 요소 반환

<pre><code>
let arr = [1,2,3,4,5];
arr.splice(1,3,100,200);
console.log(arr);// [1, 100, 200, 5]

let result = arr.splice(1,2);
console.log(arr); // [1,4,5]
console.log(result); // [2,3]
</code></pre>

### arr.slice(n, m)
- n부터 m까지 반환한다.

### arr.concat(arr2, arr3 ..) 
- 합쳐서 새배열 반환

### arr.forEach(fn) 
- 배열 반복문.

### arr.indexOf / arr.lastIndexOf

### arr.includes() 
- 있으면 true, 없으면 false를 반환한다.

### arr.find(fn) / arr.findIndex(fn)
- 해당하는 값은 반환한다.
- 하나의 요소만 반환한다.

<pre><code>
let userList = [
  { name: 'anne', age: 33 },
  { name: 'leesack', age: 25 },
  { name: 'yu', age: 20 }
];

const result = userList.find((user) => {
  if(user.age < 30) {
    return true;
  }
  return false;
});
console.log(result); //leesack
</code></pre>

### arr.filter(fn)
- 만족하는 모든 요소를 배열로 반환한다.

### arr.reverse() 
- 역순으로 재정렬하여 반환한다.

### arr.map(fn)
- 함수를 받아 특정 기능을 시행하고 새로운 배열을 반환한다.

### arr.join(str)
- 배열값을 str을 사이에 두고 합쳐서 문자로 반환한다.

  


