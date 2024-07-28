# Fragment - Lifecycle

<br>

* Fragment란 Activity 위에서 사용자와 상호작용을 할 수 있는 재사용 가능한 ui를 제공함
* 일반적으로 Fragment는 Activity에 속하고 Fragment Manager에 의해 관리가 됨

<br>

* onCreate()
  * 이 콜백 함수는 onAttached()가 호출이 된 후에 호출, 즉 Fragment가 생성이 되어 FragmentManager에 추가가 되어있음을 알 수 있음
  * 여기서는 Fragment의 Activity가 생성이 되는 동안 호출될 수 있으므로 여기서는 아직 getActivity() 메서드 호출과 같은 Activity 기반 작업을 수행을 하면 안됨
* onCreateView()
  * Fragment의 대부분의 View는 여기서 처리가 됨
  * 이 함수에서 유효한 view 인스턴스를 반환하면 Fragment의 Lifecycle이 형성이 됨
  * Fragment의 생성자에 layout id를 제공해 적절한 시간에 뷰를 자동으로 inflate 할 수 있음
* onViewCreate()
  * onCreateView에서 인스턴스 반환한 후에 호출이 됨
    * onViewCreate()의 inflate된 뷰를 파라미터로 받고, 이는 뷰의 계층 구조와 생명주기가 완전히 초기화가 되었음을 의미함
    * UI 관련 작업을 수행가능
* onStart()
  * 이 함수는 Fragment가 사용자에게 나타낼때 사용됨
  * 일반적으로 Activity.onStart 생명 주기 메서드와 밀접한 관련이 있음 (여러 Activity 또는 애플리케이션 간에 전환하는 경우 두 번 이상 실행될 수 있음)
* onResume()
  * 이 함수는 Fragment가 스크린에 노출이 되어 상호작용을 할 준비가 되어있음을 나타냄
  * 일반적으로 Activity.onResume 생명주기 메서드와 연결이 되어있음
* onPause()
  * 이 함수는 사용자가 Fragment를 떠나갈때 사용이 되지만 여전히 부분적으로 보여질 수 있음을 나타낼때 호출이 됨
  * 예를 들어 멀티 윈도우에 있을 경우이다
  * 이 함수는 일반적으로 Activity.onPause 생명 주기 메서드와 연결이 됨
* onStop()
  * 이 함수는 Fragment가 사용자에게 더 이상 뷰가 표시가 되지 않을때 호출이 됨
  * 일반적으로 Activity.onStop 생명 주기 메서드와 연결이 됨
* onDestroyView()
  * 이 함수는 이전에 생성된 뷰가 Fragment와 분리가 되었을때 호출이 됨
  * 즉, Fragment의 뷰의 상태가 destoryed 상태이며 뷰를 다시 사용할 수 없음
* onDestroy()
  * 이 함수는 Fragment가 삭제되거나 FragmentManager가 파괴가 되었을때 호출이 됨
  * 액티비티에서 분리하기 전에 이 함수에서 남아 있는 모든 리소스를 해제하거나 제거할 수 있음