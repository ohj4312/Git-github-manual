## 기술면접 대비 준비
아래 링크를 기준으로 추가 내용 정리합니다 :)
https://github.com/binghe819/tech-interview


### CS

### 웹

## JAVA
#### Q. 자바란 무엇인가?
<details>
  <summary>답변</summary>

  ---

  * 자바는 제임스 고슬링과 다른 연구원들이 개발한 **객체 지향적 프로그래밍 언어**이다.
    * 엄밀히 말하면 멀티 패러다임 프로그래밍언어 (절차형, 함수형 모두 지원)
  * 특징
    * JVM (WORA) 가상머신 -> 운영체제와 독립적
    * GC라는 프로세스를 통해 자동으로 메모리 관리는 수행한다.
    * 멀티 스레드를 지원한다.
    * Managed 언어

  ---
</details>

#### Q. 자바를 사용한 이유는?
<details>
  <summary>답변</summary>
  
  ---

  * 가장 대표적인 객체지향언어. (확장, 유지보수면에서 유리하다)
  * 메모리를 직접 관리하지 않아도 되는 Managed 언어. (시간 단축, 편의성)
  * 플랫폼과 독립적인 언어.
  * 언어 차원에서 스레드를 지원해준다.
  * 높은 점유율과 오랜 역사. 문서화.

  ---
</details>

#### Q. Primitive Type vs Wrapper class
<details>
  <summary>답변</summary>

  ---

  * Wrapper Class를 사용하는 이유
    * **Nullable**
    * `toString()`를 통해 String 타입으로 바로 변환 가능
    * **원시타입을 객체 타입처럼 사용 가능 (자율적인 객체로 사용 가능)**
    * Generic 타입으로 사용하기 위함
    * 멀티스레딩에서 동기화를 지원하려면 객체가 필요 (?)
  * Boxing vs Unboxing (Auto)
    * Primitive -> Warpper : Boxing
    * Wrapper -> Primitive : Unboxing
    * JVM은 상황에 따라 Boxing을 하기도, Unboxing을 하기도 한다.
    * [편리한 AutoBoxing의 단점](./JAVA/AutoBoxing/AutoBoxing의%20단점.md)
      * **Wrapper Class를 연산하면 오토박싱/언박싱이 일어나기에 비효율적이다.**

  ---
</details>


#### Q. Generic은 왜 Wrapper Class만 사용하는가?
<details>
  <summary>답변</summary>

  ---

  * 우선 Generic을 사용하는 가장 큰 이유가 타입 체크를 위함이다. 즉, 컴파일 타임시에만 타입 체크 및 제약을 적용하고, 자동 형변환을 해준다. 그리고 컴파일 된 `.class` 파일에는 실제로 제네릭 정보가 전혀 없다. (소거됨)
  * 다르게 말하면 런타임엔 Generic으로 주어진 타입으로 형변환 된 Object만이 존재할 수 있다. 그러기 때문에 Primitive 타입은 Object가 될 수 없기에 불가능한 것.
  * 쉽게 말하면 **Generic 특성상 Object로 Convertable한 타입만 가능하다.**
  * [참고 1](https://www.quora.com/Why-is-it-impossible-to-use-primitive-types-as-a-type-parameter-in-Java), [참고 2](https://stackoverflow.com/questions/2721546/why-dont-java-generics-support-primitive-types)

  ---
</details>

#### Q. 생성자 vs 정적 팩토리 메서드
<details>
  <summary>답변</summary>

  ---

  * 생성자와 정적 팩토리 메서드의 차이는 정적 팩토리 메서드의 장단점으로 알 수 있다.
  * 정적 팩토리 메서드의 장점
    * 이름을 가질 수 있다.
    * **반드시 새로운 객체를 만들 필요가 없다. 불변 객체를 캐싱하거나, Validation을 처리할 수 있다.**
    * 반환 타입의 하위 타입 객체를 반환할 수 있는 능력이 있다.
    * 입력 매개변수에 따라 매번 다른 클래스의 객체를 반환할 수 있다.
    * static 팩토리 메서드를 작성하는 시점에는 반환할 객체의 클래스가 존재하지 않아도 된다.
  * 정적 팩토리 메서드의 단점
    * 상속하려면 public, protected 생성자가 필요하니, 정적 팩토리 메서드만 제공하면 하위 클래스를 만들 수 없다.
    * static 팩토리 메서드는 프로그래머가 찾기 어렵다.

  ---
</details>

### Spring

### Database

