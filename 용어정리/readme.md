# 용어정리

## 리팩터링 Refactoring

리팩터링(refactoring)은 소프트웨어 공학에서 
'결과의 변경 없이 코드의 구조를 재조정함'을 뜻한다. 
주로 가독성을 높이고 유지보수를 편하게 한다. 버그를 없애거나 새로운 기능을 추가하는 행위는 아니다.


## Reflow & Repaint
- Reflow : 생성된 DOM 노드의 레이아웃 수치(너비, 높이, 위치 등) 변경 시 영향 받은 모든 노드의(자신, 자식, 부모, 조상(결국 모든 노드) ) 수치를 다시 계산하여(Recalculate), 
렌더 트리를 재생성하는 과정.
- Repaint : Reflow 과정이 끝난 후 재 생성된 렌더 트리를 다시 그리게 되는데 이 과정을 Repaint 라 한다.

#### Reflow 과정이 일어나는 상황

- 노드의 추가 또는 제거시. 
- 요소의 위치 변경 시. 
- 요소의 크기 변경 시.(margin, padding, border, width, height, 등..) 
- 폰트 변경 과(텍스트 내용) 이미지 크기 변경 시.(크기가 다른 이미지로 변경 시) 
- 페이지 초기 랜더링 시.(최초 Layout 과정) 
- 윈도우 리사이징 시.

#### Repaint 과정이 일어나는 상황
- Reflow가 끝나고 나서.
- background-color, visibillty, outline 등의 스타일 변경 시에는 레이아웃 수치가 변경되지 않으므로 Reflow 과정이 생략된 Repaint 과정만 발생.

#### 주의하기
- CSS 하위선택자는 필요한 만큼만 정리하기.
- position:relative 사용 주의.
- cssText 및 클래스를 활용해 Reflow or Repaint 최소화. => 여러번 스타일 변화를 주기보다 한번으로 끝내기.

## 플러그인 vs 라이브러리
- 플러그인은 어떤 특정한 하나의 문제를 해결하기 위한 컴포넌트 ex: 슬라이더, 모달.
- 라이브러리는 비슷한 성격을 가진 플러그인의 집합.

## 프레임워크 vs 라이브러리
- 흐름에 대한 제어 권한이 어디에 있느냐에 대한 차이가 있다.
- 프레임워크는 전체적인 흐름에 대한 권한을 가지고 있고, 라이브러리는 사용자가 흐름에 대한 권한을 제어 하면서 필요한 상황을 가져다 사용한다.

## 객체지향
좀 더 나은 프로그램을 만들기 위한 프로그래밍 패러다임으로,
로직을 상태(state)와 행위(behave)로 이루어진 객체로 만드는 것이라고 할 수 있다.
## 캡슐화 
외부에서 함부로 변수의 값을 마음대로 바꿀 수 없도록 내부의 정보를 외부로부터 은폐하는 것을 캡슐화라고 한다.
## 추상화
객체를 만들 때에는 복잡한 원리나 구동방식을 추상화 시켜주는 작업이 필요하다. 복잡함 속에서 필요한 관점만을 추출하는 행위를 추상화라고 한다.
### 데이터 추상화의 장점
- 사용자가 낮은 수준의 코드를 작성하지 않도록 도움.
- 코드 중복 방지 및 재사용성 향상.
- 사용자에게 영향을 끼치지 않은 채로 독립적으로 클래스의 내부 구현 변경 가능
- 중요한 세부 정보만 사용자에게 제공하므로 응용 프로그램 또는 프로그램의 보안 향상에 도움

<pre><code>
class ImplementAbstraction {
  // method to set values of internal members
  set(x, y) {
    this.a = x;
    this.b = y;
  }

  display() {
    console.log('a = ' + this.a);
    console.log('b = ' + this.b);
  }
}

const obj = new ImplementAbstraction();
obj.set(10, 20);
obj.display();
// a = 10
// b = 20
</code></pre>
https://developer.mozilla.org/ko/docs/Glossary/Abstraction
## 인스턴스 
인스턴스란 클래스를 복제한 것으로 new 키워드를 입력하여 해당 클래스타입의 새로운 이름의 변수를 입력한다. 

### 예시 
https://im-developer.tistory.com/136

## 호이스팅
스코프 내부 어디서든 변수 선언은 최상위에 선언된 것 처럼 행동

## 클로저
내부함수에서 외부함수의 변수를 호출할 수 있는 범위
<pre>
<code>
  var makeCounter = function() {
      var privateCounter = 0;
      function changeBy(val) {
        privateCounter += val;
      }
      return {
        increment: function() {
          changeBy(1);
        },
        decrement: function() {
          changeBy(-1);
        },
        value: function() {
          return privateCounter;
        }
      }
    };

    var counter1 = makeCounter();
    var counter2 = makeCounter();
    alert(counter1.value()); /* 0 */
    counter1.increment();
    counter1.increment();
    alert(counter1.value()); /* 2 */
    counter1.decrement();
    alert(counter1.value()); /* 1 */
    alert(counter2.value()); /* 0 */
</code>
</pre>
참고 문서 : https://developer.mozilla.org/ko/docs/Web/JavaScript/Closures


