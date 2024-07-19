# Koin - DI

<br>

* Dagger 보다 러닝 커브가 더 짧아 쉽고 빠르게 DI 적용이 가능함
* Hilt와 같이 별도의 Annotation이 사용이 안되기 때문에 컴파일 시간이 단축이 됨
* 런타임시에 의존성을 주입하기 때문에 알 수 없는 오류를 뱉어내기도 함
* DI 패턴이 아닌 Service Locator Service를 사용하는 Service Locator에 의존하는 안티 패턴임

<br>

* single
  * 통신 객체와 같이 APP 전체 주기 동안 다일 인스턴스로 존재하는 객체를 싱글톤과 같이 생성하여 주입함
* factory
  * single과 반대로 항상 객체를 생성하여 주입함
  * 요청(get, inject)을 할 때마다 새로운 객체를 생성하여 주입함
* viewModel
  * ViewModel에 관한 Module 선언임