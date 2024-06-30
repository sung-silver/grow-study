# ATOM 14: 식과 문

> 문(statement)과 식(expression)은 대부분의 프로그래밍 언어에서 가장 작은 코드 조각임

### 문(statement) vs 식(expression)

- 문은 효과를 발생시키지만 결과를 내놓지 않음
- 식은 항상 결과를 만들어냄
- 결과를 반환하지 않기 때문에 문이 쓸모 있으려면 문을 둘러싸고 있는 주변 상태를 변경해야 함 → `부수 효과(side effect)`를 얻기 위해 문을 사용함
  > 부수효과: 문이 결과를 만들어내지 않고 부수적인 일을 한다는 뜻

### For는 Statement

- ForIsStatement.kt
  ```KOTLIN
    fun main(){
      // 다음과 같이 할 수 X
      // val f = for(i in 1..10)
      // 컴파일 오류:
      // for is not an expression, and only expression are allowed here
    }
  ```
- for 루프는 부수 효과를 위해서만 사용됨
  > 식은 값을 돌려주기 때문에 이 값을 변수에 대입하거나 다른 식의 일부분으로 쓸 수 있음.
  > 반면에 문은 다른 식의 일부분이 되거나 변수에 대입할 수 없는 최상위 요소임

### 함수 호출 == 식

- 모든 함수 호출 코드는 식임
- UnitReturnType.kt

  - 함수가 Unit을 반환하고 부수 효과를 목적으로 호출되더라도 여전히 함수 호출 결과를 변수에 대입할 수 있음

  ```KOTLIN
    fun unitFun() = Unit

    fun main(){
      println(unitFun())
      val u: Unit = println(42)
      println(u1)
      val u2 = println(0) //타입 추론
      println(u2)
    }

    // 출력
    kotlin.Unit
    42
    kotlin.Unit
    0
    kotlin.Unit
  ```

- Unit 타입에는 오직 Unit이라는 값만 포함됨
- unitFun(): Unit 값을 직접 반환
- val u1: println()의 결과를 저장하며 Unit 타입으로 명시적으로 선언되어 있음
- val u2: 타입 추론을 사용함

### if는 식을 만들 수 있음

- if는 식을 만들 수 있고 if의 결과를 변수에 대입할 수 있음
- AssigningAnIf.kt

  ```KOTLIN
    fun main(){
      val result1 = if(11>42) 9 else 5
      val result2 = if(1<2){
        val a = 11
        a + 42
      } else 42

      val result3 =
        if('x'<'y')
          println("x < y")
        else
          println("x > y")

      println(result1)
      println(result2)
      println(result3)
    }
    // 출력
    x < y  // [1]
    5
    53 // [2]
    kotlin.Unit
  ```

- [1]: x < y가 먼저 출력된 이유는 result3이 정의될 때 if 식을 평가하기 때문임
- [2]: result를 계산하는 코드 블록 안에서 a라는 변수를 정의함
  - if 블록의 마지막에 있는 식의 결과가 if 전체의 결과가 됨 → 11+42
  - 코드 블록을 벗어나면 a에 더 이상 접근할 수 없음
  - a는 임시적인(temporary)인 변수로, 이 변수가 선언된 영역(scope)을 벗어나면 a도 버려짐

### 증가 및 감소 연산자

- `전위 연산자(prefix operation)`: ++i처럼 피연산자 앞에 나오고, 변수값을 먼저 증가시킨 다음에 (변경된) 값을 돌려줌
- `후위 연산자(postfix operation)`: i++처럼 피연산자 다음에 위치하며, 변수값을 증가시키기 직전에 i에 들어 있던 값을 돌려줌
- 증가 및 감소 연산자는 혼동을 야기할 수 있으므로 다른 식 안에 부분 식으로 사용하는 것을 권장하지 않음
