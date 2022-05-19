## 파생 클래스를 사용한 상속
ECMAScript 6 이전에는 사용자 정의 타입으로 상속을 구현할때 대규모 과정이 필요했습니다. 적절한 상속에는 여러 단계가 필요했습니다. 예를 들어 다음 예제를 살펴보겠습니다.

<pre><code>
function Rectangle(length, width) {
    this.length = length;
    this.width = width;
}
Rectangle.prototype.getArea = function() {
    return this.length * this.width;
};
function Square(length) {
    Rectangle.call(this, length, length);
}
Square.prototype = Object.create(Rectangle.prototype, {
    constructor: {
        value:Square,
        enumerable: true,
        writable: true,
        configurable: true
    }
});
var square = new Square(3);
console.log(square.getArea());              // 9
console.log(square instanceof Square);      // true
console.log(square instanceof Rectangle);   // true
</code></pre>

Square는 Rectangle을 상속받습니다. 그래서 Square.prototype을 Rectangle.prototype에서 생성한 새로운 객체로 덮어 쓰고Rectangle.call() 메서드를 호출해야합니다. 이 단계들은 종종 JavaScript 신참을 혼란스럽게 만들거나 경험 많은 개발자에게 오류의 원인이 되었습니다.

클래스는 익숙한 extends 키워드를 사용하여 클래스가 상속해야하는 함수를 지정함으로써 상속을 보다 쉽게 구현할 수 있도록합니다. 프로토 타입은 자동으로 조정되며 super() 메서드를 호출하여 기본 클래스 생성자에 액세스할 수 있습니다. 다음은 앞의 예제와 동일한 ECMAScript 6 코드입니다.

<pre><code>
class Rectangle {
    constructor(length, width) {
        this.length = length;
        this.width = width;
    }
    getArea() {
        return this.length * this.width;
    }
}
class Square extends Rectangle {
    constructor(length) {
        // Rectangle.call(this, length, length)와 같습니다.
        super(length, length);
    }
}
var square = new Square(3);
console.log(square.getArea());              // 9
console.log(square instanceof Square);      // true
console.log(square instanceof Rectangle);   // true
</code></pre>

이번에 Square 클래스는 extends 키워드를 사용하여 Rectangle에서 상속받습니다. Square 생성자는 super()를 사용하여 지정된 파라미터로 Rectangle 생성자를 호출합니다. 
ECMAScript 5 버전의 코드와 달리 식별자 Rectangle은 클래스 선언 (extends이후)에서만 사용됩니다.

다른 클래스로부터 상속받은 클래스를 파생 클래스(derived classes)라고합니다. 파생 클래스는 생성자를 지정하는 경우 super()를 사용해야합니다. 그렇지 않으면 오류가 발생합니다. 
생성자를 사용하지 않기로 결정한 경우 클래스의 새 인스턴스를 만들 때 super()가 모든 파라미터와 함께 자동으로 호출됩니다. 예를 들어, 다음 두 클래스는 동일합니다.

<pre><code>
class Square extends Rectangle {
    // 생성자가 없습니다.
}
// 위 클래스는 아래와 동일합니다.
class Square extends Rectangle {
    constructor(...args) {
        super(...args);
    }
}
</code></pre>

이 예제의 두 번째 클래스는 모든 파생 클래스에 대한 기본 생성자와 동일합니다. 모든 파라미터는 순서대로 기본 클래스 생성자에 전달됩니다. 이전에 정의한 예제에서 Square 
클래스의 생성자는 하나의 파라미터만 필요하기 때문에 super(...args)는 올바르지 않으므로 수동으로 생성자를 정의하는 것이 좋습니다.

super()를 사용할 때 유의해야할 몇 가지 사항이 있습니다.

파생 클래스에서만 super()를 사용할 수 있습니다. 비 파생 클래스 (extends를 사용하지 않는 클래스) 또는 함수에서 사용하려고
하면 오류가 발생합니다.

생성자에서 this에 접근하기 전에 super()를 호출해야합니다. super()는 this를 초기화할 책임이 있기 때문에 super()를 호출하기 전에 this에 접근하려고 하면 에러가 발생합니다.

super()를 호출하지 않는 유일한 방법은 클래스 생성자에서 객체를 반환하는 것입니다.


출처 : https://infoscis.github.io/2018/02/13/ecmascript-6-introducing-javascript-classes/
