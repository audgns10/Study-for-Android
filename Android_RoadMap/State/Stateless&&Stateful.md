# Stateless And Stateful - State

* Jetpack Compose에서는 성능 최적화를 하기 위한 방법에 따라 Stateless와 Stateful로 설명이 됨

<br>

* Stateful
  * Composable 함수는 remember를 사용할때 Stateful로 간주가 됨
  * 이러한 접근 방식을 이용하게 되면 함수가 객체를 메모리에 저장하게 되어 여러 recomposition에서 상태를 효과적으로 보존할 수 있음
  * remember 함수는 Composable 함수가 반복적으로 호출이 되더라도 상태가 일관되도록 함
* Stateless
  * Composable 함수는 remember를 사용하지 않고 대신 인수를 통해서 상태를 수신할 때 Stateless로 간주가 됨
  * 해당 시나리오에서의 함수는 내부 상태를 유지하지 않고 전달된 데이터에 전적으로 의존을 하므로 특정 시나리오에서 더 예측 가능하고, 재사용이 더 쉬움

<br>

* 컴포즈에서 효율적이고 효과적인 UI 개발하기 위해서는 Stateful 및 Stateless Composables의 차이점을 이해하는 것이 매우 중요한 과제임
* 애플리케이션 내에서 상태를 처리하고, 유지하는 방법에 영향을 미침
* Stateful과 Stateless Composable 함수중에서 선택을 하는 것은 요구 사항에 따라서 달라질 수도 있지만, 일반적으로 Stateless한 Composable 함수는 만드는 것이 좋음
* 이러한 권장 사항의 근거는 재사용성과 유지 관리성에서 비롯이 됨
  * 유지 관리성(Maintainability)
    * Stateful한 Composable는 호출자 입장에서 사용하지 편리해보일 수 있지만, 내부 동작에 대한 이해를 흐리게 만들 수 있음
    * 이러한 투명성 부족으로 인해서 개발자는 Composable이 다양한 시나리오에서 어떻게 작동할지 예측하기 어려워 유지 관리에 어려움을 겪을 수 있음
  * 재사용성(Reusability)
    * 외부 상태 관리에 의존하는 Stateless Composable은 다양한 애플리케이션 부분에서 더 재사용이 가능한 부분이 있음
    * 이는 입력에 따라 예측할 수 있는 순수 함수처럼 작동을 하며, 예기치 않게 동작에 영향을 미칠 수 있는 내부 상태를 유지하지 않음

<br>

* Statless Composable 함수를 선택하면 구성 요소를 다양한 맥락에서 테스트, 유지 관리 및 재사용하기 쉬운 더 깔끔하고, 모듈화된 코드베이스로 이어질 수 있음
* Stateful Composable 함수를 Stateless Composable 함수로 변환을 하는 기술을 상태 호스팅(State Hoisting)이라고 함