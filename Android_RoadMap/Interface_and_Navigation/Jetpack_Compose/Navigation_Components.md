# Jetpack Compose Navigiation Components

<br>

* NavController : 앱 화면 간 이동
* NavGraph : 이동할 컴포저블 대상을 매핑 담당
* NavHost : NavGraph의 현재 대상을 표시하는 컨테이너 역할을 하는 컴포저블

<br>

* * *

<br>

1. NavController
    * stateful하며 앱의 화면과 각 화면 상태를 구성하는 컴포저블의 backstack을 추적한다
    * compose 환경에서 NavController는 rememberNavController를 통해서 가져올 수 있다
      * rememberNavController를 사용하면서 주의를 해야할 점은 상태호스팅이다 -> composable 계층 구조에서 NavController를 만드는 위치는 이를 참조해야 하는 모든 컴포저블이 access를 할 수 있는 위치이여야 한다.
    
2. NavGraph
    * NavGraph는 ID로 가져올 수 있는 NavDestination 노드의 집합이다
    * NavGraph 자체는 backstack에 나타나지 않지만 NavGraph로 이동을 하게 되면 시작 대상이 backstack에 추가가 된다
    * 새로운 NavGraph는 대상을 추가하고 시작 경로을 설정할 때까지 유효하지 않다
    * 대상을 추가하는 방법은 NavGraphBuilder.composable() 함수를 이용해서 작업을 하면 된다
   
3. NavHost
    * 자체 포함된 탐색이 발생할 수 있도록 Composable 계층 구조에 제공한다
    * 각 NavController와 NavHost Composable을 연결해야한다
    * NavHost는 내부적으로 구성 가능한 대상을 지정하는 NavGraph와 NavController를 연결한다
    * navController : NavHostController 클래스의 인스턴스이다 -> navigate() 메서드를 호출하여 다른 대상으로 이동하는 등의 방식으로 화면 간에 이동하는 데 이 객체를 사용할 수 있다
    * startDestination : 앱에서 NavHost를 처음 표시할 때 기본적으로 표시되는 대상을 정의하는 문자열 경로이다.
    * builder : NavGraphBuilder로 그래프를 생성하기 위해 사용되는 빌더이다 -> 여기에 NavGraphBuilder의 composable() 함수를 이용하여 경로 대상을 정의 할 수 있다