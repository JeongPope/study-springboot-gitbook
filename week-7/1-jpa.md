# WEEK 7

**Jakarta EE**

자바 기술을 사용하여 엔터프라이즈 애플리케이션을 개발하기 위한 플랫폼 및 표준의 집합

* **Servlet API** : 웹앱 개발을 위한 기본적인 API. HTTP 요청/응답을 처리하는 서블릿과 관련된 클래스 및 인터페이스를 제공한다.
* **JSP** : 동적 웹페이지를 생성하기 위한 스크립팅 언어를 제공한다.
* **EJB** : 엔터프라이즈 앱 개발을 위한 서버 컴포넌트 모델을 제공한다.
* **JPA** : 객체-관계 매핑을 지원하는 API로 데이터베이스와의 상호작용을 객체지향 방식으로 처리할 수 있도록 한다.

그외 JMS, JTA, JAX-RS, JAX-WS 같은 요소들이 있다.



**JPA ( Jakarta Persistence API )**

자바 애플리케이션에서 관계형 데이터베이스를 사용할 때 객체와 데이터베이스 간의 매핑을 쉽게 처리할 수 있도록 도와주는 자바 표준 API. JPA는 데이터베이스의 테이블과 자바 객체 사이의 매핑을 설정하고, 데이터베이스에 대한 CRUD(Create, Read, Update, Delete) 작업을 수행하는 방법을 제공한다.

* **Entity** : JPA에서는 데이터베이스의 테이블과 매핑될 자바 객체를 엔티티라고 한다. 엔티티 클래스는 `@Entity` 어노테이션을 사용하여 표시된다.
* **EntityManager** : JPA core interface로, entity의 영속성(persistence)를 담당한다. 데이터베이스와의 상호작용을 처리하고 엔티티의 영속성 상태를 관리한다.
* **Transaction** : Entity의 영속성 상태 변경을 관리하기위해 사용된다. Transaction을 시작하고 commit, rollback 하는데에 사용된다.

JPA는 여러 구현체가 있는데, 가장 널리 사용되는 구현체중 하나가 **Hibernate** 이다.



**Hibernete**

ORM(Object-Relational Mapping) 프레임워크로, 객체와 관계형 데이터베이스 간의 매핑을 간편하게 처리할 수 있다.



**Entity Manager**

JPA에서 영속성 컨텍스트와 엔티티 생명주기를 관리하며, 데이터베이스와의 인터랙션을 담당한다.

* 영속성 컨텍스트 관리 : 엔티티 인스턴스의 상태를 추적하고 관리한다. 엔티티를 컨텍스트에 저장하거나 삭제하고, 변경사항을 동기화한다.
* 생명주기 관리 : 엔티티를 detach, remove, merge 하는 등의 작업을 수행한다
* Transaction 관리 : 트랜잭션 범위 내 엔티티의 영속성 상태 변경을 지원한다.
* JPQL 실행 : JPQL은 객체지향적인 방식으로 데이터베이스에 쿼리를 전달할 수 있는 쿼리언어이다.
* 캐싱 및 성능 최적화 : 쿼리 결과를 캐싱하여 성능을 최적화할 수도 있다.

**Transaction**

데이터베이스에 대한 일련의 작업을 묶어서 원자적으로 처리하는 논리적 작업 단위를 의미한다. 즉, 여러 데이터베이스 조작 작업이 모두 성공하거나 모두 실패해야 하며, 어떠한 작업도 일부만 적용는것을 허용하지 않아야 한다.

* 원자성 : 모든 작업이 성공하면 트랜잭션은 커밋되고, 하나의 작업이라도 실패하면 롤백되어야 한다.
* 일관성 : 트랜잭션 전후에 데이터베이스는 일관된 상태를 유지해야한다. 일부 작업이 실패하더라도 마찬가지
* 격리성 : 동시에 여러 트랜잭션이 실행될 때, 각 트랜잭션은 서로 영향을 주지 않고 독립적으로 실행되는것처럼 보여야 한다. 트랜잭션간의 변경은 서로에게 영향을 주어서는 안된다.
* 지속성 : 트랜잭션이 성공적으로 커밋되고 나면 이 변경사항은 영구적으로 데이터베이스에 저장되어야 한다.

**Embeddable, Embedded**

엔티티 객체 내에 포함될 수 있는 값 타입(Value Type)을 나타내는데, 복합적인 데이터 타입을 표현하고자 할 때 사용된다.&#x20;

주소(Address)나 이름(Name)과 같이 단순한 객체가 아니라 여러 속성으로 구성된 객체를 Embeddable로 표현할 수 있다.

Embedded는 엔티티 객체 내에 객체의 속성으로 포함되며, 해당 객체의 생명주기에 종속적이다.&#x20;

```
@Embeddable
public class Address {
    private String street;
    private String city;
    private String zipCode;
    
    // Constructors, getters, setters, and other methods
}

// Customer entity class에서 Address Embeddable를 사용해 Customer의 address를 포함했다.
@Entity
public class Customer {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    
    @Embedded
    private Address address;
    
    // Other properties, constructors, getters, setters, and methods
}
```

**Aggregate Mapping**

객체 모델링에서의 집합적인 객체들을 데이터베이스에 매핑하는 방법을 의미한다. Aggregate는 여러 객체의 집합을 나타내며, 한 객체가 다른 객체들을 포함하고 있는 개념이다.&#x20;

예를 들어, 주문(Order) 객체는 주문 상품(OrderItem) 객체들의 집합을 포함한다면 Order가 Aggregate Root이 되며, OrderItem은 Aggregate에 속하는 객체이다.



**N + 1 문제**

데이터베이스 쿼리 최적화 관련된 문제 중 하나로, 한 번의 쿼리로 모든 필요한 정보를 가져오는 것이 아니라, 여러 번의 쿼리를 실행하여 동일한 작업을 반복하는 현상

example)

* 게시물(Post)에 대한 정보와 그 게시물의 작성자(User) 정보를 함께 가져오는 경우
  * 게시물에 대한 쿼리를 실행한 후에 작성자에 대한 정보를 가져오는 쿼리를 실행
  * 이런 경우, 게시물이 N개 있을 때, 게시물 쿼리가 N번 실행되고, 그에 따라 작성자 정보를 가져오는 쿼리가 N번 추가로 실행되므로 총 2N개의 쿼리가 실행

**N+1 문제를 해결하기 위한 일반적인 방법**

* Fetch Join
* @EntityGraph

**CascaseType.ALL**

데이터의 일관성을 유지하기 위해 부모 객체의 변경이 자식 객체에 영향을 미치는 방법을 지정하는 옵션. 일반적으로 ORM(Object-Relational Mapping)을 사용하여 객체 간의 관계를 매핑할 때, 부모 객체와 자식 객체 간의 관계를 정의하는데, 이때 "cascadeType.All"을 사용하면, 부모 객체에 대한 어떤 변경이든 자식 객체에도 동일한 변경이 적용됩니다. 주로 부모 객체가 삭제되었을 때 그에 속하는 자식 객체들도 함께 삭제되어야 할 때 사용됩니다.

**orphanRemoval**

부모 객체와 자식 객체 간의 일대다(One-to-Many) 또는 일대일(One-to-One) 관계가 있을 때, "orphanRemoval" 옵션을 true로 설정하면 부모 객체가 자식 객체에 대한 참조를 잃으면 해당 자식 객체를 자동으로 삭제한다. 이 기능은 부모 객체와 자식 객체 간의 관계를 유지하면서 데이터베이스에서 불필요한 데이터를 자동으로 정리하고, 데이터의 일관성을 유지하는 데 도움을 줄 수 있다. 다만 부모 객체가 자식 객체를 삭제할 수 있음을 주의해야한다.



**Event sourcing**

Event Sourcing은 전통적인 관계형 데이터베이스 모델링 패턴과는 다른 데이터 저장 및 변경 방식을 의미다. Event Sourcing은 주로 CQRS(Command Query Responsibility Segregation) 아키텍처 패턴과 함께 사용되며, 데이터 변경 이벤트를 이벤트 스트림으로 저장하고 이를 통해 현재 상태를 재구성하는 방식을 기반으로 한다.



**DAO <--> Repository**

* DAO(Data Access Object)
  * 전통적인 방식으로 데이터 액세스 계층을 구현하는 객체 지향 디자인 패턴
  * 데이터베이스에 액세스하고 데이터를 조작하는 일반적인 인터페이스를 제공
  * 주로 JDBC(Java Database Connectivity)나 Hibernate와 같은 ORM(Object-Relational Mapping) 프레임워크와 함께 사용된다
* Repository
  * 프레임워크에서 제공하는 데이터 액세스 계층을 구현하기 위한 인터페이스
  * Spring Data 프로젝트의 일부로서, 특정 데이터 저장소(예: 데이터베이스)와의 상호작용을 추상화한 일반적인 인터페이스를 제공한다.&#x20;
  * 데이터베이스에 액세스하고 데이터를 CRUD 작업을 수행하며, 이를 통해 애플리케이션의 비즈니스 로직에서 데이터를 관리한다



**JPA Repository <--> DDD Repository**

데이터 액세스를 추상화하고 데이터베이스와의 상호작용을 캡슐화하는 인터페이스를 제공하는 개념이라는 점에서는 공통점을 가진다.

1. 기술적 관점에서의 차이
   * JPA Repository
     * Spring Data JPA와 같은 프레임워크에서 제공하는 인터페이스
     * JPA(Java Persistence API)와 관련된 데이터 액세스 기술에 특화되어 있으며, 주로 JPA 엔티티와 관련된 CRUD(Create, Read, Update, Delete) 작업을 수행
     * Spring Data JPA는 자동으로 쿼리 메서드를 생성하고 페이징 및 정렬을 지원하는 등의 다양한 기능을 제공
   * DDD Repository
     * 도메인 주도 설계의 일부로서, 도메인 모델과 밀접하게 연관된 개념
     * 도메인 객체(Entity 또는 Aggregate)를 저장하고 검색하는 데 필요한 인터페이스를 제공
     * 주로 도메인 객체의 저장소와의 상호작용을 추상화하고, 도메인 객체에 특화된 비즈니스 논리를 캡슐화
2. 관심사 분리
   * JPA Repository
     * 주로 데이터베이스와의 상호작용에 집중한다.&#x20;
     * JPA 엔티티를 기반으로 하여 데이터베이스의 CRUD 작업을 수행하고, JPA 기술을 활용하여 영속성을 관리한다
   * DDD Repository
     * 도메인 객체의 영속성과 관련된 기술적인 책임뿐만 아니라, 도메인 객체 간의 관계와 비즈니스 규칙을 적절하게 처리하는 비즈니스 로직에 대한 책임도 갖는다.&#x20;
     * 도메인 객체의 저장과 검색 뿐만 아니라, 해당 객체와 관련된 비즈니스 로직의 일부를 처리하는 역할을 수행합니다.

