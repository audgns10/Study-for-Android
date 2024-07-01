# Repository_Pattern(래포지토리 패턴)

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