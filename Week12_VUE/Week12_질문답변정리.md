# Week 12 - 질문/답변 정리

#### 김빛누리

1. Vue 라이프사이클 간단히 설명

```
Creation
컴포넌트 초기화 단계
SSR 지원 O
가장 먼저 실행되며 아직 컴포넌트가 DOM에 추가되기 전

Mounting
DOM 삽입 단계
SSR 지원 X

Updating
렌더링 단계
컴포넌트에서 사용되는 반응형 속성들이 변경되거나 다시 렌더링되면 실행됨

Destruction
해체 단계
인스턴스가 소멸되기 직전에 호출
```

   - Vue에서 초기 백엔드 통신할 때 어느 단계에서?

      ```
      creation
      ```

   - 왜 creation에서 하는지?

      ```
      creation은 서버 렌더링에서도 지원되는 훅

      일반적으로 created는 데이터 초기화에 대한 목적, 
      mounted는 렌더링 이후 DOM 조작에 대한 목적으로 사용하므로 
      creation 에서 초기 백엔드 데이터 가져온다.
      ```

2. Vue에서 데이터 바인딩 방법

```
Mustache, v-on으로 기본적인 데이터 바인딩
v-model로 뷰와 모델의 데이터를 동기화하는 양방향 바인딩
```

  - v-on 디렉티브 역할?

    ```
    이벤트 핸들러 추가
    ```

3. methods computed 차이

```
method는 재 렌더링 할때마다 항상 메소드를 호출한다. 
하지만 computed 는 저장된 결과(캐싱)를 반환하므로 값이 변했을 경우에만 재 렌더링 한다. 
```

  - 이벤트 처리에서 어떤 함수를 사용?

    ```
    methods만 사용가능함
    ```

#### 김주영
1. Vue의 Life Cycle
1-1. Vue의 Life Cycle의 순서를 말해주세요
```
- create, mount, update, destruct의 순서를 따름
```
1-2. 그 중 Virtual Dom이 Rendering 되는 때는 언제인가요?
```
- mount
```
1-3. Virtual Dom의 동작 순서나 원리에 대해 아는 대로 말씀해주세요
```
- UI가 변경되면 전체 UI를 Virtual DOM으로 렌더링 합니다
- 현재 Virtual DOM과 이전의 Virtual DOM을 비교해 차이를 계산합니다
- 이렇게 변경된 부분을 실제 DOM에 반영합니다
```
1-4. 위와 같은 과정은 어떤 문제를 해결하기 위한 방법인가요?
```
- SPA의 특징으로 DOM 복잡도 증가에 따른 최적화 및 유지 보수가 어려워지는 문제를 해결하기 위해
```
2. directive 
2-1. v-if, v-show 의 차이점에 대해 설명해주세요
```
- v-if는 false로 설정 되어 있을 때 아예 사라지지만 v-show는 false일 때 display:none과 같이 크기는 차지한 채로 hide 됨
```
2-2. data-binding 기법 중 양방향 모델에 어떤 것이 있는지 말하고 이에 대해 설명해주세요
```
- v-model 
- v-bind와 v-on을 합친 방법으로 뷰 인스턴스의 데이터 속성을 해당 html 요소에 연결하고, html요소를 뷰 인스턴스의 로직과 연결하는 것
```
2-3. preventDefault (), stopPropagation()의 차이점에 대해 설명해주세요
```
- preventDefault는 기본으로 정의된 이벤트를 작성하지 못하게 하는 메서드
- propagation은 말 그대로 상위 엘레멘트로 이벤트가 전파되는 이벤트 버블링을 막는 방법
```
2-4. method, computed, watch 중 컴포넌트가 다시 렌더링 될 때 리렌더링 되는 것은?
```
- method, watch
```
2-5. 데이터가 변화할 때 감지되는 것은?
```
- computed, watch
```
#### 박상민
1. Vue 의 라이프 사이클은 크게 4가지로 나눠지는데 그 중 Updating은 언제 호출되고 어떤 상황에서 사용되는지 예를 들어 설명해주세요.
```
    - Updating은 랜더링 단계
    - 컴포넌트의 데이터가 변할 때 실행된다.
    - beforeUpdate 와 updated 로 나눠서 호출이 되며 Update 가 되어 돔이 재 랜더링 된 이전과 이후를 구분하여 프로세스를 처리할 수 있음
``` 
2. Computed 와 watch 의 차이점은 어떤 것이 있나요
``` 
    - computed 는 return이 필수
    - computed 는 선언형이고 watch는 명령형 프로그래밍 방식
    - 데이터의 변경의 응답으로 비동기식 계산이 필요한 경우, 시간이 많이 소요되는 과정을 거칠 때에는 watch 를 사용하는 것이 좋음
``` 
3. Firebase 란 무엇인가요
``` 
    - 웹 애플리케이션 개발 플랫폼
    - 반복되는 백앤드 구축을 클라우드 형태로 제공하는 서비스
    - 백앤드에 대해 신경쓰지않고 프론트개발에만 전념할 수 있음
``` 
#### 장시우

1. Vue 의 라이프 사이클 4가지는 무엇인지 말하고 각각 설명해주세요.
```
Creation
컴포넌트 초기화 단계

Creation 단계에서 실행되는 훅(hook)들이 라이프사이클 중 가장 먼저 실행됨
아직 컴포넌트가 DOM에 추가되기 전이며 서버 렌더링에서도 지원되는 훅임
클라이언트와 서버 렌더링 모두에서 처리해야 할 일이 있으면, 이 단계에 적용하자

#beforeCreate
가장 먼저 실행되는 훅
아직 데이터나 이벤트가 세팅되지 않은 시점이므로 접근 불가능

#created
데이터, 이벤트가 활성화되어 접근이 가능함
하지만 아직 템플릿과 virtual DOM은 마운트 및 렌더링 되지 않은 상태임

#Mounting
DOM 삽입 단계
초기 렌더링 직전 컴포넌트에 직접 접근이 가능하다.
컴포넌트 초기에 세팅되어야할 데이터들은 created에서 사용하는 것이 나음


#beforeMount
템플릿이나 렌더 함수들이 컴파일된 후에 첫 렌더링이 일어나기 직전에 실행됨

많이 사용하지 않음

#mounted
컴포넌트, 템플릿, 렌더링된 DOM에 접근이 가능함
모든 화면이 렌더링 된 후에 실행

#주의할 점
부모와 자식 관계의 컴포넌트에서 생각한 순서대로 mounted가 발생하지 않는다. 즉, 부모의 mounted가 자식의 mounted보다 먼저 실행되지 않음
부모는 자식의 mounted 훅이 끝날 때까지 기다림


#Updating
렌더링 단계
컴포넌트에서 사용되는 반응형 속성들이 변경되거나 다시 렌더링되면 실행됨
디버깅을 위해 컴포넌트가 다시 렌더링되는 시점을 알고 싶을때 사용 가능


#beforeUpdate
컴포넌트의 데이터가 변하여 업데이트 사이클이 시작될 때 실행됨
(돔이 재 렌더링되고 패치되기 직전 상태)

#updated
컴포넌트의 데이터가 변하여 다시 렌더링된 이후에 실행됨
업데이트가 완료된 상태이므로, DOM 종속적인 연산이 가능
```
2. computed는 왜 사용하는가?
```
computed를 한마디로 얘기하자면 “반응형 getter”이다. 
```
3. watch는 왜 사용하는가?
```
변경을 감시(watch)한다는 점 때문에 computed와 watch를 혼동할 수 있다.걱정할 필요는 없다. 
computed에 비해 watch는 단순하고 이해하기 쉽기 때문이다. watch는 Vue 인스턴스의 특정 프로퍼티가 변경될때 지정한 콜백함수가 실행되는 기능이다.
```
