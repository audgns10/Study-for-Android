# Android Activity Lifecycle

<br>

* 핵심 콜백 메소드
  * onCreate()
  * onStart()
  * onResume()
  * onPause()
  * onStop()
  * onDestroy()
  * 
<br>

* * *

<br>

1. onCreate() -> **tip** : savedInstanceState 파라미터 수신을 하고 이는 activity의 이전 상태가 저장된 Bundle 객체에 해당(처음 생성된 activity는 null을 담고 있음) 이를 통해 이전 상태를 복원해 화면 표시
    * 시스템이 activity를 구성할 때 실행이 되는 메소드(다른 콜백 메소드들과 다르게, 오버라이딩을 하여 구현)
    * activity 전체 수명 주기 동안 딱 한 번만 동작되는 초기화 및 시작 로직 실행 가능(e.g_RecyclerView에 데이터를 바인딩 / button에 View.OnClickListener를 설정하는 동작)
    * setContentView()를 통해 XML 레이아웃 파일을 넘겨줌 -> 해당 레이아웃을 그림(setContentView()는 onCreate()에 종속적인 메소드임 그러므로 반드시 해당 콜백 메소드 안에 구현)

<br>

2. onStart() -> onStart()는 매우 빠른 속도로 실행, 액티비티가 RESUMED 상태에 진입함과 동시에 onResume() 메소드를 호출
    * activity가 onCreate()를 호출한 뒤 activity가 STARTED 상태에 진입하게 되면 onStart()가 호출(이 메소드가 호출되면 activity가 사용자에게 보여지고, 포그라운드 태스크로써 사용자와 상호작용할 수 있도록 준비)

<br>

3. onResume() -> 방해 이벤트가 발생하면, activity는 PAUSED 상태에 들어가게 되어 시스템이 onPause() 콜백 메소드를 호출
    * activity가 RESUMED 상탱에 진입하게 되면 포라그운드에 activity가 표시가 되고 앱이 사용자와 상호작용을 할 수 있는 상태(어떤 방해 이벤트, 인터럽트 등이 발생하여 사용자의 포커스가 없어지지 않는 이상, 앱은 RESUME 상태)
    * 포그라운드에서 사용자에게 activity가 보여지는 동안 실행해야 하는 모든 기능을 활성화 가능

<br>

4. onPause() -> 방해 이벤트, 인터럽트가 발생(전화가 갑자기 오는 경우) / 멀티 윈도우 상 다른 앱에 포커스 / 화면에 반투명 액티비티(권한 요청 다이얼로그)
    * 사용자가 잠시 activity를 떠났을 때 호출되는 콜백 메소드(포그라운드에 있지 않게 되었다는 것)
    * 예외적인 상황으로는 한 화면에 두 앱을 동시에 구동할 수 있는 멀티 윈도우 모드에서는, 멀티 윈도우의 또다른 앱에 포커스를 두어도 해당 activity가 포그라운드에 있으면서 onPause() 호출
    * 계속 실행되어서는 안 되지만 언젠가 다시 시작할 작업을 일시중지하는 작업
    * **onPause()는 아주 잠깐 실행되기 때문에 저장을 해야하는 작업을 실행하기에는 시간이 부족할 수 있다 -> onPause() 내부에서는 사용자 데이터 저장, 네트워크 호출, DB 트랜잭션 등을 실행헤서는 안된다**

<br>

5. onStop() -> 새로 시작된 activity가 화면 전체를 차지할 경우 / activity의 실행이 완료되어 종료될 시점
    * 필요하지 않는 리소르를 해제하거나 조정(e.g_애니메이션을 일시중지, GPS 사용 시 배터리를 아끼기 위해 위치 인식 정확도를 세밀한 위치에서 대략적인 위치로 전환)
    * UI 관련 마무리 작업을 onStop()에서 수행(onPause() -> x)
    * 사용자가 다시 activity로 돌아오게 된다면, STOPPED 상태에서 다시 시작되어 onRestart() -> onStart() -> onResume()이 연달아 호출되며 RESUMED 상태로 변화하여 다시 포그라운드 activity로써의 태스크를 시작, 사용자와 상호작용 시작

<br>

6. onDestroy() -> **import** : 만약 onDestroy()가 호출되기 까지 해제되지 않은 리소스가 있다면, 모두 여기서 해제(Memory Leak 발생 위험 상승)