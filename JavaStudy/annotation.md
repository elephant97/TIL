# annotation(어노테이션) 📌

### 어노테이션은 언제 사용하나?
> 메타데이터라고 불리기도 함.   JDK 5부터 등장
* 컴파일러에게 정보를 알려줄 때
* 컴파일 할 때와 설치시의 작업을 지정할 때
* 실행할 때 별도의 처리가 필요할 때

### 미리 정해져 있는 어노테이션
> 사용하기 위해서 정해져 있는 어노테이션은 3개가 있으며,   
> 어노테이션을 선언하기 위한 메타 어노테이션은 4개가 있음   
> 메타어노테이션은 선언을 위해 존재하기 때문에 일반적으로 사용 가능한 어노테이션은 3개가 있다.

<br>

* @Override
  > 해당 메소드가 부모 클래스에 있는 메소드를 Override했다는 것을 명시적으로 선언   
  > 이렇게 명시적으로 선언한 경우 Override의 조건을 갖추지 못한 경우에 컴파일 시 오류 발생
* @Deprecated
  > 미리 만들어져 있는 클래스나 메소드가 더 이상 사용되지 않는 경우에 사용
  > 해당 어노테이션이 있는 메소드 사용 시 컴파일 시 경고 발생
* @Supress Warning
  > 경고 문자를 출력하지 않으려고 할 시 사용
  > @Supper Warning("deprecated") 이런식으로 지정하여 사용 가능

### 어노테이션을 선언하기 위한 메타 어노테이션
> 개발자가 직접 어노테이션 선언 시 사용함
* @Target
  * 어노테이션을 어떤 것에 적용할 지를 선언할 때 사용
  ```java
    @Target(ElementType.METHOD)
  ```
    * 적용 대상 목록
        - CONSTRUCTOR : 생성자 선언 시
        - FIELD : enum 상수를 포함한 필드 값 선언 시
        - LOCAL_VARIABLE : 지역 변수 선언 시
        - METHOD : 메소드 선언 시 
        - PACKAGE : 패키지 선언 시
        - PARAMETER : 매개 변수 선언 시
        - TYPE : 클래스, 인터페이스 , enum 등 선언 시
* @Retention
  * 얼마나 오래 어노테이션 정보가 유지되는 지 
  ```java
    @Retention(RetentionPolicy.RUNTIME)
  ```
    * 적용 대상 목록
        - SOURCE : 어노테이션 정보가 컴파일 시 사라짐
        - CLASS : 클래스 파일에 있는 어노테이션 정보가 컴파일러에 의해 참조 가능. 하지만 가상머신(VM)에서는 사라짐
        - RUNTIME : 실행 시 어노테이션 정보가 가상머신에 의해서 참조 가능
* @Documented
  * 해당 어노테이션 정보가 Javadocs(API) 문서에 포함된다는 것을 선언
* @Inherited
  * 모든 자식 클래스에서 부모 클래스의 어노테이션을 사용 가능하다는 것
* @Interface
  * 어노테이션을 선언할 떄 사용
```java
import java.lang.annotation.*;

@Target(ElementType.METHOD)
@Retention(RetentionPolicy.RUNTIME)
public @interface UserAnnotation{
  public int number();
  public String text() default "This is first annotation";
}

//위의 어노테이션 사용 시
public class UserAnnotationSample{
  @UserAnnotation(number=1,text="hi")
  public void annotationSample(){
  }
}

// 위의 어노테이션 선언한 값 확인 시
public void checkAnnotation(){
  Method[] methods = UserAnnotationSample.class.getDeclaredMethods();
  for(Method tempMethod:method){
    UserAnnotation annotation = tempMethod.getAnnotation(UserAnnotation.class);
    if(annotation != null){
      System.out.println(tempMethod.getName()+annotation.number()+annotation.text());
    }
  }
}
```

### 어노테이션도 상속이 안됨
> enum클래스가 상속을 지원하지 않듯이, 어노테이션을 선언할 때에도 미리 만들어 놓은 어노테이션을 확장하는 것 불가능
> 즉, extends 예약어 사용 불가능

### 어노테이션의 용도
* 제약사항 등을 선언하기 위해
  * @Deprecated, @Override, @NotNull
* 용도를 나타내기 위해
  * @Entity, @TestCase, @WebService
* 행위를 나타내기 위해
  * @Statefull, @Tracsaction
* 처리를 나타내기 위해
  * @Column, @XmlElement
