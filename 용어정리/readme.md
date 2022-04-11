## 용어정리

### 리팩터링 Refactoring

리팩터링(refactoring)은 소프트웨어 공학에서 
'결과의 변경 없이 코드의 구조를 재조정함'을 뜻한다. 
주로 가독성을 높이고 유지보수를 편하게 한다. 버그를 없애거나 새로운 기능을 추가하는 행위는 아니다.


### Reflow & Repaint
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


