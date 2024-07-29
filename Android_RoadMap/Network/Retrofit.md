# Retrofit - Network

<br>

* Retrofit은 JVM용 type-safe HTTP 클라이언트임
* OkHttp 위에 추상화 계층을 제공하므로 저수준 구현을 처리하지 않고도 쉽고 간결하게 요청사항을 정의가능함
* 해당 라이브러리에서 재공하는 어노테이션을 활용하여 URL, 헤더 조작, method 및 body를 쉽게 요청이 가능함(원하는 HTTP를 쉽게 빌드가능)
* 플러그인이 가능한 Converter.Factory를 연결하면 보일러 플레이트 코드를 작성할 필요없이 모든 JSON응답을 처리할 수 있음(쉽게 직렬화 가능)
* 원시 응답을 처리하고 응답 유형을 원하는 유형으로 모델링할 수 있는 CallAdapter를 연결하여 네트워크 응답을 조작할 수 있음