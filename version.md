## Version 정리

버전 번호는 점(dot)으로 구분되며 순서대로 다음과 같은 식의 구조를 가지고 있다.
`Major Version . Minor Version . Build or Maintenance Version`
실제로 버전 번호는 3자리 이상도 사용 하기도 한다.
일단 여기서는 설명을 위해 3자리를 기준으로 이렇게 표현하겠다.

### Release Number . Major Number . Minor Number`
- Release Number: 1로 시작해서 전체를 뒤엎을 정도로 큰 변화가 발생했을 때 이 수치를 올린다. (영화 속편이 나오면 2편 혹은 투(two)이라는 이름을 붙이듯 말이다.)
- Major Number: 0으로 시작해서 주요 기능의 추가나 변경 등 사용상 혹은 컨텐츠의 주요 변화가 발생했을 때 1혹은 무작위로 증가한다. 간혹 알파벳이 붙기도 하는데 예를 들어 Beta(테스트버전)의 경우 b를 숫자 뒤에 붙이는 경향이 있다.
- Minor Number: 0으로 시작해서 버그 수정 등 미미한 변화가 발생하면 1씩 혹은 무작위로 증가한다. 역시 개발사 정책에 따라 특정 알파벳이 붙을 수도 있다.
    
## Sementic Versioning
  그라바타(Gravatars)의 창시자이자 깃헙(GitHub)의 공동창업자인 톰 프레스턴-베르너(Tom Preston-Werner)가 작성했으며, 
오픈소스 프로젝트에 일반적으로 사용된다.버전은 사용자가 이 package (api)가 어떤식으로 변경되었는가를 이해할 수 있게 해준다.
  
- MAJOR Version: 기존 api가 변경 / 삭제 되었기 때문에 update 하면 동작하지 않을 수 있다는 경고의 의미
- MINOR Version: 이전 버전과 호환되는 방식으로 API가 추가되었으니 살펴보라는 의미
- PATCH Version: 이전 버전과 호환되는 버그 수정을 했을 경우

### 특징
- SemVer(유의적버전)을 쓰는 소프트웨어는 반드시 공개 API를 선언한다. 코드자체로 선언하거나, 문서로 엄격하게 명시해야 한다. (책임감 있는 개발자..)
- Normal Version은 반드시 X.Y.Z 형태이며 음수가 아닌 정수여야 하며 절대 앞에 0이 붙으면 안되고 각 수는 증가하는 수여야 한다.
- 배포하면 그 버전의 내용은 절대 변경해서는 안된다. 😱
- 0(0.y.z)은 초기 개발을 위해서 쓴다. 아무 때나 마음대로 바꿀 수 있다.
- 1.0.0 버전은 공개 API를 정의한다. 이후 버전은 배포한 공개 API에서 어떻게 바뀌었는지에 따라 올린다.
- MAJOR Version이 올라가면 MINOR Version과 PATCH Version은 0이 되야하고
- MINOR Version이 올라가면 PATCH Version이 0이 반드시 되어야 한다.
- 정식 배포를 앞둔 pre-release version은 PATCH Version 바로 뒤에 붙임표(-)와 마침표(.)로 구분된 식별자를 더해서 표시할 수 있다. 
  식별자는 반드시 아스키(ASCII) 문자, 숫자, 붙임표로만 구성한다[0-9A-Za-z-]. 
  식별자는 반드시 한 글자 이상으로 한다. 
  숫자 식별자의 경우 절대 앞에 0을 붙인 숫자로 표기하지 않는다. <br>
  예) 1.0.0-alpha, 1.0.0-alpha.1, 1.0.0-0.3.7, 1.0.0-x.7.z.92. <br>
  우선순위는 1.0.0-alpha < 1.0.0.
- Build metadata는 수버전이나 정식배포 전 식별자 뒤에 더하기(+) 기호를 붙인 뒤에 마침표로 구분된 식별자를 덧붙여서 표현할 수 있다.

  ### 참고 문헌
  - https://semver.org/lang/ko 
  - https://semver.org
  - https://velog.io/@slaslaya/Semantic-Versioning-2.0.0-MAJOR-MINOR-PATCH%EC%99%80-%EB%AA%85%EC%84%B8%EC%97%90-%EA%B4%80%ED%95%98%EC%97%AC
  - http://seorenn.blogspot.com/2012/02/version.html





