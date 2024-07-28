# Android - Network

<br>

* 네트워크 통신은 모든 최근 애플리케이션에서 필수적인 영역임
* 자체 네트워크 솔루션을 구축하려면 connection pooling, 응답 캐싱, HTTP와 같은 저수준 기능, 예를들어 인터셉터 및 비동기 호출 지원 등을 직접 구현해야하는 방대한 리소스가 요구됨
* 7~8년 전 Android 개발자들은 HttpURLConnection 또는 Apache의 HttpClient를 사용하여 HTTP 요청을 수행했음
* 하지만 위와 같은 라이브러리들은 많이 양의 보일러 플레이트 코드가 필요하고, 연결기능, 보완 지원 및 DNS 해결책들이 Android 플랫폼과의 호환성을 지원하지 않음