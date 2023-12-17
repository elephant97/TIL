# Java7에서 추가되거나 달라진 것들📌
> - 숫자 표시 방법 보완
> - switch문에서 String사용
> - 예외 처리시 다중 처리 가능
> - 제네릭을 쉽게 사용할 수 있는 Diamond

### 달라진 숫자 표현법
* 0을 숫자 앞에 넣어주면 8진수
* 0x를 숫자 앞에 넣어주면 16진수
* 0b를 숫자 앞에 넣어주면 2진수로 표현 가능하며, 7에서 추가된 내용
* 숫자 사이에 "_"를 넣어 1000단위 구분 가능 ex) 1_000_000

### switch문장의 확대
* Java 7부터는 switch문장에 String 사용 가능
  > string 문자열이 null인 경우 NullPointerException이 발생하므로 null체크 필요

### 제네릭의 diamond
