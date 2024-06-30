# ATOM 18: 프로퍼티

> 프로퍼티(property)는 클래스에 속한 var이나 val임

### 프로퍼티

- 프로퍼티를 정의함으로써 클래스 안에서 상태를 유지함
- 함수를 한두 개 별도로 작성하는 대신에 클래스를 작성하는 주된 이유가 상태 유지임
- var 프로퍼티는 재대입이 가능하지만, val 프로퍼티는 그렇지 않음
- 각각의 객체는 프로퍼티를 저장할 자신만의 공간을 따로 할당 받음

### 점 표기법

- 클래스 안에 정의한 var나 val은 클래스의 일부분이 되며, 점 표기법(객체이름.프로퍼티\_이름)을 사용해야만 해당 프로퍼티 값에 접근할 수 있음
- 멤버 함수는 점 표기법을 쓰지 않고(즉, 해당 프로퍼티를 한정하지 않고) 자신이 속한 객체의 프로퍼티에 접근할 수 있음
- Cup2.kt

  ```
    class Cup2{
      var percentFull = 0
      val max = 100
      fun add(increase: Int): Int{
        percentFull += increase
        if(percentFull > max)
          percentFull = max
        return percentFull
      }
    }

    fun main(){
      val cup = Cup2()
      cup.add(50)
      println(cup.percentFull)
      ...
    }
  ```

- 클래스 밖에서는 멤버 함수와 프로퍼티를 모두 한정시켜야 함

### 최상위 프로퍼티

- 변경할 수 없으므로 최상위 수준에 val을 정의해도 안전함
- TopLevelProperty.kt

  ```KOTLIN
  val constant = 42

  var counter = 0

  fun inc(){
    counter++
  }
  ```

- 하지만 가변(mutable)인 최상위 프로퍼티를 선언하는 일은 `안티패턴(anti-pattern)`임
- 프로그램이 복잡해질수록 공유된 가변 상태에 대해 제대로 추론하기가 어려워짐
- 가변 상태는 클래스 안에 가두는 것이 가장 좋음

### 참조

- var와 val은 객체가 아니라 참조를 제한함
- var를 사용하면 참조가 가리키는 대상을 다른 대상으로 다시 엮을 수 있지만, val을 사용하면 다른 대상을 엮을 수 없음
- 객체에서 `가변성`은 내부 상태를 바꿀 수 있다는 뜻임
