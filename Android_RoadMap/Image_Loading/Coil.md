# Coil - Image_Loading

<br>

* Coil은 100% Kotlin으로 제작이 되었음
* 즉, API들이 Kotlin에 친화적임
* 주목할 점은 Coil이 OkHttp, Coroutine과 같은 안드로이드 프로젝트에서 이미 널리 사용이 되는 솔루션들을 사용하기에 다른 대체재 보다는 가벼움
* Coil은 JetPack Compose를 지원함
* Transformations, animated GIF 지원, SVG 지원 및 비디오 프레임 지원과 같은 유용한 기능을 제공함
* Coil의 장점은 크게 4가지로 볼 수 있음
  * 빠름 
    * Coil은 메모리 및 디스크 캐싱, 메모리 내 이미지 다운샘플링, 요청 자동 일시 중지 / 취소등 여러가지 최적화를 제공함
  * 가벼움
    * Coil은 APK에 ~2000개의 메서드를 추가함(이미 OkHttp와 코루틴을 사용하는 앱의 경우) 이는 Picasso와 비슷하고 Gride와 Fresco보다 상당히 적음
  * 사용이 간편함
    * Coil은 Kotlin 기반으로 개발이 되었기 때문에 언어적 특징을 활용하여 간편성, 최소한의 보일러 플레이트를 구현함
  * 최신임
    * Coil은 Kotlin을 기반으로 하며 Coroutines, OkHttp, Okio, AndroidX Lifecycles를 포함한 최신 라이브러리를 사용함