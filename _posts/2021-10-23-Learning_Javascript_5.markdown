---
layout: post
title:  "-Learning Javascript 5"
date:   2021-10-23 22:30:00 +0900
categories: javascript
tags: [javascript, language, web]
---
# Javascript 알아보기 5

Javascript에 대해 공부하고 알게 된 내용을 정리한 페이지입니다. 편의상 JS로 줄여 부르겠습니다.

[[_TOC_]]

## 1. JS와 HTML의 연결

- js는 html의 요소를 가지고 올 수 있는 기본 함수들을 제공합니다.

### 1. Document object

- document는 js에서 바로 사용할 수 있는 객체입니다.

- js가 연결되어 있는 html 파일에 대한 정보를 갖고 있습니다.

- document의 하위 함수로써, html문서의 여러 항목들을 가져올 수 있는 함수들은 다음과 같습니다.

  - getElementsByClassName("classname")
    - classname이라는 클래스를 가진 html항목을 모두 찾아준 뒤 항목들의 배열을 반환합니다.
  - getElementsByTagName("tag")
    - tag 태그에 해당하는 html항목을 모두 찾아준 뒤 항목들의 배열을 반환합니다.
  - querySelector("css selector")
    - css selector에 해당하는 html 항목을 가져옵니다.
    - 여러 개의 후보가 있더라도 가장 먼저 찾은 항목을 가져옵니다.
  - querySelectorAll("css selector")
    - css selector에 해당하는 html 항목을 전부 가져옵니다.
  - gelElementById("hello")
    - hello라는 id에 해당하는 html항목을 가져옵니다.
    - 하나만 가져옵니다. (Id는 유일해야 하기 때문에)

- html항목을 가져오는 예시

  - ```js
    const title = document.getElementById("title")
    ```

### 2. Event

- 웹에서 어떤 사건이 발생하면 event가 발생합니다.

- event는 변화가 발생한 모든 상황을 가리킵니다.

- js는 이러한 event를 추적할 수 있는 함수들을 제공합니다. (이를 바인딩이라고 합니다.)

- component.addEventListener("something", function)

  - 불러온 html항목 component의 하위 함수
  - component에 발생한 something에 해당하는 event가 발생했을 때 function 함수를 실행합니다.
  - 발생하는 event 목록은 console.dir()을 사용하여 확인할 수 있습니다.
    - 항목의 목록 중 on+eventname로 이름붙은 항목들이 event들입니다.
    - addEventListener에 적용할 때는 on은 빼고 eventname만 적습니다.

- event에 함수를 바인딩하는 또다른 방법

  - ```js
    component.onevent = function;
    ```

- event의 목록은 [여기](https://developer.mozilla.org/ko/docs/Web/Events)에서 확인할 수 있습니다.
