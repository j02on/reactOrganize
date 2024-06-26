# 01. 리액트는 어쩌다 만들어졌을까?

소유자: 지연 박
생성 일시: 2024년 6월 13일 오전 8:34

## JavaScript를 사용할 때

---

<aside>
💡 **javascript를 사용**하여 UI를 제어할 땐, DOM을 변형시키기 위해 브라우저의 DOM Selector API를 사용해 특정 DOM을 선택 후 특정 이벤트가 발생하면 변화를 주도록 설정해야한다.

</aside>

HTML이 구성되어 있고, id를 사용해 각 DOM을 선택한 뒤, 원하는 이벤트가 발생하면 DOM의 특정 속성을 바꾸어주어야 한다.

사용자와의 인터랙션이 별로 없는 웹페이지라면 상관없겠지만, 인터랙션이 자주 발생하고, 이에 따라 동적으로 UI를 표현해야된다면, 규칙들이 다양해질 것이고 관리하기도 어려워질 것이다.

**`코드형태`**

![Untitled](01%20%E1%84%85%E1%85%B5%E1%84%8B%E1%85%A2%E1%86%A8%E1%84%90%E1%85%B3%E1%84%82%E1%85%B3%E1%86%AB%20%E1%84%8B%E1%85%A5%E1%84%8D%E1%85%A5%E1%84%83%E1%85%A1%20%E1%84%86%E1%85%A1%E1%86%AB%E1%84%83%E1%85%B3%E1%86%AF%E1%84%8B%E1%85%A5%E1%84%8C%E1%85%A7%E1%86%BB%E1%84%8B%E1%85%B3%E1%86%AF%E1%84%81%E1%85%A1%20e4ec68e0bcba49f69bd8de48efe5c85e/Untitled.png)

> 처리해야 할 이벤트, 관리해야 할 상태값, DOM도 다양해지게 된다면, 이에 따라 업데이트르르 하는 규칙도 복잡해지기 때문에, 이렇게 코드가 복잡한 형태로 바뀌게 된다.
> 

<aside>
💡 그래서 Ember, Backbone, Angular JS 등의 프레임워크가 만들어졌었는데, 이 프레임워크들은 JS의 특정 값이 바뀌면 특정 DOM의 속성이 바뀌도록 연결해 주어서 업데이트하는 작업을 간소화해주는 방식으로 웹개발 어려움을 해결해주었다.

</aside>

## 그렇다면 react는?

---

<aside>
💡 react는 어떠한 상태가 바뀌었을 때, 그 상태에 따라 DOM을 어떻게 업데이트  할 지 규칙을 정하는 것이 아니라, 아예 날려버리고 처음부터 모든걸 새로 만들어서 보여준다면 어떨까?라는 아이디어에서 개발이 시작됐다.

</aside>

> 정말로 동적인 UI를 보여주기 위해서 모든걸 다 날려버리고 모든걸 새로 만들게 된다면, 속도가 느릴 것이다. 하지만, react에서는 Virtual DOM을 이용해 이를 가능하게 했다.
> 

## Virtual DOM이란?

---

<aside>
💡 **가상의 DOM**
브라우저에 실제로 보여지는 DOM이 아니라 그냥 메모리에 가상으로 존재하는 DOM으로서 그냥 javascript 객체이기 때문에 작동 성능이 실제로 브라우저에서 DOM을 보여주는 것보다 속도가 훨씬 빠르다.

</aside>

> react는 상태가 업데이트 되면, 업데이트가 필요한 곳의 UI를 Virtual DOM을 통해서 렌더링합니다. 그리고 나서 react 개발팀이 만든 매우 효율적인 비교 알고리즘을 통해 실제 브라우저에 보여지고 있는 DOM과 비교를 한 후, 차이가 있는 곳을 감지해 이를 실제 DOM에 패치시켜준다.
>