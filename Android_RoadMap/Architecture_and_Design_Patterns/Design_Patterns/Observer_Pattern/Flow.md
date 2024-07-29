# Flow and StateFlow

* 코루틴 기반(flow and stateflow)
	* cold stream이다 즉, collect가 될때까지 실행을 하지 않음

	* stateflow는 clean architecture에서는 livedata 보다는 stateflow를 사용하는 것이 좋다고 함(오직 순수 koltin 라이브러리)
	* hot stream이다 즉, 뭐라고 하지 구독을 하지 않더라도 데이터를 계속 collect한다
	* 생명주기가 파괴가 될 때 까지 데이터를 수집한다. 그래서 뷰가 표시가 안되거나 앱이 백그라운드에 있어도 문제가 되지 않음
	* livedata와 다르게 생명주기가 destroy 될 때 까지 데이터를 수집 그래서 문제점이 있는데 데이터를 계속 수집을 하여서 메모리에 문제를 일으켜서 앱을 다운시켜버리는 일이 생길 수 있는데 그것을 해결하기 위해서는 repeatOnLifeCycle api를 사용해야 한다
	* flow 라이브러리를 사용하고 싶다면 stateflow
	* 안드로이드의 생명주기를 모름(stopped이 되어도 동작)

<br>

* 코루틴은 코틀린의 언어수준에서 지원이 되는 non-blocking 및 비동기 솔루션임
* Flow는 코루틴과 함께 동작을 함
* cold stream임(collect을 해줄때까지 실행을 해주지 않음)
* Flow는 Transform, Flattening, flowOn 연산자와 같은 유용한 연산자를 제공하여 비동기 연산을 보다 쉽게 할 수 있도록 도와줌
* 안드로이드에서 stateFlow나 sharedflow와 같은 것을 활용하여 state를 holding하고 관찰 가능한 flow를 구현하고 여러 구독자에게 값을 보낼 수 있음