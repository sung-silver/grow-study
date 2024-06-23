# ATOM 8: 문자열 템플릿

> 문자열 템플릿은 String을 프로그램으로 만드는 방법이다

### 문자열 템플릿

- 식별자 이름 앞에 $를 붙이면, 문자열 템플릿이 그 식별자의 내용을 String에 넣어줌
  ```KOTLIN
  fun main(){
    val answer = 42
    println("Found $answer!") // [1] $answer는 answer의 값으로 치환됨
    println("printing a $1) // [2] $ 다음에 오는 대상이 프로그램 식별자로 인식되지 않으면 아무 일도 일어나지 않는다
  }
  ```

### 문자열 연결(concatenation)

- 문자열 연결(+)로 String에 값을 넣을 수 있음
  ```KOTLIN
  fun main(){
    val s = "hi\n"
    val n = 11
    val d = 3.14
    println("first: " + s + "second: "+ n + "third: " + d)
  }
  ```

### 식 평가

- ${}의 중괄호 안에 식을 넣으면 그 식을 평가함
- 평가한 결과값을 String으로 변환해 결과 String에 삽입함
  ```KOTLIN
  fun main(){
    val condition = true
    println(
      "${if (condition) 'a' else 'b'}" // [1] if(condition) 'a' else 'b'를 평가한 결과가 전체 ${} 식을 대신함
    )
  }
  ```

### 특수 문자

- String 안에 큰따옴표 등의 특수 문자를 넣어야 하는 경우에는 `역슬래시(\)`를 사용해 `이스케이프(escape)`하거나 큰따옴표를 연달아 세 개 쓰는 String 리터럴을 사용해야 함
  ```KOTLIN
    fun main(){
      val s = "value"
      println("s = \"$s\".")
      println("""s = "$s".""")
    }
  ```
- 큰따옴표 세 개를 쓸 때도 큰따옴표 하나만 쓰는 문자열과 마찬가지로 $ 식별자나 ${식}을 사용해 식의 값을 삽입할 수 있음
