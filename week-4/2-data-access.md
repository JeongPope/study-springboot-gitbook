# #2 Data Access

DAO는 말 그대로 실제 DB에 접근하는 객체를 뜻한다. DAO는 Service와 실제 데이터베이스를 연결하는 역할을 하게 된다. 즉, DB에서 데이터를 꺼내오거나 넣는 역할을 DAO가 담당한다.&#x20;

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

DAO는 인터페이스와 DataSource(데이터소스)와 연결하여 처리되는 부분을 분리시켜 데이터베이스가 변경(다른 데이터베이스로 변경, 테이블 변경, 칼럼 변경) 되거나 처리 방식이 변경(쿼리 변경) 되더라도 인터페이스는 변경되지 않기 때문에 비즈니스 로직에는 영향을 주지 않는다.
