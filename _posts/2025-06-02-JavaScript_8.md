---
layout: single
title: "[JavaScript]비동기 처리 ① 콜백함수와 콜백지옥"
categories: JavaScript
tag: [JavaScript, 콜백함수, 콜백지옥]
date: 2025-06-02
published: true
toc: true # 목차 생성
author_profile: true # 사용자 프로필
search: true # false로 설정하면 검색시 내용이 뜨지 않는다.
---

# 자바스크립트 비동기 처리 ① - 콜백 함수와 콜백 지옥

자바스크립트는 기본적으로 **동기(Synchronous)** 언어이지만, 실무에서는 네트워크 요청, 타이머, 사용자 이벤트 등 **비동기(Asynchronous)** 작업이 매우 많습니다.  
이런 비동기 작업을 처리하는 가장 기본적인 방법이 **콜백 함수(callback function)**입니다.

---

## ✅ 콜백 함수란?

> 다른 함수의 **인수로 전달되는 함수**이며,  
> 보통 비동기 작업이 끝난 후 실행될 **"결과 처리 함수"**로 자주 사용됩니다.

### 📌 기본 예제: 비동기 덧셈 함수

```js
function add(a, b, callback) {
  setTimeout(() => {
    const sum = a + b;
    callback(sum);
  }, 3000);
}

add(1, 2, (value) => {
  console.log(value); // 3초 뒤에 3 출력
});
```

- `setTimeout()`은 대표적인 **비동기 함수**
- `callback(sum)`은 작업이 끝난 뒤 결과를 전달받는 함수

---

## 🍜 예제: 음식을 준비하는 시나리오

> 음식 준비 → 식히기 → 냉동하기  
> 이 모든 과정을 비동기 함수로 구현하면 어떻게 될까요?

```js
function orderFood(callback) {
  setTimeout(() => {
    const food = "떡볶이";
    callback(food);
  }, 3000);
}

function cooldownFood(food, callback) {
  setTimeout(() => {
    const cooldownedFood = `식은 ${food}`;
    callback(cooldownedFood);
  }, 2000);
}

function freezeFood(food, callback) {
  setTimeout(() => {
    const freezedFood = `냉동된 ${food}`;
    callback(freezedFood);
  }, 1500);
}
```

### 실행 흐름

```js
orderFood((food) => {
  console.log(food); // 떡볶이

  cooldownFood(food, (cooldownedFood) => {
    console.log(cooldownedFood); // 식은 떡볶이

    freezeFood(cooldownedFood, (freezedFood) => {
      console.log(freezedFood); // 냉동된 식은 떡볶이
    });
  });
});
```

- **이전 단계의 결과를 다음 단계의 인자로 전달**하면서 비동기 흐름을 유지
- 순차적 처리가 가능하긴 하지만…

---

## 😵 콜백 지옥(Callback Hell)이란?

이처럼 콜백 안에 또 콜백을 넣는 구조가 반복되면…

```js
orderFood((food) => {
  cooldownFood(food, (cooldownedFood) => {
    freezeFood(cooldownedFood, (freezedFood) => {
      doSomething(freezedFood, (result) => {
        doNext(result, (next) => {
          // ...
        });
      });
    });
  });
});
```

- **들여쓰기가 계속 깊어짐**
- 코드 흐름 파악이 어려워짐
- 디버깅/에러 처리도 복잡해짐

> 이러한 구조를 **콜백 지옥(Callback Hell)** 이라고 부릅니다.

---

## 💡 해결책: `Promise`, `async/await`

콜백 지옥을 해결하고, 가독성 좋고 체계적인 코드 작성을 가능하게 해주는 방법이 바로:

- `Promise` 객체
- `async/await` 문법

이 두 가지는 이후 포스팅에서 자세히 다룰 예정입니다. 👀

---

## ✍️ 마무리 정리

| 개념 | 설명 |
|------|------|
| 콜백 함수 | 비동기 작업이 끝난 후 호출되는 함수 |
| 장점 | 간단한 비동기 작업에 사용하기 쉬움 |
| 단점 | 콜백 안에 콜백이 중첩되며 가독성/유지보수성 저하 |
| 해결책 | `Promise`, `async/await` 활용 |

---

## 📘 느낀 점

콜백 함수는 비동기 처리를 이해하는 **첫 번째 열쇠**라고 느꼈습니다.  
콜백 지옥을 직접 작성해보니, 나중에 왜 `Promise`나 `async/await`가 필요한지도 자연스럽게 이해할 수 있을 것 같아요.
