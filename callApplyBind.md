

## call/ Apply
call, apply 모두 매개변수를 전달 하는 역할이며 apply는 배열안의 요소를 매게변수로 전달한다.

## bind 
this를 변경해주는 역할.
<pre><code>
const user = {
  name: 'Anne',
  showName: function() {
    console.log(`hello, ${this.name}`);
  },
}

user.showName();

let fn = user.showName();
fn.call(user);
fn.apply(user);

let boundFn = fn.bind(user);

boundFn();
</code></pre>

