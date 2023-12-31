# MVC(Model-View-Controller)패턴📌
> MVC는 사용자 인터페이스, 데이터 및 논리 제어를 구현하는데 널리 사용되는 소프트웨어 디자인 패턴
> 소프트웨어 비지니스 로직과 화면을 구분하는데 중점을 두고 있으며, 이러한 관심사분리는 더 나은 업무의 분리와 향상된 관리를 제공함.

### Model, View, Controller의 관계
> 사용자가 Controller를 사용하게되면 Controller는 Model에게서 데이터를 받아오고 받아온 데이터를 통해
> View에서 시각적인 부분을 제어하여 사용자에게 전달한다.
  1. 사용자의 요청을 Controller가 받는다.
  2. Controller는 Service에서 비지니스 로직을 처리한 후 결과를 Model에 담는다.
  3. Model에 저장된 결과를 바탕으로 시각적 요소 출력을 담당하는 View를 제어하여 사용자에게 전달.
- Web에서의 처리
  1. User: 사용자의 웹 사이트 접속
  2. Manipulates: Controller는 사용자가 요청한 웹 페이지를 보여주기 위해 Model 호출
  3. Updates: Model은 비지니스 로직을 통해 DB 및 파일과 같은 데이터를 제어한 후 결과를 반환
              이후 Controller는 Model에게 반환 받은 결과를 View에 반영
  4. Sees: 데이터를 받아온 View가 사용자에게 웹 페이지를 출력하여 보여줌.

### Model(모델)
> 소프트웨어나 애플리케이션에서 정보 및 데이터 부분을 의미함.
> 이는 Controller에게 받은 데이터를 조작(가공)하는 역할을 수행한다고 볼 수 있다.
> 즉, 데이터와 관련된 부분을 담당하며 값과 가능을 가지는 객체라고 보면 된다.
  * **Model이 가지는 규칙**
    * 사용자가 편집하길 원하는 모든 데이터를 가지고 있어야함.
    * View나 Controller에 대해서 어떤 정보도 알지 말아야 한다.
    * 변경이 일어나면, 변경 통지에 대한 처리방법을 구현해야만 한다.

### View(뷰)
> View는 입력값이나 체크박스 등과 같은 사용자 인터페이스 요소를 나타냄.
> 이는 Controller에게 받은 Model의 데이터를 사용자에게 시각적으로 보여주기 위한 역할을 수행함.
> 사용자에게 보여지는 화면이라고 볼 수 있음.
  * **View가 가지는 규칙**
    * Model이 가지고 있는 정보를 따로 저장해서는 안된다.
    * Model이나 Controller를 알고 있을 필요가 없다.
    * 변경이 일어나면 변경통지에 대한 처리 방법을 구현해야하만 한다.

### Controller(컨트롤러)
> Controller는 Model과 View사이에서 데이터 흐름을 제어한다.
> 사용자가 접근한 URL에 따라 요청을 파악하고, URL에 적절한 Method를 호출하여 Service에서 비지니스 로직 처리.
> 결과를 Model에 저장하여 View에게 전달하는 역할 수행.
> **Controller는 Model과 View의 역할을 분리하는 중요한 요소**
  * **Controller가 가지는 규칙**
    * Model이나 View에 대해 알고있어야 함
    * Model이나 View의 변경을 모니터링 해야 함

### 실전에서 MVC규칙을 지키며 코딩하는 법
1. 모델은 컨트롤러나 뷰에 의존하면 안된다.
   > 모델 내부에 컨트롤러 및 뷰와 관련된 코드가 있어서는 안됨.
2. 뷰는 모델에만 의존해야하고, 컨트롤러에는 의존하면 안된다.
   > 뷰 내부에 모델의 코드만 있을 수 있고, 컨트롤러의 코드가 있으면 안된다.
3. 뷰가 모델로부터 데이터를 받을 때에는 사용자마다 다르게 보여줘야하는 데이터에 한해서만 받아야 함.
4. 컨트롤러는 모델과 뷰에 의존해도 된다.
   > 컨트롤러 내부에는 모델과 뷰의 코드가 있을 수 있다.
5. 뷰가 모델로부터 데이터를 받을 때에는 반드시 컨트롤러에서 받아야 함.

### MVC 패턴의 이점
> MVC의 목표는 관심사의 분리이다.
* 컴포넌트의 명확한 역할 분리로 인해 서로간의 결합도를 낮출 수 있다.
* 코드의 재사용성 및 확장성을 높일 수 있다.
* 서비스를 유지보수하고 테스트하는데 용이해진다.
* 개발자간의 커뮤니케이션 효율성을 높일 수 있다.

### MVC 패턴의 한계점
1. Model과 View의 의존성을 완전히 분리시킬 수 없다.
   > 실제 애플리케이션에서는 뷰가 모델의 상태변화를 지속적으로 감지하고 반영해야 하는 상황이 많아 모델과 뷰
   > 사이에 일정 수준의 의존성이 생기게 되어 완전한 분리가 어려움.
2. 컨트롤러의 비중이 높아져 부담이 커진다면 Massive-View-Controller현상을 피할 수 없다.
   > 컨트롤러가 비대해지는 경향이 있다. 이는 컨트롤러가 다양한 로직과 기능을 담당하게 되면서 발생한다.
   > 이러한 Massive-View-Controller는 유지보수와 확장성에 문제를 일으키며 복잡성이 증가하여 디버깅이 어려워 질 수 있다. 
