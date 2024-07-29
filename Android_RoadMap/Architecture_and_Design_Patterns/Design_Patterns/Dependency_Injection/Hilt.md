# Hilt - DI

<br> 

* 컴파일 시에 stub 파일을 생성하고 그래프를 구성하기 때문에 빌드 시간도 Koin에 비해 상대적으로 느림
* AnroidX 라이브러리와 호환되며, Android Component별 Scope가 명확함
* Hilt에서는 Android 환경에서 표준적으로 사용이 되는 컴포넌트들을 제공함
* 내부적으로 제공하는 컴포넌트들의 전반적인 라이프 사이클 또한 자동으로 관리해주기 때문에 사용자가 초기 DI환경을 구축하는데 드는 비용을 최소화해줌

* annotation
  * @HiltAndroidApp
    * 의존성을 주입하기 위해서는 Application이 있어야함(초기화 코드가 필요함 -> @HiltAndroidApp)
  * @AndroidEntryPoint
    * 주입할 공간(외부에서 주입하는 것을 여기에 넣는다고 보면 됨)
  * @Module
    * 의존성을 주입하고 있는 Provider가 있는 공간임
  * @InstallIn / @InstallIn(singletonComponent::class)
    * 싱클톤을 할 애들은 여기다가 설치를 해달라고 하는 것임(이렇게 컴포넌트가 만들어져있어 자동으로 연결이 되는 것임)
  * @Singleton
    * 한 번만 생성되게 하는 것임
  * @Provides
    * 여기에 주입을 해야하기 때문에 사용함
  * @Named
    * 스트링이 여러 개일 수도 있다 -> 어떤 타입이 있는지만 확인을 하는데 같은 타입이 여러 개일 수도 있기 때문에 이러한 경우에는 @Named 세팅해줌
  * @HiltViewModel
    * HiltViewModel을 사용할때 위와 같은 어노테이션을 사용한다(액티비티를 사용할 수 있게 위의 어노테이션을 사용)
  * @Inject
    * 이 어노테이션을 써주는데 혼자서는 못쓰기 때문에 앞에 constructor를 붙여줌(생성자에 @Inject(뒤에 constructor)를 붙여줌)
  * @Binds
    * 특정 인터페이스의 구현체를 Hilt가 알 수 있도록 연결해주는 역할을 함
    * 인터페이스와 그 구현체를 연결하여, 의존성 주입을 올바르게 설정하는 데 사용함