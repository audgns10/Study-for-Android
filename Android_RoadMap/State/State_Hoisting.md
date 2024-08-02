# State_Hoisting - State

* Jetpack Compose의 상태 호이스팅은 상태 호출을 호출자 쪽으로 위임을 하며 Stateful한 Composable 함수를 Stateless한 상태로 변경시키는 방법임
* 기본적으로 상태 호이스팅의 핵심은 일반적으로 remember로 관리가 되는 상태 변수를 Composable 함수의 두 매개변수로 대체하는 것을 포함함
* 이 프로세스는 상태를 유지하는 책임을 Composable 함수에서 호출자로 효과적으로 전환하여 함수를 Stateless한 함수로 만듦

<br>

```kotlin
@Composable
fun HomeScreen() {
    HomeTextField()
}

@Composable
fun HomeTextField() {
    val (value, onValueChanged) = remember { mutableStateOf("") }
    TextField(value = value, onValueChanged = onValueChanged)
}
```

* 위의 코드 예제는 HomeTextField를 remember Composable 함수를 이용해서 상태를 메모리에 저장을 하고 입력 변경사항을 추적하여 상태를 추적하는 것을 알 수 있음
* 이러한 구현은 HomeTextField를 내부적으로 구현을 하고 있으므로 Stateful하다고 볼 수 있다
* 하지만 위 코드에서는 장점이 있음
  * HomeScreen은 HomeTextField를 관리할 필요가 없기 때문에 구현이 간소화 됨
    * 하지만 이는 해당 함수 외부에서 HomeTextField의 동작을 이해하고 제어하는 것이 더 어려워진다는 것을 의미함
* 결과적으로 내부적으로 관리되는 상태로 인해 MyTextField를 다른 컨텍스트에서 재사용하기 어려울 수 있음

<br>

```kotlin
@Composable
fun HomeScreen() {
    val (value, onValueChanged) = remember { mutableStateOf("") }
    HomeTextField(value = value, onValueChanged = onValueChanged)
}

@Composable
fun HomeTextField(
    value: String,
    onValueChanged: (String) -> Unit
) {
    TextField(value = value, onValueChanged = onValueChanged)
}
```

* 위의 예에서는 HomeTextField가 인수를 통해서 값을 받을 수 있도록 구현이 되어있으며 HomeScreen에서는 HomeTextField의 모든 상태를 관리할 수 있음
* 이러한 접근 방식은 처음 보여준 예제 즉, Stateful한 코드와는 다르게 코드가 조금 더 길어질 수는 있지만, 다양한 사례에서는 HomeTextField Composable의 재사용성이 더 확장이 된다는 것을 알 수 있음
* 위와 같은 접근 방식은 상태 호이스팅(State Hoisting)이라고 하며 HomeTextField에서 HomeScreen으로 상태 관리를 승격 또는 호이스팅하는 관행이라고 함
* 즉, 계층 구조에서 상태가 더 높은 위치에서 관리가 되어 보다 유연하고 제어된 상태 관리가 가능함

<br>

```kotlin
@Composable
fun HomeScreen() {
  val (value, onValueChanged) = remember { mutableStateOf("") }
  val processedValue by remember(value) { derivedStateOf { value.filter { !it.isDigit() } } }

  HomeTextField(value = processedValue, onValueChanged = onValueChanged)
}

@Composable
fun HomeTextField(
  value: String,
  onValueChanged: (String) -> Unit
) {
  TextField(value = value, onValueChange = onValueChanged)
}
```

* 위의 예는 Stateless Composable을 활용한 텍스트에서 숫자를 타이핑하게 하면 필터링하여 숫자를 쓴다면 제거면 "" 빈문자열이 되어 abc123을 치면 숫자인 123이 빠지고 abc만 남게 됨
* 위와 같이 HomeTextField를 다양한 방식으로 계속 사용을 할 수 있고, 특정 요구 사항에 맞게 조정을 할 수 있음
* 이러한 유연성은 상태 호이스팅이 다양한 컨텍스트에서 구성 요소의 동작에 대한 외부 제어 및 사용자 정의를 허용하기 때문에 Composable 함수의 재사용성을 향상시키는 이유를 명확히 해야함