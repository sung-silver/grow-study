# ATOM 13: in 키워드

> in 키워드는 어떤 값이 주어진 범위 안에 들어있는지 검사

### in

- in 키워드는 에터레이션과 원소 여부 검사에 함께 사용함
- for 루프 제어식에 있는 in만 이터레이션을 의미하고, 나머지 in은 모두 원소인지 검사하는 in임
  ```KOTLIN
    fun main(){
      val valeus = 1..3
      for(v in values){
        println("iteration $v")
      }
      val v = 2
      if(v in values){
        println("$v is a member of $values")
      }
    }
  ```
- in 키워드를 범위에만 사용할 수 있는 것은 아니며 어떤 문자가 문자열 안에 들어있는지 검사할 때에도 사용할 수 있음
  ```KOTLIN
    println('t' in "kotlin")
    println('a' in "kotlin")
  ```

### !in

- !in은 어떤 값이 범위에 속하지 않으면 true를 반환함

  ```KOTLIN
  fun isDigit(ch: Char) = ch in '0' .. '9'

  fun notDigit(ch: Char) = ch !in '0' .. '9'

  fun main(){
    println(isDigit('a'))
    println(isDigit('5'))
    println(notDigit('z'))
  }
  ```

### 부동소수점 범위

- 부동소수점은 원소인지 여부를 검사할 때에만 범위를 사용함
  ```KOTLIN
  fun main(){
    println(5.0 in 1.0..10.0) // true를 반환
    println("ab" in "aa".."az") // true를 반환
    println(5.0 in 1.0..<2.0) // 코틀린 1.8부터 지원하게 된 문법 1.0 이상 2.0 미만인 범위를 검사, false를 반환
  }
  ```
