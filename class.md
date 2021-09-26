# 클래스
## 생성자 및 초기화 블럭
+ 클래스 body에 init블럭은 객체가 생성될 때 실행 됨
  - 기본 생성자가 클래스의 헤드에 들어가기 때문에 어떠한 코드도 포함될 수 없음
  - 그렇기 때문에 이런 역할을 해줄 초기화 블럭이 필요
+ 코틀린의 생성자에는 기본 생성자와 보조 생성자가 있고 기본 생성자는 클래스 선언부에 위치
+ 기본적으로 public접근 네어자를 가지게 되고 이 때는 constructor를 생략하고 클래스 이름 바로 뒤에()를 통해 선언할 수 있음
```kotlin
  class ExClass constructor(example: String){}
  class Ex2Class(example: String){} //생략할 때
  class Ex3Class private constructor(example: String){}//생략 못할 때, public이 아닐때
```

+ 기본 생성자에 var과 val 키워드를 붙이게 되면 property를 선언한 것과 동일한 효과
```kotlin
  class ExClass constructor(example:String){
    val mainExample:String = example
  }
  class Ex2Class(val example: String){}
```

+ var로 선언할 경우 컴파일 시 default로 getter와 setter 메서드가 생기고 val로 선언할 경우 getter 메서드가 자동적으로 생김
```kotlin
  // get, set을 통해 커스터마이징 할 수 있음
  var naem:String
  get()=this.toString()
  set(value){
    setDataFromString(value)
  }
```

+ 보조 생성자는 클래스 body에 constructor를 통해 생성할 수 있음
+ 기본생성자가 있다면 반드시 this()키워드를 통해 기본생성자를 호출해 줘야 함
```kotlin
  class ExClass(example: String){
    constructor(num: Int):this(num.toString()){
      ...
    }
  }
```

## 상속
+ 클래스를 상속받을 때 기본생성자의 파라미터를 포함해서 전달해야하고 없다면 ()를 필수적으로 사용해야 함
+ 부모클래스에서 open 되어있는 요소를 사용할 수 있음
+ 자식이 부모 객체와 동일한 이름을 변수에 사용할 수 없고, 사용하기 위해서는 오버라이딩이 필수
```kotlin
  open class Exam{

    //자식에서 오버라이딩해 재정의 하기위해 open 으로 선언
    open fun exam():String{
      return "Exam"
    }
  }

  class SubExam(): Exam(){
    override fun exam():String{
      return "SubExam"
    }
  }
```

## Any
+ Any 클래스에는 equals(), hasCode(), toString()의 3가지 메서드만 정의
+ 코틀린의 모든 클래스는 명시적으로 특정 클래스를 상속 받지 않으면 Any 객체를 묵시적으로 상속 받음

## Modifier
+ 클래스 내부의 요소들은 private, protected, internal, public의 4가지 접근 제어자를 가질 수 있음
  - private: 클래스 외부에서 접근이 불가
  - protected: 상속관계에 있는 외부에서는 접근 가능
  - internal: 한 모듈안에서 접근 가능
  - public: 어디서든 접근 가능
