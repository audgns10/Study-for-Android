# App Shortcuts(앱 바로가기)

<br>

**구글 안드로이드에서는 App Shortcuts, 즉, 앱 바로가기를 지원하고 있다**

<br>

* Static Shortcuts -> 정적인 것 / APK나 App Bundle로 패키징된 리소스 파일에 정의 / 앱 실행 중에 변경하거나 변경 불가능
* Dynamic Shortcuts -> 동적인 것 / 런타입 앱에서 만들거나 엡데이트하고 삭제할 수 있다
* Pinned Shortcuts -> 런처에 바로가기 아이콘을 꺼내놓은 Shortcuts / 사용자가 권한을 허락하면 추가 가능 / 

<br>

* 이메일 앱에서 새 이메일을 작성하기
* 메신저 앱에서 사용자의 친구나 다른 사용자에게 메세지 보내기
* 넷플릭스와 같은 앱에서 다음 동영상으로 바로가는 화살표를 클릭
* 게임 앱에서 마지막 저장 지점 불러오기

<br>

* 앱 바로가기의 타입의 위처럼 3가지가 존재한다
* Shortcuts 한 개는 하나 이상의 Intent를 참조한다(각 Intent는 사용자가 Shortcuts을 실행하였을때 앱에서 특정 작업을 실행한다)
* Shortcuts의 사용여부는 프로젝트의 주요 사용 케이스를 보고 사용여부를 결정하면 된다
* 참고로 Shortcuts은 Static과 Dynamic을 포함해서 한번에 5개를 지원한다