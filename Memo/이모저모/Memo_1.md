면접 질문
질문 1:
백엔드 개발에서 중요한 Java와 Spring에 대한 경험이 부족함에도 불구하고, 이 포지션에 지원하게 된 동기는 무엇인가요?

질문 2:
C 언어를 사용한 5년의 경험을 바탕으로, 어떻게 Java와 Spring과 같은 새로운 기술 스택을 빠르게 습득하고 적응할 수 있을 것 같나요?

질문 3:
대용량 데이터 처리에 대한 경험이 있나요? 만약 있다면, 구체적인 예시와 사용한 기술, 그리고 해결한 문제에 대해 설명해주시겠어요?

질문 4:
C 언어를 사용하면서 어떤 종류의 백엔드 시스템을 개발했나요? 그 과정에서 가장 도전적이었던 문제는 무엇이었고, 어떻게 해결했나요?

답변 1:
우선 약 5년간 C 언어로 개발해오면서 물론 C언어의 장점도 많이 있겠지만, 현대에 맞는 개발을 하는데에 레퍼런스가 많지 않다던지 또는 C언어의 수요가 부족하다라는 단점을 많이 느껴왔습니다. 현재 한국에서 가장 많이 필요로 하는 기술이 무엇인지를 봤을 때 Java 와 Spring이라는 생각을 많이 하게 되었고, 현대 시대의 흐름에 맞는 객체 지향 언어에 대한 경험과 해당 언어의 장점을 이용하여 다양한 개발을 해보고싶다는 생각을 하게되어 지원하였습니다. 또한 큰 서비스회사에서 대용량 데이터 처리를 하는 경험을 얻고싶었습니다.

답변 2:
우선 이 포지션에 지원하기 위해 Java에 대해 공부를 하게 되면서 Java와 C는 비슷하면서도 한편으로는 상당부분이 다르다고 생각하게되었습니다. C는 상대적으로 개발자가 많은 부분을 관여하고 조절해야하는 것이 많습니다. 예를들면 메모리에 대한 할당과 해제라던지, 각 OS에 따른 컴파일이라던지 필요로하는 자료구조나 로직을 직접적으로 구현해야하는 것이 많습니다. 하지만 Java는 이미 많은 것들이 이미 만들어져있으며, 그것들을 어떻게 사용해야하는지, 메모리 관리를 GC가 직접해주지만 GC가 메모리 해제를 효율적으로 잘 하려면 어떻게 코드를 짜야하는지 등을 고민해야 하는 언어입니다. 이러한 차이점을 봤을 때 C언어를 약 5년간 다뤘다는 점이 저한테 Java의 언어를 습득하는데에 빠르게 습득할 수 있는 장점이 될 수 있을 것 같습니다 처음부터 Java만을 다뤘다면 직접 자료구조를 만들어보거나 이미 제공된 플랫폼들을 개발하는 일을 해보지 못했겠지만 반대로 직접 C를 사용하면서 자료구조들을 직접 만들고 적용해 본 경험이 있어 내부를 더 깊이있게 파악할 수 있고, 또한 C가 OS와 밀접하기 때문에 OS와 관련된 지식을 더 많이 알고있어 메모리나 프로세스의동작을 많은 부분 알고있어 Java를 배울 때 해당 언어의 특성을 추가적으로 배우며 GC의 동작이 여유롭게 될 수 있는 부분에 집중해서 보다 빠르게 습득할 수 있을 것 이라고 생각합니다. 

답변 3:
대용량 데이터처리 같은 경우는 회사에서 Slow log나, binlog같은 Mysql/Maria의 로그 파일들을 파싱해본 경험이 있습니다. 해당 파일은 db의 설정 값에 따라 대용량 파일이 생성될 수있으며 해당 파일을 쉽게 파싱하고 처리할 수있도록 파일을 감시하는 쓰레드를 만들고 마지막 읽었던 파일의 위치를 포인터로 갖고있다 포인터의 끝이 달라지는 순간 새로 쓰인 파일의 여부를 감지하고 해당 파일을 사용자가 분석할 수 있도록 Mysql/Maria 가 정해놓은 규칙대로 데이터화 하였습니다. 이런 과정에서 너무 많은 데이터가 들어오는 경우 쿼리 사이즈를 측정하고 끝을 감지하는 포인터를 정확하게 파악하는 것이 어려웠습니다. 파일의 형태가 append되는 형태였는데 파일이 가득 찰 경우에 마지막 읽은 포인터의 위치가 정확하지 않게 되었습니다. 기존 로직은 쿼리의 시작 점을 가지고 한 줄씩 읽어 각 줄의 데이터 len값을 구해 쿼리를 한번에 읽어오는 로직이었으며 해당 로직이 빠르게 많은 데이터가 들어오는 경우 포인터의 시작점이 명확하지 않아 쿼리가 짤리는 경우가 있었습니다. 해당 경우 쿼리가 잘리는 현상을 방지하고자 한줄씩 읽어 쿼리의 끝을 만났을 때 처음 위치부터 쿼리의 끝을 한번에 읽어오는 로직에서 읽으면서 새롭게 realloc하여 데이터를 바로바로 버퍼에 담도록 하여 해결한 경험이 있습니다. 

답변 4:
C언어를 사용하면서 데이터베이스와 OS의 성능을 모니터링하는 시스템을 개발하였고, 그중에서 가장 도전적이었던 문제는 입사 후 가장 지식이 적었던 상황에서 개발했었던 binlog 추출이었습니다. binlog가 발생하는 상황은 db에 부하가 있을 시 발생하는데, 부하에 해당하는 정보들을 바이너리 파일로 binlog가 작성되어 해당 binlog를 decode하는 과정 또한 오래걸릴 것이라고 판단했습니다. 처음 개발할 당시 사내에서 서버를 구성해서 간단히 테스트하였을 땐 빠른시간안에 추출되었고 문제가 없었으나 스스로 생각했을 때 부하가 있다면 decode의 과정이 오래걸릴 텐데 해당 문제를 해결하는 방법에 대해 고민하게 되었습니다. 그때 해결방법으로 내가 사용자라면 최대 몇분을 기다릴 수 있을까? 라는 고민을 하게되었고 그 대기시간의 기준을 1분으로 잡고 1분안에 decode완료되지 않은 경우 decode 커맨드를 끊는것이 필요했습니다 C에서 system함수로 수행 시 해당 커맨드가 수행되고있는 정확한 pid값을 알기가 어려웠기 때문에 shell로 실행시켜 내가 실행시킨 쉘의 pid를 알아내고, 해당 pid가 1분 내로 수행 완료되지 않는다면 강제로 종료한 후 1분동안 수행 한 결과만 데이터로 전송하자는 아이디어를 내고 적용 시켰던 경험이 있으며 그 덕에 부하가 있는 경우에도 1분내로 사용자는 데이터를 받아볼 수 있게 되었습니다
