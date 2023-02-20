# z-index

가상의 Z축을 사용한 HTML 요소의 3차원 속성 <br />
속성값이 클수록 높은 우선순위를 가진다. <br />
(음수 값을 사용해서 우선순의를 낮출 수도 있음)

## 부모-자식 z-index 적용 순서

```html
<!-- 1번 div -->
<div class="z-index-2">2</div>

<!-- 2번 div -->
<div class="z-index-1">
  1
  <div class="z-index-10">1.10</div>
</div>
```

위 코드에서 두 요소가 겹치게 되면<br />
`2번 div의 자식 div`가 `1번 div`의 z-index보다 높은 값을 가져도
`1번 div`가 먼저 보이게 됨
