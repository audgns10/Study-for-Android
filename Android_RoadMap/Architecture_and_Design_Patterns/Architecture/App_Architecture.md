# App Architecture

<br>

* 안드로이드 개발에서 앱 아키텍처는 앱 확장, 테스트 및 유지보수를 하는 방향에 큰 영향을 줌
* Google은 Android Jetpack에 정의된 앱 아키텍처를 달성하기 위해 다양한 라이브러리들을 지원함

<br>

* UI Layer
  * 책임의 화면에 애플리케이션의 데이터를 랜더링 하는 것임
  * 사용자의 상호작용, 네트워크 및 데이터베이스와의 외부 통신으로 인한 애플리케이션의 데이터에 변화가 있을때 UI요소를 업데이트를 해주어야함
  * 해당 레이어에는 ViewModel과 같은 UI 요소와 상태 홀더도 포함이 되기 때문애 Presentation Layer라고도 함
  * lib : ViewBinding, DataBinding, ViewModel, LiveData, LifeCycle ...
* Domain Layer
  * 도메인 계층은 복잡한 비즈니스 로직을 추상화하고 재사용성을 향상시키는 역할을 함
  * 복잡한 애플리케이션 데이터를 UI계층에 적합한 유형의 변환을 하고, 유사한 비즈니스 로직을 단일 기능으로 그룹화를 함
  * **이 계층은 유사한 기능이 많이 포함이 되고 빈번한 데이터 처리가 필요한 프로젝트를 확장하는 데 유용함**
  * **이 레이어의 유무는 앱 아키텍처의 필수가 아닌 선택사항임**
* Data Layer
  * 데이터 계층의 핵심은 CRUD와 같은 비즈니스 로직 실행 결과를 전달하는 것임
  * 이 계층은 DataSource, Repository와 같은 전략으로 책임을 나누어서 설계할 수 있음
  * lib : DataSource, WorkManager, Room ...