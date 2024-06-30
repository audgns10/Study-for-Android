# adsf

* Interview

Clean Architecture
presentation 모듈에서는 ui에 관련된 코드가 쓰여지게 된다
data 모듈에서는 데이터를 관리하고 액세스하는 부분으로, 로컬 데이터베이스나 원격 서		버와의 통신을 담당
domain 모듈에서는 비즈니스 로직이 위치하는 부분으로, 애플리케이션의 핵심 기능과 		업무에 대한 것들을 담당 / 바로 repository를 viewmodel에서 사용을 할 수도 있지만 		invoke를 사용해서 usecase를 구성하고 viewmodel에서 usecase를 사용한다면 파		라미터로 받을 수 있기 때문에 유지보수나 협업에서의 측면에서 긍정적인 효과를 볼 수 있		음
domain은 다른 계층에 의존하지 않음 / presentation -> domain / data -> 			domain


mvvm(mvvm에서 vm이란 -> Viewmodel)
view -> ui
model -> data or 비즈니스 로직
viewmodel -> view에 필요한 data를 model에서 Viewmodel로 가져와서 처리를
하고 이를 view에 넘겨주어 view가 그에 맞게 업데이트를 할 수 있게 해준다

	사용자가 view에서 이벤트를 발생시키고, 사용자의 이벤트의 데이터를 viewmodel에 		데이터를 넘겨준다. 그리고 또 해당 데이터를 model에 넘겨준다. mode과 viewmodel		이 서로 상호작용을 한다. 그리고 viewmodel에서는 livedata(?)을 통해서 옵저빙을 한 	다음, 해당 데이터를 view에 전달을 한다(변경 사항이 있을때 view update)

mvi


Flow(stateflow, dispatcher.IO)
코루틴 기반
cold stream이다 즉, collect가 될때까지 실행을 하지 않음

	stateflow는 clean architecture에서는 livedata 보다는 stateflow를 사용하는 것
	이 더 좋다고 함(오직 순수 koltin 라이브러리)
	hot stream이다 즉, 뭐라고 하지 구독을 하지 않더라도 데이터를 계속 collect한다
	생명주기가 파괴가 될 때 까지 데이터를 수집한다. 그래서 뷰가 표시가 안되거나 앱이 백		그라운드에 있어도 문제가 되지 않음
	livedata와 다르게 생명주기가 destroy 될 때 까지 데이터를 수집
	flow 라이브러리를 사용하고 싶다면 stateflow
	안드로이드의 생명주기를 모름(stopped이 되어도 동작)

	깃허브를 보다가 Dispatcher.IO를 사용한 부분을 보아서 구글링을 해본 결과 통신 부분
	할때는 Dispatcher.IO를 써주는 것이 더 좋다고 해서 사용. 아마 백그라운드에서 처리가	
	된다고 알고 있음

Object
클래스를 정의를 함과 동시에 객체를 생성하는 것이 특징 / 생성자를 가질 수 없음

Coroutine
코루틴 스코프란 코루틴이 실행되는 영역
코루틴은 안드로이드에서 비동기 작업을 쉽게 처리할 수 있게 도와준다
**viewModelScope**는 ViewModel의 생명 주기를 따르는 코루틴 스코프
viewmodel이 파괴가 된다면 viewmodelscope 내의 모든 코루틴이 파괴가 되어서
메모리 누수 같은 걸 방지가능

Suspend fun vs fun
coroutine suspend 함수는 thread 를 block 하지 않는다.
따라서, 하나의 thread 에서 여러 개의 coroutine 을 실행할 수 있다. 특정 작업이 		suspend 되고 resume 될 때까지 이 사이에 다른 작업을 수행할 수 있기 때문

DI(hilt)
클래스 간의 의존성을 외부에서 주입을 한다?

	hilt를 사용한 이유는 처음에 koin이 어노테이션을 사용하지 않고 di를 할 수 있는 라이브
	러리라고 해서 사용을 하려 했는데 koin를 사용한 학교 프로젝트도 없고 참고를 할 수 있
	는 방법이 딱히 생각이 안나서 hilt로 선택을 하였다.

Noting vs Unit
Unit은 함수가 값을 반환하지 않음을 나타냅니다.
Nothing은 함수가 정상적으로 끝나지 않음을 나타냅니다.

멀티 모듈 작업
처음 Clean architecture를 시작할때 멀티모듈을 대부분 사용하는 것을 보기도 하고
유지보수하기 쉽다고 들어서 선책을 하게되었다

Compose state
ui의 상태를 변경하고 업데이트를 하는데 사용
mutablestateof 같은 걸 사용해서 상태를 하나 만들고 remember 함수를 사용해서
상태를 말 그대로 기억을 시켜준다
그리고 아래 뭐 다른 증가하는 코드를 써서 ui에 변화를 주던가 알아서 하는 걸로 앎

Data class
데이터 처리를 위한 클래스?

Dto
데이터를 전달하고 전송을 하는 역할을 하는 걸로 앎(data transfer objcet)

Const val vs val
const val은 컴파일 시점에 값이 할당(프로그램이 실행되기전에 어떤 그런게 일어나는 		그런 느낌)
val은 런타임 시점에 값이 할당(프로그램이 실제로 실행이 되는 시점)

By 키워드
위임?하는 것?

Livedata
생명주기를 가진 activity나 fragement를 관찰 즉, 생명주기에 따라 데이터 전달			(stopped가 된다면 알아서 멈춤)
안드로이드 생명주기와 통합이 중요하다면 livedata 사용

?: 엘비스 연산자
앞에 나오는 값이 null이 아닐 때 앞에 값 출력 null이면 뒤에 값

Viewmodel vs aac viewmodel
mvvm의 viewmodel은 view와 model의 매개체 역할을 하고 view에 보여지는 data		
를 가공한다
aac의 viewmodel의 앱의 LifeCycle을 고려하여 UI 관련 데이터를 저장하고 가공을		한다

Sealed 키워드(sealed class(interface))
실드 클래스는 추상 클래스처럼 계층을 나타낼 수 있으며 하위 클래스는 데이터 클래		스, Object, 일반 클래스, 또 다른 실드 클래스 등 모든 타입의 클래스가 될 수 있습니다.

	interface가 kotlin 버전이 업데이트 되어서 무슨 단점들이 사라져서 써보는 것도 나쁘지 	않다고 해서 사용해봄

mutableStateFlow
stateflow의 값을 변경하거나 변경을 할때 사용하는 것이 mutablestateflow

Compose 리컴포지션
compose로 구성된 ui를 다시 그리는 것?

lateinit vs lazy
lateinit 초기화 이후에 값을 바꿀 수 있음
lazy 초기화 이후에 읽기 전용 값을 사용을 할때