# ATOM 3: Hello, World!

### 식별자(identifier)

- 프로그램을 이루는 요소를 가리키기 위해 사용
- 선택해야 하는 사항
  - 식별자가 가리키는 내용이 프로그램을 실행하는 동안 별할 수 있는가? (var)
  - 단 한번만 어떤 값을 지정하면 되는가? (val)
- 문자(유니코드 문자)나 밑줄(\_)로 시작됨
- 첫 글자로 문자나 밑줄을 적은 다음부터는 문자나 밑줄, 숫자도 원하는 길이만큼 더 올 수 있음
  식별자를 구별할 때에 대소문자 여부도 구분

### var

- 변할 수 있는 수(variable)의 약자로 내용을 재대입할 수 있음
  ```KOTLIN
  var 식별자 = 초기화
  ```
- Vars.kt

  ```KOTLIN
  fun main(){
    var whole = 11 // [1]
    var fractional = 1.4 // [2]
    var words = "Twas Briliing" // [3]
    println(whole)
    println(fractional)
    println(words)
  }
  ```

  - [1] whole이라는 이름의 var를 만들고 11을 저장
  - [2] fractional이라는 이름의 var에 소수 1.4를 저장
  - [3] words라는 var에 텍스트를 저장

  > 변할 수 있는 수라는 이름처럼 var에 저장된 값은 달라질 수 있음 즉, var에 저장된 데이터를 변경할 수 있음 = `mutable(가변)`

- AvarIsMutable.kt
  ```KOTILIN
  fun main(){
    var sum = 1
    sum = sum + 2 // [1]
    sum += 3 // [2]
    println(sum)
  }
  ```
  - [1] sum의 현재 값을 가져와 2를 더한 결과를 다시 sum에 대입
  - [2] += 연산자: 이전 값을 얻어와 뒤의 숫자를 증가시킴
- var에 저장한 값을 변경하는 방식은 변화를 표현할 때 유용함

### val

- 프로그램이 복잡해질수록, 변화하지 않는 식별자를 통해 값을 표현해야 더 명확하고 안전하며 이해하기 쉬워짐 = 재대입을 하지 않음
- val을 사용해 변화하지 않는 식별자를 지정할 수 있음
- val은 처음 생성될 때 대입이 단 한 번만 이루어짐
  ```KOTLIN
  val 식별자 = 초기화
  ```
- val 키워드는 값(value)을 뜻하며, 값이란 변할 수 없는 것을 가리킴
- val 변수는 `불면(immutable)`임
- Vals.kt
  ```KOTLIN
    fun main(){
      val whole = 11
      // whole = 15 //[1]: 오류
      val fractional = 1.4
      val words = "Twas Brilling"
      println(whole)
      println(fractional)
      println(words)
    }
  ```
  - [1] val을 초기화하고 나면 재대입할 수 없음
    - whole에 다른 값을 대입하려고 시도하면 'val cannot be reassigned' 라고 뜸

### 변수명

- 식별자에 이름을 붙일 때 좀 더 서술적인 이름을 붙이면 좋음
  - 코드를 이해하기 쉬움
  - 주석을 추가할 필요성이 줄어듦

### var VS val

- var는 프로그램이 실행될 때 변경되어야만 하는 값을 표현할 경우에 유용함
- val만 사용하면 프로그램을 확장하고 유지보수하기가 더 쉬워짐
  - 그러나 문제를 해결하기에는 너무 복잡해지는 경우도 가끔 있음
- 코틀린에서는 var도 허용해 유연성을 제공하는 것
- 그러나 var가 필요한 경우가 거의 없으며, 이를 사용하지 않으면 프로그램이 더 안전해지고 신뢰성이 높아짐
