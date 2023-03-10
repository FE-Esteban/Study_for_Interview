# virtual DOM

- DOM을 복사한 가상의 DOM이다.
- 렌더링 이전의 가상 돔과 렌더링 이후에 나타나게 될 가상 돔의 차이점을 집단화 시켜서 실제 DOM에 동기화 시키는 방식이다.
- 주로 react, vue에서 사용하며, 스크린에 직접적으로 실제로 렌더링하는 방식이 아니라 DOM을 직접 업데이트하는 것보다 빠른 장점이 있다.

<br/>

# 🍀 DOM과의 차이점

- 최근 모던 웹들은 SPA를 사용을 한다. SPA는 하나의 html밖에 없는데, DOM의 경우 리소스가 모두 합쳐진 html을 지속적으로 리렌더링을 하게 된다.
- 프로젝트의 규모가 커져서 html의 크기가 커지게 되면 전체의 html을 리렌더링 하는 것 자체가 시간적으로 굉장히 오래걸릴 위험이 있다.
- DOM의 경우 수정된 부분 뿐만 아니라 전체의 DOM를 업데이트 하고, 부모와 자식 노드에 대한 CSS를 다시 계산해서 렌더 트리를 형성한다.
- 렌더 트리를 계속 생성한다는 것은 수정사항이 있을 때마다 계속 렌더링이 발생하고 수정되면서 새롭게 html이 구성이 된다는 것이다.
