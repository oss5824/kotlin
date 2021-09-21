# interface와 abstract class
## 인터페이스
+ 추상화 메소드와 구현 코드를 가지고 있고 state는 저장 불가
+ 클래스나 오브젝트는 한개 이상의 인터페이스를 가질 수 있음
+ 구현 부분이 없게 만들 수 있는 클래스
+ 인터페이스의 객체는 생성할 수 없음
 
```kotlin
    interface BookInterface{
        fun first()
        fun second(){ 
            //body는 선택 
        }
    }
    class BookSub: BookInterface{
        override fun first(){}
    }
```

+ Interface는 property를 가질 수 있지만 추상화 하거나 접근자를 구현해야함
+ val과 var 프로퍼티도 포함할 수 있지만 이 프로퍼티는 인터페이스 내에서 초기화 해줄 수 없음
+ state를 저장할 수 없는 속성을 가져 프로퍼티는 backing fields를 가질 수 없게되므로 interface에 있는 접근자들 또한 property를 참조할 수 없음
+ 인터페이스에서 프로퍼티를 디폴트 구현해주지 않으면 구현하는 클래스에 반드시 구현해야함

+ 같은 메소드에 여러 타입의 구현이 상속되는 경우
```kotlin
    interface First{
        fun foo(){print("First")}
        fun bar() // abstract
    }
    interface Second{
        fun foo(){print("Second")}
        fun bar(){print("SecondB")}
    }
    class A: First{
        override fun bar(){print("FirstA")}
    }
    class B: First,Second{
        override fun foo(){
            super<First>.foo()
            super<Second>.foo()
        }
        override fun bar(){
            super<Second>.bar()
        }
    }
```

## 추상클래스
+ class를 정의할 때와 같지만 class 키워드 앞에 abstract라는 키워드를 써주어야 함
+ 클래스 내에 추상 메소드, 일반 메소드가 들어갈 수 있음
+ 추상 프로퍼티가 하나라도 있다면 해당 클래스는 추상 클래스가 되어야 함
+ 추상 메소드는 블록으로 이루어진 구현부인 {} 를 가질 수 없고 초기화 역시 마찬가지임
+ 인터페이스와 마찬가지로 객체 생성을 할 수 없음

```kotlin
    abstract class Book{
        abstract fun read()
        open fun what():String{
            return "Book"
        }
        abstract val line: Int
        abstract var readLine: Int
        val isRead = false
    }
```
