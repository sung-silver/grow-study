# ATOM 11: while로 반복하기

### while

- while은 주어진 Boolean식이 true인 동안 블록을 반복 수행함
  ```KOTLIN
  while(Boolean 식){
    // 반복할 코드
  }
  ```
- 루프를 시작할 때 Boolean식을 한 번 평가하고, 블록을 다시 반복하기 직전에 매번 다시 평가함

  ```KOTLIN
  fun condition(i: Int) = i<100 // [1] 비교 연산자는 Boolean 결과를 내놓는다. 따라서 코틀린은 condition() 함수의 결과 타입을 Boolean으로 추론함

  fun main(){
    var i=0
    while(condition(i)){ // [2] 이 while 조건식은 condition()이 true를 반환하는 동안 본문의 코드를 반복해야함을 의미
      print(".")
      i+=10 // [3] += 연산자가 유효하려면 i는 var여야 함
    }
  }
  ```

### while과 do-while

- do와 while을 함께 사용
  ```KOTLIN
  do{
    // 반복할 코드
  }while(Boolean 식)
  ```
- DoWhileLoop.kt

  ```KOTLIN
  fun condition(i: Int) = i<100 // [1] 비교 연산자는 Boolean 결과를 내놓는다. 따라서 코틀린은 condition() 함수의 결과 타입을 Boolean으로 추론함

  fun main(){
    var i=0
    do{
      print(".")
      i+=10
    } while(condition(i))
  }
  ```

- while과 do-while의 차이
- do-while:n 식이 false를 돌려줘도 본문이 최소 한 번은 실행됨
- while: 처음에 조건문이 false면 본문이 결코 실행되지 않음

### 증감 연산자

- 증가: ++
- 감소: --

### 이터레이션(iteration)

- 어떤 정수 범위의 값을 차례로 반복
- 정수 범위에 대한 이터레이션을 할 때는 for문을 사용
