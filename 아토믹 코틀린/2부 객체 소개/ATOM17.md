# ATOM 17: 클래스 만들기

> IntRange나 String처럼 미리 정의된 타입을 사용할 수 있을 뿐만 아니라, 직접 원하는 객체의 타입을 정의할 수도 있음

### 객체

- 클래스를 정의함으로써 새로운 타입을 정의할 수 있음
- 문제를 해결할 때 필요한 개념을 표현하는 객체를 생각하는 것이 문제를 해결하는 방법 중 일부분임

### 예제: 동물원 관리 프로그램

- 동물원의 동물을 관리하는 프로그램을 작성하고 싶다면 동물의 행동 양식, 요구 환경, 함께 잘 지내는 동물이나 함께 살면 서로 싸우는 동물 등에 기반해 동물 유형을 나눌 수 있을 것임
- 각 동물 종에 따른 모든 차이점은 객체의 분류(classification)에 의해 표현될 수 있음
- Animals.kt

  ```KOTLIN
    // class들을 정의
    class Giraffe
    class Bear
    class Hippo

    fun main(){
      // 객체를 만듦
      val g1 = Giraffe()
      val g2 = Giraffe()
      val b = Bear()
      val h = Hippo()

      // 클래스이름()을 호출해 만든 객체는 각각 고유한 정체성을 가짐
      println(g1)
      println(g2)
      println(b)
      println(h)
    }

    // 출력
    Giraffe@28d93b30
    Giraffe@1b6d3586
    Hippo@4554617c
    Bear@74a14482
  ```

  > 클래스를 정의할 때는 class 키워드 다음에 클래스 이름으로 쓸 식별자를 넣음

- 클래스 이름은 반드시 글자로 시작해야 하지만, 두 번째 자리부터는 숫자나 밑줄을 포함할 수 있음
  - 관례적으로 클래스 이름의 첫 번째 글자는 대문자로 표기하며, val이나 var로 쓰이는 이름의 첫 번째 글자는 소문자로 표기함
- @뒤에 출력된 정보는 컴퓨터 메모리의 위치로 프로그램이 생성한 객체의 고유한 주소임

### 클래스 본문

- `클래스 본문(class body)`: 클래스의 특성이나 행동 양식을 정의
- 클래스 본문 안에 정의된 함수는 해당 클래스에 속함 → `멤버 함수`
- `멤버 함수`: 클래스에 속한 함수
- `최상위 함수`: 클래스에 속하지 않은 함수

> 자바와 다르게 메서드라는 용어를 채택하지 않음

### 멤버 함수

- 멤버 함수는 어떤 클래스에 속한 특정 인스턴스에 대해 작용
- 함수가 호출되는 동안 함수 내부에서는 지정한 객체의 다른 멤버에 접근할 수 있음
- 멤버 함수를 호출할 때 코틀린은 객체를 가리키는 `참조(reference)`를 함수에 전달해서 객체를 추적함
  - 멤버 함수 안에서는 this라는 이름으로 참조에 접근할 수 있음
- 멤버 함수는 클래스에 속한 다른 요소들을 멤버 이름만 사용하여 접근할 수 있음
  - 원한다면 this를 사용해 이런 요소를 한정할 수 있음

> 불필요한 this는 명시하지 않아야 함
