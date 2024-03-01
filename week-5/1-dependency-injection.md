# #1 Dependency Injection

#### IoC, Inversion of Control

기존에는 클라이언트 구현 객체가 스스로 필요한 서버 구현 객체를 직접 생성, 연결, 실행했다. 이 말은 객체가 애플리케이션의 흐름을 제어하게됨을 말한다.

객체가 흐름을 제어하지 않고 자신이 가진 로직을 실행하는 역할만 하게끔하고, 이외의 역할을 위해 필요한 객체들을 외부에서 관리해 그 의존성을 가져오도록 하는것을 말한다.

애플리케이션의 컨텍스트에 대한 것을 관리하는 주체를 IoC 컨테이너(최근에는 DI Container라고 한다고 함)라 하고, 이 컨테이너에서 관리되는 객체들을 Bean이라 부른다. 스프링 프레임워크는 DI Container를 통해 Bean들의 의존성을 관리한다.



**DI, Dependency Injection**

객체가 그 역할을 하기위해 필요한 객체와 의존관계를 맺게되는데, 요구되는 객체를 IoC 컨테이너로부터 받아오는 것을 말한다.



**Spring AOP (Aspect Oriented Programming)**

다수의 모듈에서 공통적으로 사용하는 기능이 존재할 수 있다. (ex. Logging, Security, …) 이러한 공통 기능을 하나의 관점으로 보고, 이를 분리하여 관리하기 위한 방법을 말한다.



**PSA, Portable Service Abstraction**

스프링에서 제공하는 여러 기술들을 추상화해, 개발자가 쉽게 사용하는 인터페이스를 말한다. 가장 널리 알려진 예로, 스프링에서 데이터베이스 활용 기술로는 JDBC, JPA 등 여러 기술이 있는데, 어떤 기술을 사용하더라도 일관된 방식으로 활용가능한 인터페이스를 제공한다.



**Spring Bean**

1.  BeanFactory

    스프링 컨테이너의 최상위 인터페이스이며, 스프링 빈을 관리하고 조회하는 역할을 한다.
2.  ApplicationContext

    BeanFactory를 상속받아 그 기능을 모두 제공한다. 또 다른 여러 인터페이스를 상속받아 여러 기능들을 제공한다.

**Bean 조회**

* ac.getBean(Bean name, Type)
* ac.getBean(Type)
* 조회 대상이 없는 경우 예외가 발생한다.
* Type 조회시 같은 타입의 빈이 두개 이상이면 오류가 발생하므로 빈 이름을 지정한다.

**Bean 상속관계 조회**

* 부모 타입을 조회하게 되는 경우 아래 자식타입도 모두 조회한다.
* 모든 자바 객체의 Root object인 Object 를 검색하면 모든 빈을 조회하게 된다.

**BeanDefinition**

ApplicationContext를 구현하는 AnnotationConfigApplicationContext는 AnnotatedBeanDefinitionReader 를 사용해서 AppConfig.class 를 읽고 BeanDefinition 을 생성한다.





