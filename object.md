# object와 companion object
## Object
+ Object키워드를 사용하게 되면 클래스를 정의함과 동시에 인스턴스 생성
+ 싱글턴 패턴으로 생성되어 2개 이상의 스레드에서 생성한다면 해당 클래스의 인스턴스는 한 개만 생성됨
+ 개발자가 원하는 시점에 인스턴스를 생성하는 방식이 아니기 때문에 생성자 parameter를 전달할 수도 없어서 생성자를 가질 수 없음
+ 클래스나 인터페이스를 상속할 수 있음
+ 선언되자마자 초기화 되지 않고 처음으로 접근될 때 초기화 됨

+ Object 변수
```kotlin
    val day=object{
       var days=30
       var hours=24
       var minutes=60
       var seconds=60 
    }
```

+ Object 클래스
```kotlin
    object DayObject{
        fun PrintDay(days: Int,months: Int){
            println("~~~")
        }
    }
    fun main(){
        DayObject.PrintDay(20,8)
    }
```

+ object 표현식(무명객체, 익명클래스)
    - singleton이 아님
    - 메소드 내부에 로컬 또는 클래스 멤버로 정의할 수 있음
    - 한번만 사용되고 재사용되지 않을 때

## Companion Objects
+ 클래스 인스턴스 없이 클래스의 내부에 접근하고 싶을 때 선언
+ 클래스 당 한개만 생성할 수 있음
+ companion object의 이름은 생략될 수 있고, 그럴 때는 Companion이란 식별자를 사용할 수 있음
+ 생성자를 가질 수 없음
+ top level에 선언할 수 없음
+ 외부 클래스의 private에도 접근이 가능해서 팩토리 메서드를 만들 때 적합
```kotlin
    class Day{
        companion object Days{
            fun getDays(days: Int){
                println("~~")
            }
        }
    }
```
팩토리 메서드 패턴
+ 객체를 생성하기 위해 인터페이스나 추상클래스를 정의하지만 실제 어떤 클래스의 인스턴스를 생성할지 결정하는 것은 서브 클래스에 맡기는 패턴
+ 클래스간의 결합도를 낮추기 위해 사용 됨

```kotlin
    class Car private constructor(val oil:String){
        companion object{
            fun createCar(oil:String)=Car(oil)
        }
    }
    fun main(){
        val myCar = Car.createCar("oilName")
        // Car는 private constructor를 가져서 외부에서 생성할 수 없지만 companion object는 외부클래스의 private property에 접근이 가능
    }
```
