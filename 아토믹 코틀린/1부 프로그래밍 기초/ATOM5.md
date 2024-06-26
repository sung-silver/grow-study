# ATOM 5: 데이터 타입

### 타입(type)

- 데이터 타입이라고도 함
- 어떤 식이 취할 수 있는 값의 집합을 제공
- 데이터에 대해 적용할 수 있는 연산, 데이터의 의미, 타입에 속한 값을 컴퓨터 메모리에 저장하는 방식을 정의함
- 타입은 코틀린이 각 타입에 속하는 값과 연산을 어떻게 사용하는 것이 올바른지 알려줌
- StringPlusNumber.kt: 코틀린은 String + 숫자의 연산을 통해 새로운 String을 만듦

  ```KOTLIN
  fun main(){
    println("Sally" + 5.9)
  }
  ```

- StringPlusNumber.kt에 있는 +를 \*으로 변경하면 코틀린이 이해하지 못하고 오류를 표시함

### 타입 추론(type inference)

- 다양한 타입의 값을 변수에 저장하면, 코틀린이 각 값이 어떻게 쓰이는지 살펴보고 각 변수의 타입을 알아내어 알려주는 것
- 다음과 같이 작성하면 코틀린이 타입 추론을 하지 않고 타입을 알 수 있게 함

  ```KOTLIN
    // var 식별자: 타입 = 초기화

    // val n = 1
    val n: Int = 1

    // var p = 1.2
    var p: Double = 1.2
  ```

- 타입을 섞어서 사용하는 경우에도 코틀린은 타입 추론을 이용해 전체 문장이나 식의 의미를 결정함
