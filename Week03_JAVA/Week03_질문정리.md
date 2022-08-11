# Week 03 - 질문 정리

#### 김빛누리

1. 가비지컬렉션의 메모리 해제 과정(3가지)에 대해 설명해보시오
- 위의 과정의 비효율적인 부분에 대해 설명해보시오

2. CheckedException / UncheckedException 차이점에 대해 설명해보시오
- 알고있는 checkedException 2가지

3. 자바에서 예외처리방법 2가지 설명해주세요
- try-catch로 자원반납시 문제점?

#### 김주영

1. Error와 Exception의 차이점에 대해 설명하시오
- Checked exception / Unchekced exception 차이점
- unchecked exception은 runtime exception인가?
- 컴파일시에 진행된다는 의미인가요? (컴파일이 관여를 하는가요?)  

2. Exception을 다루는 방법에 대해 설명해보시오
- try-catch를 사용해본 경험이 있으면 말해주세요
- finally()는 어떨 때 사용하는가요?

3. Weak Generational 
- Hypothesis에 대해서 말해주세요
- old영역으로 옮겨지는 기준은 무엇인가요?
- old generation 영역이 가득 차게 되면 어떻게 되나요?

#### 박상민

1. 가비지 컬렉션에서 어떤 상황에서 minor GC 가 일어나고, 일어날 때 객체들의 이동이 어떻게 진행이 되는지 설명해주세요
- Eden영역에 객체가 가득차면 Minor GC가 일어나는데, Survivor 영역에 객체가 가득차면 어떤 GC가 실행되나요? 과정도 설명해주세요

2. Young 영역과 Old 영역에 대해서 설명해주세요.
- Young 영역에서 Old영역으로 넘어가는데 기준이 있나요?
- 어떤상황에서 Young 영역에서 Old 영역으로 객체가 이동하는지 설명해주세요

3. Unchecked Exception에 대해서 설명해주세요
- Checked Exception 이랑 다른 점은 무엇인가요?

#### 박성아

1. GC가 발생되는 과정에 대해 설명해보시오
- 방금 말한 과정의 단점은 무엇인가요?

2. Error와 Exception의 차이에 대해 설명해보세요
- 자바에서 Exception을 처리하는 방법에 대해 설명해보시오
- try-catch 구조에 대해 자세히 설명해보시오

3. 알고있는 Exception Class에 대해 설명해보시오

#### 장시우

1. GC의 메모리 해제 과정에 대해 설명해보시오

2. GC의 영역에 대해 설명해보시오

3. Minor GC와 Major GC의 차이에 대해 설명하시오
