# box model

모든 HTML 요소는 박스 모양으로 구성됨 <br />
박스모델 속성은 요소를 content, padding, border, margin 4 영역으로 구분한다.

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FYSNJx%2FbtrS9PZ5AED%2Fvo3Hi6RXQUokP7O9kWsKk0%2Fimg.png">

> 출처 : Learn CSS! (https://web.dev/learn/css/box-model/)

위 그림처럼 HTML 요소는 4 영역으로 나뉨

1. content box : 텍스트나 이미지가 들어있는 내용 부분
2. padding : content와 border의 간격
3. border : 테두리 영역
4. margin : border와 이웃하는 요소 사이의 간격

## box-sizing

HTML 요소의 box-sizing 기본값은 `content-box` <br />
width, height의 값을 예측하기 쉽게 `box-sizing: boder-box` 옵션을 줄 수 있다.
