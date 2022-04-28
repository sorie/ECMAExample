
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
