# Implicit Intent(암시적)

<br>

* 호출할 대상이 명확하지 않을때 사용
* intent의 의도에 맞는 activity를 찾아서 실행
* action, category, type 등등을 저장

<br>

* * *

<br>

* 안드로이드 개발에서 암시적 인텐트(Implicit Intents)는 명시적 인텐트(Explicit Intents)와 달리 타겟 컴포넌트를 명확하게 지정하지 않는다
* intent 설명에 맞는 적절한 컴포넌트를 시스템이 찾아서 요청을 처리하도록 한다
* 시스템은 모든 설치된 앱의 AndroidManifest.xml 파일에 있는 <intent-filter> 섹션을 암시적 인텐트와 비교하여 이 인텐트를 처리할 수 있는 액티비티를 찾는다
* 암시적 인텐트의 이상적인 예로는 URL 열기가 있다
* 이 요청을 처리할 수 있는 특정 액티비티를 알 필요 없이, 웹 페이지를 보기 위한 인텐트를 선언하면 안드로이드 시스템이 URL을 열 수 있는 적절한 앱을 선택한다