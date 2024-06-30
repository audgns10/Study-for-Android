# LiveData

* 관찰 가능한 data holders class이다
* android 플랫폼에 종속적이다
* 앱 아키텍처에 사용할때 비슷한 패턴을 따른다
* 생명주기를 가능 fragment, activity를 관찰한다
* 관찰자의 생명주기에 따라 데이터를 전달한다
    * 뷰가 Stopped 상태가 된다면 LiveData.observe()는 소비자를 자동으로 등록 취소
* 참고로 android의 생명주기와의 통합이 더 중요하다면 livedata를 선정하는 것이 더 좋다