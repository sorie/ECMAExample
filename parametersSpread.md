
## 인수전달
- arguments : 나머지 매개 변수

<pre><code>
function showName(name){
  console.log(name);
  console.log(arguments.length);
  console.log(arguments[0]);
  console.log(arguments[1]);
}

showName('Mike');
showName('Mike', 'Tom');

showName();

</code></pre>

## 나머지 매개변수(Rest parameters)
<pre><code>
function showName(...names){
  console.log(names);
}

showName(); // []
showName('Anne'); // ['Anne']
shwoName('Anne','Isac'); // ['Anne', 'Isac']
</code></pre>

## 배열 전개구문(Spread syntax)
<pre><code>
function User(name, age, ...skills) {
  this.name = name;
  this.age = age;
  this.skills = skills;
}

const user1 = new User("Anne", 33, "html", "css");
const user2 = new User("Isac", 26, "JS", "React");
const user3 = new User("Rue", 20, "Android");

console.log(user1);
console.log(user2);
console.log(user3);

let arr1 = [1, 2, 3];
let arr2 = [4, 5, 6];

let result1 = [...arr1, ...arr2];
let result2 = [0, ...arr1, ...arr2, 7,8,9];

console.log(result1);
console.log(result2);
</code></pre>

## 객체 전개구문(Spread syntax)
<pre><code>
let arr = [1, 2, 3];
let arr2 = [...arr];

let user = {name: 'Anne', age: 33};
let user2 = {...user};

user2.name = "Isac";

console.log(user.name);
console.log(user2.name);
</code></pre>

<pre><code>
//arr1 을 [4,5,6,1,2,3]
let arr1 = [1,2,3];
let arr2 = [4,5,6];
<!-- 
arr2.reverse().forEach((num) => {
  arr1.unshift(num);
}); -->

arr1 = [...arr2, ...arr1];

console.log(arr1);
</code></pre>

<pre><code>
let user = { name: "Anne" };
let info = { age: 30 };
let fe = ["JS", "React"];
let lang = ["Korean", "English"];

<!-- user = Object.assign({}, user, info, {
  skills: [],
}); -->

<!-- user.skill = [...fe, ...lang]; -->
<!-- fe.forEach(item => {
  user.skills.push(item);
});
lang.forEach(item => {
  user.skills.push(item);
}); -->
 
user = {
  ...user, 
  ...info,
  skills: [...fe, ...lang];
};
console.log(user);
</code></pre>


 
