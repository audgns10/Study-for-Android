# Intent_Filters

<br>

* Intent_Filters는 특정 Intent가 어떤 컴포넌트에서 처리될 수 있는지 정의하는 데 사용
* 주로 Implicit_Intent와 관련
* Intent_Filters는 action, category, data를 포함하여 어떤 인텐트를 수신할지 정의
* AndroidManifest.xml 파일에 컴포넌트(activity, service, broadcast receiver)와 함께 정의

<br>

* * *

<br>

* 안드로이드에서 인텐트 필터(Intent Filters)는 액티비티, 서비스, 브로드캐스트 리시버의 기능을 선언하는 데 필수적인 요소
* 인텐트 필터는 앱의 매니페스트 파일에 XML 요소로 정의된 표현식
* 안드로이드는 이러한 필터를 사용하여 들어오는 인텐트에 적합한 컴포넌트를 결정
* 이러한 인텐트는 명시적 인텐트(explicit intent)일 수도 있고 암시적 인텐트(implicit intent)일 수도 있다
* 앱이 인텐트에 응답할 수 있는 능력은 정의한 필터에 포함
* 필터는 액션(action), 카테고리(category), 데이터(data)로 구성된 조건 집합으로, 액티비티나 서비스가 수행할 수 있는 작업을 나타낸다
* 들어오는 인텐트가 정의된 인텐트 필터와 일치하면, 안드로이드 시스템은 해당 인텐트를 컴포넌트(액티비티, 서비스, 또는 브로드캐스트 리시버)로 허용