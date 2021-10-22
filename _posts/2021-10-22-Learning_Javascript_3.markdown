---
layout: post
title:  "-Learning Javascript 3"
date:   2021-10-22 22:30:00 +0900
categories: javascript
tags: [javascript, language, web]
---
# Javascript 알아보기 3

Javascript에 대해 공부하고 알게 된 내용을 정리한 페이지입니다. 편의상 JS로 줄여 부르겠습니다.

[[_TOC_]]

## 1. Javascript의 구성 요소(이어서)

- 지난 포스팅에서 JS의 구성요소 중 변수와 배열에 대해 알아보았습니다.
- 이어서...

### 1. Objects (객체)

- 배열을 사용할 경우 여러 변수를 동시에 다룰 수 있지만, 배열의 각 항목이 어떤 의미를 갖는지 그 배열만으로는 알 수가 없습니다.

- 그래서 사용해서 좀 더 변수들에게 의미부여를 할 수 있는 형태로 object를 사용합니다.

- 객체의 정의는 다음과 같이 할 수 있습니다.

  ```js
  const object = {
      name1: value1,
      name2: value2,
      ...
  }
  ```

- 만들어진 객체의 변수들은 다음과 같이 확인할 수 있습니다.

  ```js
  console.log(object.name1)
  ```

  console.log는 console화면에 내용을 출력하는 함수입니다.

- 이렇게 만들어진 변수는, 변수의 이름을 보고 그 의도를 짐작할 수 있습니다.

- 객체도 배열과 마찬가지로 변수를 추가하고, 삭제하는 것이 가능합니다.

### 2. Function(함수)

- 함수란

  - 반복적으로 사용하는 코드의 조각입니다.

- 함수는 다음과 같이 정의합니다.

  ```js
  function func(arguement) {
      ...
  }
  ```

  - arguments위치에 사용할 데이터가 전해집니다.

  - 함수에 전해지는 arguments는 함수 밖에서는 존재하지 않습니다.

  - object 안에 함수를 정의하는 것이 가능합니다.

    ```js
    const object {
        function func(something) {
            blabla
        }
    }
    ```

    이 경우 object의 함수를 부를 떄에는 object.func() 형태로 부릅니다.

#### 1. Return(반환)

- 함수에서 값을 얻고 싶을 때 사용합니다.

- 이렇게 얻은 값은 변수에 저장 가능합니다.

- 함수에서 반환된 값을 얻기 위해서는 다음과 같이 작성하면 됩니다.

  ```js
  const variable = func()
  ```

  이 때 함수 func의 반환값이 변수 variable에 저장됩니다.

### 3. 조건문

- if

  - 다른 언어의 조건문과 유사합니다.

  - ```js
    if(condition){
        // condition == true
    } else if(condition2){
        // condition == false
        // condition2 == true
    } else {
        // 모든 조건이 다 false이면
    }
    ```

- AND 표기법

  - &&

- OR 표기법

  - ||

- EQUAL 표기법

  - ===

- NOT EQUAL 표기법

  - !==

