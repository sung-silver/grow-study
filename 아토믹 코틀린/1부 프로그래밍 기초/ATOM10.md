# ATOM 10: 불리언

### 논리곱(and)과 논리합(or)

- &&(논리곱): 연산자 오른쪽과 왼쪽에 있는 Boolean 식이 모두 true일 때만 true를 돌려줌
- ||(논리합): 연산자 오른쪽과 왼쪽에 있는 Boolean 식 중 하나라도 true면 true를 돌려줌

### 현재 시간에 따라 가게가 운영 중인지 여부를 결정하는 예제

- Open1.kt

  ```KOTLIN
  fun isOpen1(hour: Int){
    val open = 9
    val closed = 20
    println("Operating hours: $open - $closed")
    val status =
      if(hour>= open && hour <= closed) // hour가 개점 시간과 폐점 시간 사이에 들어가는지 검사
        true
      else
        false
    println("Open: $status")
  }

  fun main() = isOpen1(6)
  ```

- Open2.kt: if식을 더 단순화

  ```KOTLIN
  fun isOpen2(hour: Int){
    val open = 9
    val closed = 20
    println("Operating hours: $open - $closed")
    val status = hour>= open && hour <= closed // hour가 개점 시간과 폐점 시간 사이에 들어가는지 검사
    println("Open: $status")
  }

  fun main() = isOpen2(6)
  ```

- Closed.kt: 논리를 반전시켜 현재 가게가 닫혀 있는 시간인지를 결정

  ```KOTLIN
  fun isClosed(hour: Int){
    val open = 9
    val closed = 20
    println("Operating hours: $open - $closed")
    val status = hour < open || hour > closed
    println("Open: $status")
  }

  fun main() = isClosed(6)
  ```

### 복잡한 논리를 간결한 식으로 기술

- EvaluationOrder.kt

  ```KOTLIN
  fun main(){
    val sunny = true;
    val hoursSleep = 6
    val exercise = false
    val temp = 55

    // [1]: 코틀린의 기본 평가 순서 && → ||
    val happy1 = sunny && temp > 50 || exercise && hoursSleep > 7
    println(happy1)

    // [2]: [1]과 같은 결과
    val sameHappy1 = (sunny && temp > 50) || (exercise && hoursSleep > 7)
    println(sameHappy1)

    // [3]: [1], [2]와 다른 결과를 냄
    val notSame = (sunny && temp > 50 || exercise) && hoursSleep > 7
    println(notSame)
  }
  ```
