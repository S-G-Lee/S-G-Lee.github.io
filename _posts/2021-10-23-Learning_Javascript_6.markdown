---
layout: post
title:  "-Learning Javascript 6"
date:   2021-10-23 22:30:00 +0900
categories: javascript
tags: [javascript, language, web]
---
# Javascript 알아보기 6

Javascript에 대해 공부하고 알게 된 내용을 정리한 페이지입니다. 편의상 JS로 줄여 부르겠습니다.

[[_TOC_]]

## 1. JS와 CSS

- html에 연결된 css 요소 역시 js로 변경할 수 있습니다.

  - 예시) h1의 color속성을 변경할 경우

  - 

    ```js
    const h1 = document.querySelector("h1");
    h1.style.color = "red";
    ```

  - color뿐만 아니라 style에 해당하는 다양한 요소를 불러오고 바꿀 수 있습니다.

  - 하지만 이렇게 css요소를 직접 바꾸는 것은 좋지 않습니다.

## 2. Class를 통한 CSS 적용

- css는 일반적으로 class의 형태로 html에 적용되기 때문에, 이를 이용하여 js에 css항목을 불러올 때 해당 css가 들어있는 class를 불러오면 됩니다.

- className을 이용한 css 적용

  - 상황

    ```css
    /* style.css */
    .clicked {
      color: red;
    }
    ```

    ```js
    // js file
    const h1 = document.querySelector("h1")
    function handleTitleClick() {
      if(h1.className === "clicked") {
        h1.className = "";
      } else {
        h1.className = "clicked";
      }
    }
    
    h1.addEventListener("click", handleTitleClick);
    ```

  - css에 정의되어 있는 `.clicked` 선택자를 적용시키고 해제하는 것을 통해 html 에 적용되는 css 요소를 제어합니다.

  - 위의 예시는 h1 문자열을 클릭할 때마다 바인딩된 함수를 수행합니다.

  - h1.className을 조회해 clicked 클래스를 가지고 있다면 지우고, 가지고 있지 않다면 추가합니다.

  - 이로써 `.clicked`에 해당하는 css요소를 적용/해제할 수 있습니다.

  - 하지만 이 경우 html을 통해 직접 삽입된 class들은 싸그리 무시됩니다.

- h1.classList.contains(clickedClass)

  - 상황

    ```js
    function handleTitleClick() {
      const clickedClass = "clicked";
      if(h1.classList.contains(clickedClass)) {
        h1.classList.remove(clickedClass);
      } else {
        h1.classList.add(clickedClass);
      }
    }
    ```

  - h1.classList는 h1이 갖고 있는 모든 클래스의 배열을 불러옵니다.

  - h1.classList.contains(clickedClass)

    - h1가 가진 클래스 중에 clickedClass가 존재하는지 확인합니다. 존재한다면 true를, 없다면 false를 반환합니다.

  - h1.classList.add(clickedClass)

    - h1에 clickedClass를 추가합니다.

  - h1.classList.remove(clickedClass)

    - h1에 clickedClass를 제거합니다.

- h1.classList.toggle("clicked")

  - clicked 클래스가 h1에 없다면 추가하고 있다면 제거합니다.

  - 이를 이용하면 위의 코드는 다음 코드로 대체 가능합니다.

  - ```js
    function handleTitleClick() {
      h1.classList.toggle("clicked");
    }
    ```

