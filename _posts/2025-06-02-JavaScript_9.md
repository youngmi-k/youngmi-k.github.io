---
layout: single
title: "[JavaScript]비동기 처리 ② - Promise"
categories: JavaScript
tag: [JavaScript, Promise]
date: 2025-06-02
published: true
toc: true # 목차 생성
author_profile: true # 사용자 프로필
search: true # false로 설정하면 검색시 내용이 뜨지 않는다.
---

# 자바스크립트 비동기 처리 ② - Promise 완벽 정리 💡

이전 글에서 콜백 함수를 사용한 비동기 처리를 살펴봤습니다.  
하지만 콜백이 중첩되다 보면 **"콜백 지옥(Callback Hell)"**에 빠지기 쉽습니다.  
이를 해결하기 위해 등장한 것이 바로 **Promise**입니다.

---

## ✅ Promise란?

> **비동기 작업을 효율적으로 처리할 수 있게 도와주는 자바스크립트의 내장 객체**

### ✔️ 특징

- 비동기 작업의 **상태와 결과**를 추상화한 객체
- 다음 3가지 상태(state)를 가집니다:

| 상태 | 설명 |
|------|------|
| `Pending` (대기) | 작업이 아직 완료되지 않음 |
| `Fulfilled` (성공) | 작업이 성공적으로 완료됨 |
| `Rejected` (실패) | 작업이 실패함 |

> `resolve()`를 호출하면 성공, `reject()`를 호출하면 실패 상태로 바뀝니다.

---

## 🛠️ 기본 예제

```js
const promise = new Promise((resolve, reject) => {
  setTimeout(() => {
    console.log("안녕");
    resolve("안녕");
    // reject("에러 발생");
  }, 2000);
});
```

### 상태 확인

```js
setTimeout(() => {
  console.log(promise); // [[PromiseState]]: "fulfilled"
}, 3000);
```

---

## ✅ Promise 사용 방법: `.then()`과 `.catch()`

```js
const promise = new Promise((resolve, reject) => {
  setTimeout(() => {
    const num = 10;
    if (typeof num === "number") {
      resolve(num + 10);
    } else {
      reject("num이 숫자가 아닙니다.");
    }
  }, 2000);
});

promise
  .then((value) => {
    console.log("성공:", value);
  })
  .catch((error) => {
    console.log("실패:", error);
  });
```

- `.then()` → 성공 시 호출
- `.catch()` → 실패 시 호출

---

## 🔁 Promise Chaining

Promise는 `.then()`이나 `.catch()`를 호출하면 **다시 Promise 객체를 반환**합니다.  
따라서 연속적으로 이어붙이는 **체이닝(Chaining)**이 가능합니다.

### ❌ 잘못된 방식 (콜백 지옥 재현)

```js
const p = add10(0);
p.then((result) => {
  console.log(result);
  add10(result).then((result2) => {
    console.log(result2);
  });
});
```

- 중첩이 생겨 가독성이 떨어짐

---

### ✅ 올바른 체이닝 방식

```js
add10(0)
  .then((result) => {
    console.log(result);
    return add10(result);
  })
  .then((result2) => {
    console.log(result2);
  })
  .catch((error) => {
    console.log("에러:", error);
  });
```

- `.then()`에서 반환한 Promise가 다음 `.then()`으로 전달됨
- 코드 가독성 상승 + 예외 처리를 `.catch()` 하나로 처리 가능

---

## 📦 실용 예제: `add10()` 함수

```js
function add10(num) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      if (typeof num === "number") {
        resolve(num + 10);
      } else {
        reject("num이 숫자가 아닙니다.");
      }
    }, 2000);
  });
}
```

---

## 🔍 Promise의 장점 요약

| 항목 | 콜백 함수 | Promise |
|------|------------|---------|
| 가독성 | 중첩됨 (지옥) | 체이닝 가능 |
| 에러 처리 | 각 콜백마다 try/catch 필요 | `.catch()` 한 번에 가능 |
| 확장성 | 제한적 | 체계적 연결 가능 |

---

## 📌 정리

- `Promise`는 **비동기 로직을 더 예측 가능하고, 읽기 쉬운 방식으로 관리**할 수 있게 해주는 도구입니다.
- 실제 API 통신, 파일 로딩, 서버 요청 등에서 자주 사용됩니다.
- 다음 단계로 `async/await` 문법까지 배우면 더 직관적인 코드 작성이 가능합니다.

---

## ✍️ 느낀 점

처음에는 `Promise`가 복잡하게 느껴졌지만, 실제로 `콜백 지옥`을 피하고  
비동기 흐름을 예쁘게 구성하는 데 필수라는 걸 깨달았습니다.  
다음에는 `async/await`로 변환하는 방법을 연습해봐야겠어요!
