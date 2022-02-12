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

#### Q. String 객체는 객체인데 왜 new로 선언하지 않는가?
<details>
  <summary>답변</summary>

  ---

  * `String`은 대표적 **불변 객체**로, `String 상수 풀 영역`에서 객체를 관리한다.
  * 즉, 상수처럼 **이미 선언된 String 객체가 있으면 이 영역에서 가져다 사용하고, 없다면 여기에 새롭게 객체를 생성하여 사용한다.**

  ---
</details>

#### Q. ""와 new String("")의 차이점은?
<details>
  <summary>답변</summary>
  
  ---

  * `""`은 Heap 내의 별도 공간인 `String 상수 풀 영역`에 문자열을 생성하고, 같은 문자열은 한번만 생성된다.
    * `String 상수 풀 영역`에 생성되는 String 객체는 불변이다.
  * `new String()`는 일반 클래스와 마찬가지로 Heap에 문자열 객체로 생성된다.

  ---
</details>

#### Q. 불변 객체를 써야하는 이유
<details>
  <summary>답변</summary>

  ---

  * 불변 객체란?
    * 불변 객체란 **생성 후 그 상태를 변경할 수 없는 객체**를 말한다. 반대 개념으로 가변(mutable)객체가 있다.
    * 불변 객체란 **외부에서 불변 객체의 값을 수정할 수 없는 객체**를 의미한다.
    * 대표적인 불변 객체: `String`, `Boolean`, `Integer`
    * 대표적인 가변 객체: `StringBuilder`
  * 불변 객체를 왜 사용하는가?
    * **멀티 스레드 환경에서 안전하다. 동기화를 고려하지 않아도 된다.**
    * **부수효과가 발생할 확률이 적다.**
      * 객체는 기본적으로 참조 값을 통해 접근하기 때문에, 방어적 복사를 통해 불변으로 만들어 두는 것이 좋다.
      * 예를 들어, 여러 스레드나 메서드에서 Money를 사용하게 된다면 언제 어디서 부수 효과가 발생해 내부 값이 변경 될지 모르기 때문에 안전하지 않다.
    * **캐시나 Map또는 Set의 요소를 활용하기에 적합하다.**
  * 컬렉션을 불변으로 만들려면 요소도 불변으로 만들어줘야된다.
    * `List`를 불변으로 해도, 그 요소가 불변이 아니면 언제든 가변이 될 수 있기 때문이다. 
  * **단점으로는 메모리 낭비를 유발할 수 있다는 것이다.**
    * 단, 이것은 GC 커스텀을 통해 개선할 수 있을 듯 하다.

  ---
</details>


### Spring

### Database

