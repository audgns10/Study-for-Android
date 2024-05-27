# Observer_Pattern(옵저버 패턴)

<br>

```kt
// 이벤트를 수신 받는 것과 수신을 하는 것을 연결하는 리스너를 만들어준다
interface EventListener {
    fun onEvent(count: Int)
}

// 생성자로 리스너를 받게 된다 / 이벤트 발생 시마다 전달받은 리스너의 메서드를 호출해줄 것이다
class Counter(var listener: EventListener) {
    fun count() {
        for (i in 1 .. 100) {
            if (i % 5 == 0) {
                listener.onEvent(i)
            }
        }
    }
}

// EventListener를 상속받아 onEvent() 메서드를 구현해준다 / 이렇게 한다면 Start()가 호출이 될때 구현한 EventListener의 구현부가 Counter()의 생성자로 전달이 되고, 5의 배수가 발생을 할때마다 print("${count}")가 실행이 되어서 5의 배수가 출력이 된다
class eventPrinter: EventListener {
    override fun onEvent(count: Int) {
        print("${count}")
    }
    
    fun Start() {
        Counter(this).count()
    }
}

// 실행코드
fun main() {
    eventPrinter().Start()
}

// EventPrinter : 이벤트를 수신해서 출력하는, 인터페이스 구현체
// Counter : 숫자를 카운트 하면서 5의 배수가 감지되면 이벤트를 발생시키는 클래스
// EventListener : 위 두 요소를 연결지어줄 옵저버 (리스너)

// 결과 : 5101520..100(5의 배수)
```

<br>

**이벤트를 감시(observer)하여 이벤트가 발생할때마다 미리 정해둔 동장을 실행하게 해주는 것이다**
**다른 객체의 변화 상태를 별도의 함수 호출 없이 즉각적으로 알 수 있기 때문에 이벤트를 자주 처리를 해주어야하는 프로그램이라면 적격이다**

<br>

**둘 사이에 인터페이스를 하나 끼워넣는 방식이다.
A 는 인터페이스를 상속하여 이벤트가 발생할 때마다 실행되게 할 메소드를 구현해둔다.
그리고 B 를 생성할 때 인터페이스 구현체를 전달하여, 이벤트가 발생할 때마다 생성자로 전달받은 A가 구현한 인터페이스 메소드를 호출하면 된다.**