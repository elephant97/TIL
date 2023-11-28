# abstract(추상클래스)	:pushpin:

### abstract 클래스란?
* 이 클래스는 하위 클래스에게 공통된 속성이나 메서드를 제공하고, 동시에 하위 클래스에서 반드시 구현해야 하는 추상 메서드를 정의할 수 있는 클래스 이다.
* abstract 클래스는 자바에서 마음대로 초기화하고 실행할 수 없도록 되어있다.
* abstract 클래스를 구현해 놓은 클래스로 초기화 및 실행이 가능하다.
   
### abstract 클래스 선언 예시
```java
      public abstract class MemberManagerAbstract{
         public abstract boolean addMember(MemberDto member);
         public void pringLog(string data){
            System.out.println(data);
         }
      }
```
   
### abstract 클래스의 규칙
* abstract 클래스는 클래스 선언시 abstract라는 예약어가 클래스 앞에 추가되면 됨
* abstract 클래스 안에는 abstract로 선언된 메소드가 0개 이상 있으면 된다. 즉 abstract로 선언된 메소드가 한개도 없어도 됨.
* abstract으로 선언된 메소드가 한개라도 있으면, 그 클래스는 '반드시' abstract로 선언되어야만 함.
* abstract 클래스는 몸통(body)가 있는 메소드가 0개 이상 있어도 전혀 상관 왒으며, static이나 final 메소드가 있어도 된다.
* 인터페이스처럼 implements라는 예약어를 사용하여 구현할 수 없다 왜냐하면 인터페이스가 아닌 '클래스' 이기 떄문.
   
### 💡abstract로 선언된 메소드가 한개도 없어도 된다고 했는데 그럼 무슨 의미가 있나? (chatGPT 내용 발췌)
* abstract 클래스가 추상 메소드를 포함하지 않아도 유용한 이유
  1. 일반 메소드를 공유
      * 추상 클래스는 추상 메소드 외에도 일반 메소드와 멤버 변수를 포함할 수 있습니다.
      * 이는 공통된 동작이나 속성을 하위 클래스들 사이에서 공유하고 재사용할 수 있게 해줍니다.
  2. 기본 구현 제공
      * 추상 클래스는 추상 메소드를 구현하지 않고도 일반 메소드의 기본 구현을 제공할 수 있습니다.
      * 이는 하위 클래스에서 반드시 구현해야 하는 추상 메소드가 없더라도, 공통된 동작이나 초기화를 제공할 수 있게 합니다.
  3. 확장성 제공
      * 추상 클래스는 추상 메소드를 추가함으로써 쉽게 확장될 수 있습니다.
      * 즉, 추후에 새로운 하위 클래스가 추가될 때, 해당 클래스에서 필요한 추상 메소드만 구현하면 됩니다.
  4. 코드 구조화
      * 추상 클래스를 사용하면 코드를 논리적으로 구조화할 수 있습니다.
      * 비슷한 동작이나 속성을 갖는 클래스들을 그룹화하여 코드의 가독성과 유지보수성을 향상시킬 수 있습니다.
  5. 강제성 제공 여부 선택
      * 추상 클래스에서 추상 메소드를 선언함으로써, 하위 클래스에서 반드시 해당 메소드를 구현하도록 강제할 수 있습니다.
      * 그러나 추상 메소드가 없는 경우에는 하위 클래스에서 구현을 강제하지 않아도 됩니다.
  
### abstract 클래스의 abstract 메소드 구현부 작성
* implements가 아닌 extends를 사용하여 구현
```java
  public class MemberManagerInpl extends MemberManagerAbstract{
  }
```

