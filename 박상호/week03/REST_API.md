# REST API

- HTTP URI를 통해 자원을 명시하고, HTTP Method를 통해 해당 자원에 대한 CRUD를 적용하는 것이다.
- REST의 원리를 따르는 API를 의미

## CRUD

- CRUD는 대부분의 컴퓨터 소프트웨어가 가지는 기본적인 데이터 처리 기능인 Create(생성), Read(읽기), Update(갱신), Delete(삭제)를 묶어서 일컫는 말.
  - Create : 데이터 생성(POST)
  - Read : 데이터 조회(GET)
  - Update : 데이터 수정(PUT, PATCH)
  - Delete : 데이터 삭제(DELETE)

## REST 구성 요소

- 자원(Resource) : HTTP URI
- 자원에 대한 행위(Verb) : HTTP Method
- 자원에 대한 행위의 내용(Representations) : HTTP Message Pay Load

## REST의 특징

- Server-Client(서버-클라이언트 구조)
- Stateless(무상태)
- Cacheeable(캐시 처리 가능)
- Layered System(계층화)
- Uniform Interface(인터페이스 일관성)

## REST의 장단점

### 장점

- HTTP 프로토콜의 인프라를 그대로 사용하기 때문에 REST API 사용을 위한 별도의 인프라를 구축할 필요가 없다.
- HTTP 프로토콜의 표준을 최대한 활용하여 여러 추가적인 장점을 함께 가져갈 수 있게 해준다.
- HTTP 표준 프로토콜에 따르는 모든 플랫폼에서 사용이 가능하다.
- Hypermedia API의 기본을 충실히 지키면서 범용성을 보장한다.
- REST API 메시지가 의도하는 바를 명확하게 나타내므로 의도하는 바를 쉽게 파악할 수 있다.
- 여러 가지 서비스 디자인에서 생길 수 있는 문제를 최소화한다.
- 서버와 클라이언트의 역할을 명확하게 분리한다.

### 단점

- 표준이 자체가 존재하지 않아 정의가 필요하다.
- HTTP Method 형태가 제한적이다.
- 브라우저를 통해 테스트할 일이 많은 서비스라면 쉽게 고칠 수 있는 URL보다 Header 정보의 값을 처리해야 하므로 전문성이 요구된다.
- 구형 브라우저에서 호환이 되지 않아 지원해주지 못하는 동작이 많다.

## REST API 설계

- URI는 동사보다는 명사를, 대문자보다는 소문자를 사용해야함.

```
http://hopak.com/Running/ (X)
http://hopak.com/run/ (O)
```

- 마지막에 슬래시를 포함하지 않는다.

```
http://hopak.com/run/ (X)
http://hopak.com/run (O)
```

- 언더바 대신 하이폰을 사용

```
http://hopak.com/run_away (X)
http://hopak.com/run-away (O)
```

- 파일확장자는 URI에 포함하지 않는다.

```
http://hopak.com/run.jpg (X)
http://hopak.com/run (O)
```

- 행위를 포함하지 않는다.

```
http://hopak.com/delete-run_away/1 (X)
http://hopak.com/run-away/1 (O)
```

## RESTful API

- RESTful이란 REST의 원리를 따르는 시스템을 의미. 하지만 REST를 사용했다 하여 모두 RESTful한 것은 아니다.
- REST API의 설계 규칙을 올바르게 지킨 시스템을 RESTful하다 말할 수 있다.
- 모든 CRUD 기능을 POST로 처리하는 API 혹은 URI 규칙을 올바르게 지키지 않은 API는 REST API의 설계 규칙을 올바르게 지키지 못한 시스템은 REST API를 사용하였지만 RESTful 하지 못한 시스템이라고 할 수 있다.

## Reference

- https://khj93.tistory.com/entry/%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-REST-API%EB%9E%80-REST-RESTful%EC%9D%B4%EB%9E%80
