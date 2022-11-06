# Week 11 - 질문/답변 정리

#### 김빛누리
1. 스프링 프레임워크의 특징

```
경량 컨테이너
스프링은 경량의 컨테이너
스프링 컨테이너는 자바 객체의 생성, 소멸과 같은 라이프 사이클을 관리하며,
스프링 컨테이너로부터 필요한 객체를 검색하여 사용할 수 있다.

DI(의존성 주입)
- 객체를 직접 생성하는 게 아니라 외부에서 생성한 후 주입 시켜주는 방식이다.
- 모듈 간의 결합도가 낮아지고 유연성이 높아진다.
- XML 설정 파일, anotation을 통해 객체간의 의존관계를 설정할 수 있다.
- DI컨테이너 -> 실행시점에 클래스 간의 관계가 형성

AOP
- 관점지향 프로그래밍
- 로깅, 보안, 트랙잭션과 같은 공통 기능을 핵심 비즈니스 모듈로부터 분리해서
각 핵심 비즈니스 모듈에 적용할 수 있다.

POJO
- 스프링 컨테이너에 저장되는 자바 객체는 특정한 인터페이스를 구현하거나 클래스를 상속받지 않아도 된다.
- 따라서 기존에 작성한 클래스를 수정할 필요 없이 스프링에서 사용할 수 있다.

트랜잭션
설정파일 또는 코드 상에서 트랜잭션 관리할 수 있다.
```

- 컨테이너?
    
    ```java
    애플리케이션 객체의 생명 주기화 설정을 포함하고 관리한다는 점에서 컨테이너
    ```
    

2. 스프링 Bean 은 무엇인가요

```
spring IoC 컨테이너가 관리하는 자바 객체를 빈(Bean)이라고 한다.
```

- 스프링 Bean의 생성 방법?
    
    ```
    - 자바 어노테이션 사용하는 방법
    이 어노테이션이 등록되어있는 경우 스프링이 이를 확인해 자체적으로 Bean
    생성한다
    @Component, @Controller, @Service 등 어노테이션 이용
    
    - XML Configuration
    설정파일 이용
    ```
    

3. 스프링 MVC 실행순서?

```
- 클라이언트가 url을 요청하면, 웹 브라우저에서 스프링으로 request가 보내진다.
- Dispatcher Servlet이 request를 받으면, Handler Mapping을 통해 해당 url을 담당하는 Controller를 탐색 후 찾아낸다.
- Controller로 request를 보내주고, 보내주기 위해 필요한 Model을 구성한다.
- Model에서는 페이지 처리에 필요한 정보들을 Database에 접근하여 쿼리문을 통해 가져온다.
- 데이터를 통해 얻은 Model 정보를 Controller에게 response 해주면, Controller는 이를 받아 Model을 완성시켜 Dispatcher Servlet에게 전달해준다.
- Dispatcher Servlet은 View Resolver를 통해 request에 해당하는 view 파일을 탐색 후 받아낸다.
- 받아낸 View 페이지 파일에 Model을 보낸 후 클라이언트에게 보낼 페이지를 완성시켜 받아낸다.
- 완성된 View 파일을 클라이언트에 response하여 화면에 출력한다
```

4. Filter 와 Interceptor 차이?

```
둘다 요청에 대한 로깅/검사, 인증, 인가 역할

Filter는 웹 컨테이너에서
Interceptor는 스프링 컨테이너에서 동작
```

#### 김주영
1. Spring MVC 의 진행 과정에 대해 설명해주세요
```
클라이언트가 url 을 요청하면 웹 브라우저에서 스프링으로 request 가 보내짐
Dispatcher Servlet이 request를 받으면 Handler Mapping을 통해 해당 url을 담당하는 Controller를 탐색 후 찾아냄
찾아낸 Controller 로 request를 보내주고, 보내주기 위해 필요한 Model을 구성
Model에서는 페이지 처리에 필요한 정보들을 Database에 접근하여 쿼리문을 통해 가져옴
데이터를 통해 얻은 Model정보를 Controller에게 Response해주면 Controller는 이를 받아 Model을 완성시켜 Dispatcher Servlet에게 전달해줌
Dispatcher Servlet은 View Resolver를 통해 request에 해당하는 view 파일을 탐색 후 받아냄
받아낸 View 페이지 파일에 Model을 보낸 후 클라이언트에게 보낼 페이지를 완성시켜 받아냄
완성된 View 파일을 클라이언트에 response하여 화면에 출력
```
2. Spring의 큰 특징인 IoC에 대해 설명해주세요
```
  개발자가 필요한 객체 생성 로직을 구현하는 기존의 방식에서 벗어나, 객체 생성을 Container에게 위임해 처리하는 것  —> 결합도를 낮춰줌
```
3. DI의 종류 3가지를 말하고 각각의 장단점에 대해 말해주세요
```
Field Injection : 변수 선언부에 @ Autowired를 붙이는 방법으로 간단하지만 final을 선언할 수 없어서 객체가 변할 수 있다는 단점이 있음
Setter Injection : 주입이 필요한 객체가 주입되지 않아도 얼마든지 객체를 생성할 수 있어서 NullPointerException이 발생할 수 있음
Constructor Injection : Constructor에 @ Autowired Annotation을 붙여 의존성 주입을 받음, instance를 만들지 못하도록 강제할 수 있기 때문에 권장
```
4. SpringBootApplication의 역할에 대해 말해주세요
```
스프링 bean을 읽어들여와 자동으로 생성해줌
SpringBootApplication.run() 으로 클래스를 run하면 내장 WAS를 사용
```

#### 박상민
1. MVC 의 요청과 응답흐름에 대해서 설명해주세요
```
요청을 DispatcherServlet 을 통해 받아 Handler Mapping 을 통해 메서드의 위치를 찾고 Controller 로 이동한다.
Controller 에서 Service Dao 를 통해 비즈니스로직을 처리한 후 DispatcherServlet 으로 응답을 보내고 View Resolver 를 통해 응답을 위한 View 를 찾아 생성한 후 View 를 클라이언트에게 응답으로 보낸다.
```

1-1. Dispatcher Servlet 은 어떤 역할을 하나요?
```
- Client 에서 들어오는 Request 를 처리하는 중심 컨트롤러
- 서블릿 컨테이너에서 http 프로토콜을 통해 들어오는 모든 request 에 대해서 제일 앞단에서 중앙 집중식으로 처리해주는 핵심적인 역할
```
2. Bean 에서의 Scope 종류에 대해서 설명해주세요.
```
- Singleton → IoC 컨테이너에서 단 하나의 객체로만 존재
- prototype → 다수의 객체가 존재할 수 있음
- request → HTTP Request 의 라이프사이클에서 단 하나의 객체로만 존재
- session → HTTP Session 의 라이프 사이클에서 단 하나의 객체로만 존재
- global session → Global HTTP Session 의 라이프 라이클에서 단 하나의 객체로만 존재
```
3. AOP 란 무엇인지 설명하고 장점에 대해서 설명해주세요.
```
AOP 란 관점 지향 프로그래밍으로 어떤 로직을 기준으로 핵심적인 관점, 부가적인 관점으로 나누어서 보고 그 관점을 기준으로 각각 모듈화 하는 것이다. 
장점으로는 중복되는 코드들과 같이 흩어진 관심사를 한군데 모아 중복되는 로직을 비즈니스 로직에서 분리하여 재사용할 수 있다는 점이 있다.
```
#### 장시우
1. Spring MVC 진행 과정에 대해 설명해주세요.
```
클라이언트가 url을 요청하면, 웹 브라우저에서 스프링으로 request가 보내진다.
Dispatcher Servlet이 request를 받으면, Handler Mapping을 통해 해당 url을 담당하는 Controller를 탐색 후 찾아낸다.
찾아낸 Controller로 request를 보내주고, 보내주기 위해 필요한 Model을 구성한다.
Model에서는 페이지 처리에 필요한 정보들을 Database에 접근하여 쿼리문을 통해 가져온다.
데이터를 통해 얻은 Model 정보를 Controller에게 response 해주면, Controller는 이를 받아 Model을 완성시켜 Dispatcher Servlet에게 전달해준다.
Dispatcher Servlet은 View Resolver를 통해 request에 해당하는 view 파일을 탐색 후 받아낸다.
받아낸 View 페이지 파일에 Model을 보낸 후 클라이언트에게 보낼 페이지를 완성시켜 받아낸다.
완성된 View 파일을 클라이언트에 response하여 화면에 출력한다.
```
2. Spring과 Spring boot의 차이점에 대해 설명해주세요.
```
성능 차이가 아닌 설정의 간편함 차이입니다.
```
3. AOP에 대해 설명해주세요.
```
관점지향 프로그래밍으로 OOP에서 발전된 개념입니다.
공통 모듈을 따로 분리해 각 로직마다 끼워넣는 방식입니다.
```
