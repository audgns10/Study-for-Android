# State And Recomposition - State

<br>

* Compose UI의 세가지 주요 단계
  * 구성(Composition)
    * 구성 단계의 이 초기 단계에서는 Composable 함수를 구성에 통합이 되는 과정이 포함이 됨
    * 해당 단계에서는 Composable 함수에 대한 설명과 메모리 내 슬롯이 여러개 생성이 됨
    * 이러한 슬롯은 각 Composable 함수를 기억하는데 사용이 되고, 런타임 중에 효율적으로 사용이 될 수 있음
  * 레이아웃(Layout)
    * 해당 단계에서는 Composable 트리 내에서 각 Composable 노드의 배치가 결정됨
    * 기본적으로 레이아웃 프로세스는 각 Composable 노드를 측정하고 적절하게 배치하여 모든 요소가 UI의 전체 구조에 올바르게 배열되도록 하는 작업에 포함이 됨
  * 그리기(Drawing)
    * 해당 단계에서는 Composable 노드를 일반적으로 장치 화면인 캔버스에 렌더링하는 작업이 포함됨
    * 해당 단계에서는 Composable 함수의 시각적 표현이 생성되어 표시됨
  
<br>

* 위와 같은 세가지 주요 단계를 거쳐 이미 렌더링된 UI에 업데이트를 하는 방법을 궁금해할 수 있음
  * 이를 해결하기 위해 Jetpack Compose는 첫 번째 단계(기술적으로는 구성, Composable 노드가 UI 변경사항을 구성에 알림)부터 시작해서 상태 변경에 대한 응답으로 UI 레이아웃을 업데이트하는 다시 그리기 메커니즘을 도입하게 되는 이를 Recomposition(재구성)이라고 함

<br>

* Recomposition을 트리거 하는 두 가지 방법
  * 입력 변경(Input Changes)
    * 이것은 Composable 함수에서 Recomposition을 트리거 하는 가장 기본적인 방법임
    * Compose 런타임은 equals 함수를 이용해서 인수의 변경 사항을 감지함
    * equals가 false를 반환하는 경우에는 런타임은 이를 입력 데이터의 변경으로 해석을 함
    * 결과적으로 이러한 데이터 변경사항에 따라 UI 표현을 업데이트하기 위해 Recomposition을 함
  * 상태 변경 관찰(Observing State Changes)
    * Jetpack Compose는 런타임 라이브러리에 제공하는 State API를 활용하여 상태 변경 사항을 모니터링 하여 Recomposition을 트리거하는 가장 기본적인 방법임
    * 일반적으로 remember Composable 함수와 함께 사용이 됨
    * 이러한 접근 방식은 메모리에 상태 객체를 보존하고 Recomposition 중에 복원하여 UI가 현제 상태를 반영할 수 있도록 하는데 도움을 줌

<br>

* Compose를 사용할때 알아야할 몇 가지 사항
  * 구성 가능한 함수는 순서와 상관없이 실행이 가능함
  * 구성 가능한 함수는 동시에 실행이 될 수 있음
  * 재구성은 최대한 많은 수의 구성 가능한 함수 및 람다를 건너뜀
  * 재구성은 낙관적이고, 취소가 될 수 있음
  * 구성 가능한 함수는 애니메이션에서의 모든 프레임에서와 같은 빈도로 매우 자주 실행될 수 있음

<br>

* Recomposition은 Jetpack Compose에서 필요한 메커니즘이지만 재구성이(Compose의 단계들이 다시 시작) 되는 만큼 성능적인 비용이 발생함