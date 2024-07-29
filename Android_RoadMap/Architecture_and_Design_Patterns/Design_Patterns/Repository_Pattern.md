# Repository_Pattern(래포지토리 패턴)

* 프레젠테이션 레이어는 로켈 데이터 베이스에서 데이터를 쿼리하고 네트워크에서 원격 데이터를 가져오는 것과 같은 비즈니스 로직에 근접한 인터페이스와 함게 추상화를 사용함
* 실제 구현 클래스는 무거운 작업을 수행하고, 도메인 관련 작업을 수행함
* 도메인과 관련된 실행 가능한 함수 집합체를 개념적으로 캡슐화하고 다른 계층에 보다 객체 지향적인 측면을 제공함
* 모던 안드로이드 개발에서 데이터 계층은 다른 계층에 공개 인터페이스로 노출되고 단일 정보 출처 원칙을 따르는 레포지포리로 구성이 됨
* 다른 레이어들은 kotlin flow, livedata 등과 같은 스크림들로 데이터 관찰 가능함 

<br>

* Repository는 데이터의 출처와 상관없이 동일한 인터페이스로 데이터에 접근할 수 있도록 만들어진것이다
* 이점
  * 도메인과 연관된 모델을 가져오기 위해서 필요한 datasource가 presentation layer에서는 알 필요가없다(필요한 datasource가 몇개든 사용될 data만 가져오면 댐)
    * 따라서 DataSource를 새롭게 추가하는 것도 부담(x)
  * datasource가 변경이 되더라도 다른 계층에는 영향이 없음(캡슐화)
  * 사용자는 Repository 인터페이스에 의존을 하기 때문에 테스트하기에 용이
  * **즉, Repository는 결국 Presentation Layer과 Data Layer간의 Coupling을 느슨하게 해주는 것이다**
* 흐름도
  1. View -> ViewModel로만 데이터를 가져온다.
  2. ViewModel -> Repository로 데이터 접근한다.
  3. Repository -> DataSource(local/remote)로 부터 데이터를 요청한다.