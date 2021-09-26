# Scope function
+ 스코프 함수는 코드를 축약해서 표현할 수 있도록 도와주는 함수
+ let, run, with, apply, also 5가지
+ run,let처럼 괄호 없이 일종의 키워드 같이 사용할 수 있으며 lateinit과 함께 Safe call의 남용을 막아줌
+ 컨텍스트 객체 참조 방법, 반환 값, 확장 함수 여부 에 따라서 각각 다르게 사용됨

## 컨텍스트 객체를 참조하는 방법
+ scope function 블럭은 람다 function으로 람다의 파라미터로는 it과 this 두가지를 가지고, 이 키워드를 통해 객체를 이용할 수 있음
+ let과 also가 it을 통해 context object 참조
+ run with apply는 this를 통해 context object를 참조(this는 생략 가능)

## 반환 값 
+ scope function는 context object를 반환하거나 lambda 결과를 반환함
+ apply와 also는 context object를 반환(자기 자신을 반환)
+ let, run, with는 람다 결과를 반환, 즉 scope function block에 있는 마지막 명령어의 결과를 반환

## 확장함수여부
+ 기본적으로 scope function은 확장함수 형식으로 사용
+ with는 확장 함수형식이 아닌 context object를 파라미터로 받는 함수형식으로 사용 가능

## 사용되는 곳
### let
+ it을 파라미터로 사용하고 람다 결과를 반환함
+ it을 생략할 수는 없지만 다른 이름으로 변경하여 사용 가능
+ null이 아닐 경우에서의 로직을 실행하도록 사용 됨
### run
+ this를 이용한 접근이 가능하고 람다 결과를 반환
+ 객체 환경설정과 연산 결과를 반환하는데 사용
### with
+ 확장 함수가 아닌 객체를 파라미터로 받음
+ 내부에서는 this를 파라미터로 사용
+ collection에서 별도의 그룹핑에 많이 사용된다고 함
### apply
+ this를 이용해 객체 접근
+ 객체 자체를 반환
+ 주로 설정, 초기화 할 때 사용 됨
### also 
+ it을 이용해 객체 접근
+ 객체 자체 반환
+ call chaning에 주로 사용
