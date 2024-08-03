# Side_Effect - Android

<br>

* SideEffect
  * 이 함수는 성공적인 Recomposition을 마친 후에 Composable 함수가 아닌 표준 함수의 실행을 가능하게 함
  * 하지만 이러한 결과가 Recomposition 전에 발생을 한다고는 보장하지 않음
  * 본질적으로 Recomposition 후에 작업을 트리거하도록 설계가 되어있음
* LaunchedEffect
  * 이 함수는 초기 구성 단계부터 시작을 하여 Composable 함수내에서 suspend 함수를 안전하게 실행할 수 있게 해줌
  * 중요한 점은 LaunchedEffect가 구성에서 제거가 된다면 코루틴 스코프가 자동으로 취소가 된다는 것임
  * LaunchedEffect에 고유한 key 매개변수를 제공하여 실행 흐름을 제어할 수 있음
  * 이 접근 방식을 사용하게 되면 특정 상황이나 상태 변경에 따라 현재 실행을 취소하고 새로운 LaunchedEffect를 실행할 수 있음
* DisposableEffect
  * 이 함수는 Composable 함수가 아닌 표준함수의 실행을 허용하는 동시에 구성에서 벗어날 때 진행 중인 작업을 취소하거나 폐기할 수 있는 기능을 제공함
  * 리소스 누수나 중복 처리와 같은 문제를 효율적으로 방지함