# ATOM 12: 루프와 범위

> for 키워드는 주어진 순열에 속한 각 값에 대해 코드 블록을 실행함

### 루프

- 주어진 값은 어떤 범위나 String, 이 책에서 다룰 컬렉션(collection) 등이 될 수 있음
- in 키워드는 이러한 값을 하나하나 가져와 사용한다는 사실을 나타냄
  ```KOTLIN
    for(v in 값들){
      // v를 사용해 어떤 일을 수행함
    }
  ```
- 루프를 돌 때마다 v에는 값들의 다음 원소가 들어감

### for 루프

- 정해진 횟수만큼 동작을 반복함
  ```KOTLIN
  fun main(){
    for(i in 1..3){
      println("Hey $i!")
    }
  }
  ```

### 범위(range)

- 양 끝을 표현하는 두 정수를 사용해 구간을 정의한 것
- 범위를 정의하는 기본적인 방법으로는 두 가지가 있음

  ```KOTLIN
    val range1 = 1..10 // [1] .. 양 끝 값을 포함한 범위를 만듦
    val range2 = 0 until 10 // [2] until 다음에 오는 제외한 범위를 만듦
  ```

- 범위를 역방향으로 이터레이션할 수도 있음
- step 값을 사용하면 값의 간격을 1이 아닌 값으로 조정할 수 있음
  ```KOTLIN
    val range3 = 5 downTo 1 // [1] downTo: 감소하는 범위를 만듦
    val range4 = 0..9 step 2 // [2] step: 간격을 변경함
    val range5 = 0 until 10 step 3 // [2] until과 step을 함께 사용할 수 있음
  ```
- `IntProgression`: Int 범위를 포함하여 코틀린이 제공하는 타입
  ```KOTLIN
  fun showRange(r: IntProgression){
    for ( i in r){
      print("$i ")
    }
  }
  ```
- 이터레이션은 정수, 문자처럼 하나하나 값이 구분되는 양에 대해서만 가능함
  - 부동 소수점 수에 대해서는 할 수 없음

### 문자

- 각괄호([])를 사용하면 숫자 인덱스를 통해 문자열(String 타입)의 문자에 접근할 수 있음
- String의 문자를 셀 때는 0부터 세기 때문에 s[0]은 String s의 첫 번째 문자를 가리킴
  - s.lastIndex를 읽으면 문자열 s의 마지막 인덱스 값을 알 수 있음
  ```KOTLIN
  fun main(){
    val s = "abc"
    for(i in 0..s.lastIndex){
      print(s[i]+1)
    }
  }
  ```
- 문자는 아스키 코드에 해당하는 숫자 값으로 저장됨
  - 따라서 정수를 문자에 더하면 새 코드 값에 해당하는 새로운 문자를 얻을 수 있음
  ```KOTLIN
   fun main(){
    val ch: Char = 'a'
    println(ch+25)
    println(ch<'z')
   }
  ```
- 루프를 사용하여 String의 각 문자에 대한 이터레이션을 직접 수행할 수 있음
  ```KOTLIN
    fun main(){
      for(ch in "Jnskhm "){
        print(ch + 1) // ch에는 문자열에 들어 있는 문자가 차례대로 전달됨
      }
    }
  ```

### repeat()

- repeat()은 키워드가 아니라 표준 라이브러리 함수임
- 어떤 동작을 단순히 정해진 횟수만큼 반복하고 싶을 때 사용함
  ```KOTLIN
    repeat(2){
      println("hi!")
    }
  ```
