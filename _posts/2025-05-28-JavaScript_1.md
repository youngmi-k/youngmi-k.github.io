---
layout: single
title: "[JavaScript]자바스크립트에서 배열과 객체를 순회하는 방법"
categories: JavaScript
tag: [JavaScript]
date: 2025-05-28
published: true
toc: true # 목차 생성
author_profile: true # 사용자 프로필
search: true # false로 설정하면 검색시 내용이 뜨지 않는다.
---

# 자바스크립트에서 배열과 객체를 순회하는 모든 방법 정리

프론트엔드 개발을 하다 보면 **배열과 객체를 반복문으로 순회**하는 경우가 정말 많습니다.  
React에서 컴포넌트를 `.map()`으로 렌더링할 때도, 객체 데이터를 파싱할 때도 마찬가지죠.

이번 글에서는 **자바스크립트에서 배열과 객체를 순회하는 여러 가지 방법**을 정리해보겠습니다.  
예제와 함께 간단하게 비교해볼게요.

---

## 🔁 배열 순회 방법

### 1. `for` 루프 (기본 방식)
```js
const arr = [1, 2, 3];
for (let i = 0; i < arr.length; i++) {
  console.log(arr[i]);
}
```
- 가장 기본적인 방식  
- 인덱스 사용 가능

---

### 2. `for...of`
```js
for (let value of arr) {
  console.log(value);
}
```
- 배열의 값을 하나씩 순회  
- 가독성이 좋아 자주 사용됨

---

### 3. `forEach`
```js
arr.forEach((value, index) => {
  console.log(index, value);
});
```
- 배열 전용 메서드  
- 리턴값 없음 (단순 반복에 적합)

---

### 4. `map`
```js
const doubled = arr.map(num => num * 2);
console.log(doubled); // [2, 4, 6]
```
- **새로운 배열을 반환**  
- 변환이 목적일 때 사용

---

## 🧭 객체 순회 방법

### 1. `for...in`
```js
const obj = { a: 1, b: 2 };
for (let key in obj) {
  console.log(key, obj[key]);
}
```
- 객체의 key를 순회  
- prototype까지 순회하므로 주의 필요

---

### 2. `Object.keys()`
```js
Object.keys(obj).forEach(key => {
  console.log(key, obj[key]);
});
```
- key만 배열로 추출해서 순회

---

### 3. `Object.entries()`
```js
for (let [key, value] of Object.entries(obj)) {
  console.log(key, value);
}
```
- key와 value를 동시에 배열로 가져와 순회  
- 구조분해 할당과 함께 사용하면 깔끔

---

## 🧩 어떤 상황에서 뭘 써야 할까?

| 상황 | 추천 방식 |
|------|-----------|
| 배열 요소 순회만 필요할 때 | `for...of`, `forEach` |
| 배열을 변환해서 새로운 배열 만들고 싶을 때 | `map` |
| 객체의 키, 값 모두 필요할 때 | `Object.entries()` |
| 객체 키만 필요할 때 | `Object.keys()` |
| 복잡한 반복이 필요할 때 | `for`, `for...in` |

---

## ✍️ 마무리

배열과 객체 순회는 자바스크립트를 다룰 때 꼭 알아야 할 **기초 중의 기초**입니다.  
상황에 따라 알맞은 반복문을 선택하면 **코드 가독성**과 **유지보수성**이 훨씬 높아집니다.
