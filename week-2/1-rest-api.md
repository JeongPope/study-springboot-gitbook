# WEEK 2

**API (Application Programming Interface)**

API는 정의 및 프로토콜 집합을 사용하여 두 소프트웨어 구성 요소가 서로 통신할 수 있게 하는 메커니즘으로, 요청과 응답을 사용하여 두 애플리케이션이 서로 통신하는 방법을 정의한다. API 문서에는 개발자가 이러한 요청과 응답을 구성하는 방법에 대한 정보가 들어 있다.



**정보의은닉(Information Hiding)과 캡슐화(Encapsulation)**

캡슐화란 객체의 필드, 메소드 등을 감싸 외부로부터 노출되지 않도록하는것을 말한다. 이를 통해 외부에서의 잘못된 접근 또는 의도하지 않은 동작을 방지할 수있다.&#x20;

정보은닉의 기법들은 대표적으로 다음 3가지로 정리해볼 수 있다.

* 업캐스팅 : 객체의 구체적인 타입을 숨긴다.
  * ex. Factory design pattern
* 구현 은닉 : 인터페이스와 추상클래스를 통해 구체체를 노출시키지 않음
  * ex. Private methods
* 캡슐화

위와같이 캡슐화는 정보의 은닉의 기법들 중 하나일 뿐이다.  정보은닉을 하면서 보안의 향상, 다형성, 유연한 객체 변경으로 인한 개발 생산성을 확보할 수 있다.



**Architecture <--> Architecture Style <--> Design pattern**

* Architecture
  * 소프트웨어의 시스템의 기본 구조
* Architecture Style
  * Architecture에서 일반적으로 발생하는 문제점들을 해결하기 위해 자주 사용되고, 이미 검증된 소프트웨어의 아키텍처 패턴
* Design Pattern
  * 소프트웨어를 구성하는 각각의 모듈들의 기능, 범위, 목적 등을 코드 수준에서 디자인 하는 것



**REST**

Representational State Transfer(REST)는 API 작동 방식에 대한 조건을 부과하는 소프트웨어 아키텍처로, REST는 처음에 인터넷과 같은 복잡한 네트워크에서 통신을 관리하기 위한 지침으로 만들어졌다.



**URI (Uniform Resource Identifier)**

리소스를 식별하는 방법으로, Identifier를 활용하여 식별한다.

* URL (Uniform Resource Locator) : 리소스의 위치를 뜻한다. 리소스의 위치 변경에 약하다.
  * `/items` : URL
  * `/items/{id}` : URI
* URN (Uniform Resource Name) : 리소스의 유니크한 이름으로 거의 쓰이지 않는다.



**MIME Type**

Content의 종류를 표현하는것으로 일반적으로 HTTP Header의 Content-Type 속성으로 전달된다.



**CRUD (Create, Read, Update, Delete)**

대부분의 컴퓨터 소프트웨어가 가지는 기본적인 데이터 처리 기능인 Create(생성), Read(읽기), Update(갱신), Delete(삭제)를 묶어서 일컫는 말



**CQS Pattern**

모든 객체의 메소드를 다음 두개로 구분하는 소프트웨어 디자인패턴

* Command : Method 작업을 수행
* Query : 작업 수행 후 데이터를 반환

하나의 method가 command이면서 query일 수 없다.

* 장점 : Write 와 Read를 분리할 수 있고, 간단하게 구현할 수 있으며, 읽기 쉽다
* 단점 : 중복되는 코드가 발생할 확률이 높고, 유지보수하기 어렵다. 간단한 코드를 복잡하게 구현해야할 수도 있다.

