# 프로퍼티와 Backing Field
+ 자바에서는 클래스의 필드와 접근자 메서드를 묶어서 프로퍼티라고 칭함
+ 클래스 내의 멤버 변수를 필드, 필드와 게터 세터를 묶어서 프로퍼티라고 부름
+ 코틀린의 프로퍼티는 자동으로 게터와 세터를 구현
+ 정확히는 val의 경우 게터만 var의 경우 게터와 세터 모두 제공
+ 프로퍼티의 접근자 메서드를 선언하는 경우 프로퍼티를 클래스 내부에 선언해야 하므로 default constructor에 선언해준 val이나 var를 제거해주어야 함
  
```kotlin
    class A{
        var count=0
            set(value){
                if(value>=0)filed=value
                // field를 통해서 값에 접근
                // 프로퍼티의 값을 저장하는 field를 코틀린에서 뒷받침하는 필드 즉 Backing Fields라고 함
            }
            get(){
                return field
                //반드시 field를 리턴해야하는 것은 아님
            }
        val isEmpty: Boolean
            get()=this.size==0
    }
```
