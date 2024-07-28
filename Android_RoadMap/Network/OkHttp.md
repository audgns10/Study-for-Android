# OkHttp - Network

<br>

* 내부적으로 Okio로 빌드된 JVM 및 안드로이드용 HTTP 클라이언트로 안드로이드 java/koltin 멀티플랫폼용 최신 I/O 라이브러리임
* 빠르게 작동을 하며 HTTP 클라이언트를 빠르게 셋업을 하는데에 있어서 장점이 있음
* 자체 복구 시스템이 있어 연결성 문제와 같이 네트워크에 문제가 발생했을 때 수동으로 처리할 필요가 없음
* 해당 라이브러리는 최신 TLS 기능, Anroid용 보안지원, 캐싱 및 인터셉터를 제공함
* OkHttp에서 가장 유능한 기능 중 하나는 호출 로그를 기록, 모니터링, 수정, 재작성 및 재시도할 수 있는 강력한 메커니즘인 interceptors임
* Bearer Authentication와 같은 액세스 토큰, 리프레쉬 토큰을 헤더에 추가하거나 요청 본문에 gizp 압축을 추가하는 등 필요에 따라 모든 네트워크 요청을 처리할 수 있음

<br>

* 본인은 NetworkModule, AuthInterceptor 부분에서 사용중임ㅇㅇ