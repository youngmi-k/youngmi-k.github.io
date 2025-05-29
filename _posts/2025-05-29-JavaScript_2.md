---
layout: single
title: "[JavaScript]자바스크립트 배열 조작 메서드 6가지 정리"
categories: JavaScript
tag: [JavaScript, 배열, 프론트엔드입]
date: 2025-05-28
published: true
toc: true # 목차 생성
author_profile: true # 사용자 프로필
search: true # false로 설정하면 검색시 내용이 뜨지 않는다.
---

# 자바스크립트 배열 조작 메서드 6가지 정리 ✂️

이번 글에서는 **자바스크립트 배열(Array)을 조작하는 대표적인 6가지 메서드**를 간단한 예제와 함께 정리해보겠습니다.  
리액트나 일반 자바스크립트 프로젝트를 할 때 배열 조작은 정말 자주 쓰이기 때문에,  
미리 익혀두면 코드를 더 효율적으로 다룰 수 있어요!

---

## ✅ 1. `push()`

**역할**: 배열의 맨 뒤에 새로운 요소를 추가하고, 변경된 배열의 길이를 반환  
```js
let arr1 = [1, 2, 3];
const newLength = arr1.push(4, 5, 6, 7); 
console.log(arr1); // [1, 2, 3, 4, 5, 6, 7]
console.log(newLength); // 7
```

---

## ✅ 2. `pop()`

**역할**: 배열의 맨 뒤 요소를 제거하고, 제거된 값을 반환  
```js
let arr2 = [1, 2, 3];
const poppedItem = arr2.pop();
console.log(arr2); // [1, 2]
console.log(poppedItem); // 3
```

---

## ✅ 3. `shift()`

**역할**: 배열의 맨 앞 요소를 제거하고, 제거된 값을 반환  
```js
let arr3 = [1, 2, 3];
const shiftedItem = arr3.shift();
console.log(arr3); // [2, 3]
console.log(shiftedItem); // 1
```

---

## ✅ 4. `unshift()`

**역할**: 배열의 맨 앞에 새로운 요소를 추가하고, 변경된 배열의 길이를 반환  
```js
let arr4 = [1, 2, 3];
const newLength2 = arr4.unshift(0);
console.log(arr4); // [0, 1, 2, 3]
console.log(newLength2); // 4
```

> 📌 참고: `shift()`와 `unshift()`는 `push()`나 `pop()`보다 성능이 느린 편입니다.

---

## ✂️ 5. `slice()`

**역할**: 배열의 일부를 잘라내어 **새로운 배열**로 반환  
> 원본 배열은 변경되지 않음  

```js
let arr5 = [1, 2, 3, 4, 5];

let sliced = arr5.slice(2, 5);  // [3, 4, 5]
let sliced2 = arr5.slice(2);   // [3, 4, 5]
let sliced3 = arr5.slice(-3);  // [3, 4, 5]

console.log(sliced, sliced2, sliced3);
```

---

## 🔗 6. `concat()`

**역할**: 두 배열을 합쳐서 **새로운 배열**을 반환  
```js
let arr6 = [1, 2];
let arr7 = [3, 4];
let concatedArr = arr6.concat(arr7);

console.log(concatedArr); // [1, 2, 3, 4]
```

---

## 💡 마무리 요약

| 메서드 | 역할 | 원본 변경 여부 |
|--------|------|----------------|
| `push` | 뒤에 추가 | O |
| `pop` | 뒤에서 제거 | O |
| `shift` | 앞에서 제거 | O |
| `unshift` | 앞에 추가 | O |
| `slice` | 잘라서 새 배열 반환 | ❌ |
| `concat` | 배열 합치기 | ❌ |

---

배열 조작은 **자바스크립트 개발의 기본기 중 핵심**입니다.  
이 6가지 메서드를 잘 이해하고 활용하면, 실무에서도 훨씬 효율적으로 코드를 다룰 수 있어요.

---

> ✍️ 블로그 주인장의 한 마디:  
> 오늘 공부한 내용을 이렇게 정리해두면 나중에 정말 큰 자산이 됩니다!  
