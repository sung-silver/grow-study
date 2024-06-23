# ATOM 9: 수 타입

> 숫자(수) 타입은 타입에 따라 서로 다른 방식으로 저장됨

### 타입 추론

- 식별자를 만들고 정수값을 대입하면 코틀린은 Int 타입을 추론함
  ```KOTLIN
  fun main(){
    val million = 1_000_000 // Int를 추론
    println(million)
  }
  ```
- 가독성을 위하여 코틀린에서 숫자 사이에 밑줄(\_)을 넣도록 허용함

### 수학 연산자

- 더하기(+), 빼기(-), 곱하기(\*), 나누기(/), 나머지(%)를 제공함
- 나머지 연산은 정수 나눗셈의 나머지를 결과로 돌려줌
- 연산의 순서는 기본적인 (수학에서 정의된) 산술 연산 순서를 따름

### 체질량지수(BMI) 예제

- BMIMetric.kt

  ```KOTLIN
  fun bmiMetric(
    weight: Double,
    height: Double
  ): String{
    val bmi = weight / (height*height) // [1] 괄호를 제거하면 weight를 height로 나눈 결과에 height를 곱하게 되므로 결과가 달라짐
    return if(bmi<18.5) "Underwieght
      else if(bmi <25) "Normal wieght
      else "Overweight"
  }

  fun main(){
    val weight = 72.57 // 160 lbs
    val height = 1.727 // 68 inches
    val status = bmiMetric(weight, height)
    println(status)
  }

  // 출력: Normal wieght
  ```

- bmiMetric()은 Double을 사용해 키와 몸무게를 처리
- Double은 아주 큰 부동소수점(floating point) 수와 아주 작은 부동소수점 수를 저장할 수 있음
- 영국 단위계를 사용한 예제(BMIEnglish.kt)

  ```KOTLIN
  fun bmiEnglish(
    weight: Int,
    height: Int
  ): String{
    val bmi = weight / (height*height) * 703.07 // [1]
    return if(bmi<18.5) "Underwieght
      else if(bmi <25) "Normal wieght
      else "Overweight"
  }

  fun main(){
    val weight = 160
    val height = 68
    val status = bmiEnglish(weight, height)
    println(status)
  }

  // 출력: Underwieght
  ```

- 두 코드의 출력 결과가 다른 이유는 코틀린이 정수의 나눗셈을 하는 과정에서 나머지를 `버림(truncation)`으로서 반올림을 하지 않기 때문임
  - 160/68\*68은 0이 되기 때문에 Underweight이라는 결과를 얻게된 것
- 이러한 문제를 피하기 위해 계산식의 앞부분에서 703.07을 곱하도록 변경하여 결과를 Double로 강제 변환하는 효과를 발생시켜야 함
  ```KOTLIN
  val bmi = 703.07 * wieght / (height*height)
  ```
- bmiMetric에서는 파라미터를 Double로 명시해주었기 때문에 이러한 문제가 발생하지 않았던 것임

### Overflow

- 프로그래밍 언어마다 정수에 저장할 수 있는 값의 범위가 정해져 있음
- 코틀린의 Int 타입은 32 비트 표현의 제약으로 인해 -2^31과 +2^31-1 사이의 값을 저장할 수 있음
- 두 Int를 더하거나 곱하면 Int로 충분하지 않을 수 있는데, 이 경우 `넘침(overflow)`가 발생함
  ```KOTLIN
    val i: Int = Int.VAX_VALUE
    println(i+i)
  ```
- `Int.MAX_VALUE`: Int 타입이 저장할 수 있는 가장 큰 값을 나타내는 미리 정의된 상수
- 넘침이 발생하면 음수이면서 예상보다 훨씬 작은 값이 나오기 대문에 명확히 틀린 결과가 나옴
- 코틀린이 컴파일 시점에 항상 넘침 가능성을 찾아내지는 못함 → 넘침을 방지하는 것은 개발자의 역할
- 만약 프로그램이 큰 수를 저장해야 한다면 Long(-2^63 ~ +2^63-1)을 사용할 수 있음
- Long 타입의 val을 정의하고 싶으면 수 리터럴 뒤에 L을 붙여서, 해당 리터럴을 Long 타입으로 다뤄야 함을 코틀린에게 명시하면 됨
  ```KOTLIN
    fun main(){
      val i = 0 // Int 타입을 추론
      val l1 = 0L // L을 사용해 Long 타입으로 다뤄야 함을 명시
      val l2: Long = 0 // 명시적으로 타입 지정
      println("$l1 $l2")
    }
  ```
- `Long.MAX_VALUE`: Long 타입으로 저장할 수 있는 가장 큰 값
