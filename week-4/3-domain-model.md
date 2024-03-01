# #3 Domain Model

Domain Model이란 해당 도메인에서 **비즈니스적인 의미를 가지는** object다.

#### Entity <a href="#entity" id="entity"></a>

* id가 있어 각각의 개체를 고유하게 식별 할 수 있는 경우
* 엄밀히 불변은 아니고 시간이 지나면서 상태가 변경될 수 있는 대상이다.
* ex. Member

#### VO ( value object ) <a href="#vo-value-object" id="vo-value-object"></a>

* id가 없음
* 필드 값 상태가 같다면 같은 객체로 처리해도 되는 경우
  * 그래서 이름이 ‘value’ object임. (반대 되는 개념 : reference object)
  * **참조가 아니라 값으로 동등함을 비교하는게 더 자연스러운 대상들.**
  * 따라서 equals, hashCode 구현 필수
* ex. Money
* 특별히 비즈니스 적인 의미를 가지지 않아도, 데이터 뭉치를 하나로 묶어주는 클래스도 VO로 본다



**Repository**

엔티티에 의해 생성된 **데이터베이스 테이블에 접근하는 메서드들(예: findAll, save 등)을 사용하기 위한 인터페이스**이다.&#x20;

데이터 처리를 위해서는 테이블에 어떤 값을 넣거나 값을 조회하는 등의 CRUD(Create, Read, Update, Delete)가 필요하다. 이 때 이러한 CRUD를 어떻게 처리할지 정의하는 계층이 바로 리포지터리이다.
