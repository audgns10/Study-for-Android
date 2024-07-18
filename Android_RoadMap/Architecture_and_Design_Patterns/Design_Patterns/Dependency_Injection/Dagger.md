# Dagger - DI

<br>

# Dagger의 핵심 요소 5가지

<br>

1. Inject
   * 의존성 주입을 요청 -> Inject 어노테이션으로 요청을 보낼 시에 연결된 Component, Module로 부터 객체를 넘겨줌
2. Component
    * 연결된 Module을 사용하여 의존성 객체를 생성함
    * Injcet로 요청받은 인스턴스로 생성한 객체를 주입함
    * 의존성을 요청하고, 주입을 받는 Dagger의 주된 역할을 수행함
3. Subcomponent
    * Component는 계층관계를 만들 수 있음
    * Subcomponent는 Inner Class 방식의 하위계층 Component임
    * Sub의 Sub도 가능함
    * Subcomponent는 Dagger의 중요한 컨셉인 그래프를 형성함
    * Inject로 주입을 요청받으면 Subcomponent에서 먼저 의존성을 검색하고, 없으면 부모로 올라가면서 검색함
4. Module
    * Module과 연결이 되어 객체를 생성함
    * 그후에 Scope에 따라 관리도 함
5. Scope
    * 생성한 Lifecycle의 범위임
    * Module에서 Scope를 보고 관리를 함