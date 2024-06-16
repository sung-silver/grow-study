# ATOM 7: if식

> if식으로 선택을 한다

### if

- if 키워드는 식을 검사해 그 값이 true나 false 중 어느 것인지 알아내고, 그 결과에 따라 작업을 수행함
- 참이나 거짓을 표시하는 식은 불리언(boolean)이라고 함
- 다음은 `>(보다 크다)`와 `<(보다 작다)` 기호를 사용한 if 식의 예시
  ```KOTLIN
  fun main(){
    if(1>0)
      println("It's true!")
    if(10<11>){
      println("10<11")
      println("ten is less than eleven")
    }
  }
  ```
- if 뒤에 있는 괄호 안의 식은 반드시 true나 false로 평가되어야 함
- 식을 평가한 결과가 true인 경우 바로 다음에 있는 식이 실행됨
- 코드가 여러 줄이라면 중괄호 안에 넣으면 됨
- 한쪽에서 불리언 식을 만든 다음, 다른 곳에서 그 식을 사용할 수도 있음
  - x가 Boolean이기 때문에 if(x) 같은 방법으로 if 식에서 x를 직접 검사할 수 있음
  ```KOTLIN
    fun main(){
      val x: Boolean = 1>=1
      if(x){
        println("It's true!)
      }
    }
  ```
- 불리언 `>=` 연산자는 연산자의 왼쪽 항이 오른쪽 항보다 크거나 같으면 true를 반환함
- `<=` 연산자는 연산자의 왼쪽 항이 오른쪽 항보다 작거나 같으면 true를 반환함

### else

- else 키워드를 사용하면 true인 경로와 false인 경로를 모두 처리할 수 있음
  ```KOTLIN
    fun main(){
      val n: Int = -11
      if(n>0)
        println("It's positive")
      else
        println("It's negative or zero")
    }
  ```
- else 키워드는 if와 함께 사용해야 의미가 있음

### else if

- if문에서 불리언 식 검사를 딱 한 번만 해야 할 필요는 없음
  원한다면 else와 if를 함께 사용해 다양한 논리 조합을 검사할 수 있음
- `==`을 사용해 두 수가 같은지(동등성 비교) 검사함
  ```KOTLIN
    fun main(){
      val n: Int = -11
      if(n>0)
        println("It's positive")
      else if(n==0)
        println("It's zero")
      else
        println("It's negative)
    }
  ```
- 일반적인 패턴은 if로 시작해서 else if를 원하는 만큼 사용한 후 모든 검사를 만족하지 않는 경우에 대하여 else를 사용함

### 논리 부정 연산자

- 논리 부정 연산자 !는 불리언 식을 반전한 결과를 반환함
  ```KOTLIN
    fun main(){
      val y: Boolean = false
      if(!y)
        println("!y is true)
    }
  ```

### return 키워드 생략

- 함수 반환 시 return을 쓰는 대신, else 키워드와 함께 if 식을 사용해 결과를 만들어낼 수도 있음
  ```KOTLIN
    fun oneOrTheOrder(exp: Boolean): String =
      if(exp)
        return "True!"
      else
        "FALSE"

      fun main(){
        val = x
        println("oneOrTheOrder(x==1))
        println("oneOrTheOrder(x==2))
      }
  ```
