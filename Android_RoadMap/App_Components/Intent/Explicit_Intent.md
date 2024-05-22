# Explicit Intent(명시적)

<br>

* 의도가 명확할때 사용
  * 호출할 대상이 확실하여, activity가 명확하게 실행이 되어야하는 경우
* Package와 Class명을 정확하게 명시

<br>

* * *

<br>

* Explicit Intent는 주로 애플리케이션의 자체 경계 내에서 사용
* Explicit Intent에서는 Intent에 응답해야 하는 컴포넌트를 지정
* 따라서 setComponent(ComponentName), setClass(Context, Class), 또는 setClassName(String, String)와 같은 메서드를 호출하여 대상 컴포넌트를 지정
* 이는 Explicit Intent가 일반적으로 activity를 실행하거나, 메시지를 방송하거나, 애플리케이션 내에서 서비스를 시작하는 데 사용된다는 것을 의미
* Explicit Intent는 시스템에 의해 해결되지 않고 Intent에서 식별된 컴포넌트로 전달