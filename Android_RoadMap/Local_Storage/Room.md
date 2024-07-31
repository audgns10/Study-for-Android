# Room - Local_Storage

<br>

* Room은 복잡한 SQL문을 사용하지 않고, 데이터베이스 쿼리 및 엑세스를 단순화 할 수 있도록 SQLite를 사용하여 추상화 계층을 제공하는 구글을 라이브러리임
* Annotation Processor(KSP(Kotlin Symbol Processing)도 지원)를 기반으로 작동하므로 쿼리 및 열 삽입과 같은 구현은 모두 컴파일 타임에 생성됨
* 이 라이브러리의 장점은 추상화 계층이 매우 간결하고, 이해하기 쉽게 개발자가 CRUD에 대한 기본적인 이해만 바탕이 된다면 SQL 쿼리를 특별히 학습할 필요가 없다는 것이 없음
* Coroutine, RxJava 호환성, 자동 마이그레이션 전략 및 Type converters와 같은 유용한 기능을 제공함