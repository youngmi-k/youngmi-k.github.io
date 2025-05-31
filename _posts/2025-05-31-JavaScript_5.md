---
layout: single
title: "[JavaScript]배열 변형 메서드"
categories: JavaScript
tag: [JavaScript, 배열]
date: 2025-05-31
published: true
toc: true # 목차 생성
author_profile: true # 사용자 프로필
search: true # false로 설정하면 검색시 내용이 뜨지 않는다.
---

# 자바스크립트 배열 변형 메서드 5가지 완벽 정리

이번 글에서는 자바스크립트에서 배열을 조작하고 변형할 때 가장 자주 사용되는 메서드 5가지를 정리해봅니다.  
**`filter`, `map`, `sort`, `toSorted`, `join`** — 이 5가지 메서드를 이해하고 자유롭게 사용할 수 있다면, 자바스크립트 배열은 거의 정복했다고 해도 과언이 아닙니다!

---

## ✅ 1. `filter()`

> **조건을 만족하는 요소만 추출하여 새로운 배열로 반환**합니다.

```js
let arr1 = [
  { name: "Satomi", hobby: "피아노" },
  { name: "홍길동1", hobby: "피아노" },
  { name: "홍길동2", hobby: "독서" },
];

const pianoPeople = arr1.filter((item) => item.hobby === "피아노");
console.log(pianoPeople);
```

- `filter()`는 **조건을 만족하는 요소들만 추출**할 때 유용
- **원본 배열은 변경되지 않음**

---

## ✅ 2. `map()`

> **배열의 각 요소를 변환하여, 변환된 값을 담은 새로운 배열을 반환**합니다.

```js
let arr2 = [1, 2, 3];
const doubled = arr2.map((item) => item * 2);
console.log(doubled); // [2, 4, 6]
```

```js
const names = arr1.map((item) => item.name);
console.log(names); // ["Satomi", "홍길동1", "홍길동2"]
```

- `map()`은 **값을 변경하거나 가공할 때 가장 유용한 메서드**
- 항상 **새로운 배열을 반환**

---

## ✅ 3. `sort()`

> **배열의 요소를 정렬**합니다.  
> 기본적으로는 **사전순(문자열 기준)**으로 정렬됩니다.

```js
let arr3 = ["b", "a", "c"];
arr3.sort();
console.log(arr3); // ["a", "b", "c"]
```

#### 🧠 숫자 정렬 시 주의

`sort()`는 숫자도 문자열처럼 비교하므로, 숫자 비교 시 콜백 함수를 사용해야 합니다.

```js
arr3 = [10, 3, 5];
arr3.sort((a, b) => a - b); // 오름차순
console.log(arr3); // [3, 5, 10]
```

- 내림차순 정렬: `b - a`
- 원본 배열이 **직접 변경**됩니다 (주의!)

---

## ✅ 4. `toSorted()` (🆕 ES2023)

> `sort()`와 기능은 같지만, **원본 배열을 변경하지 않고 정렬된 새 배열을 반환**합니다.

```js
let arr4 = ["c", "a", "b"];
const sorted = arr4.toSorted();
console.log(arr4); // ["c", "a", "b"]
console.log(sorted); // ["a", "b", "c"]
```

- `sort()`의 **불변성 문제**를 해결해준 최신 메서드
- 원본 배열 유지가 필요한 경우 적극 활용하세요!

---

## ✅ 5. `join()`

> 배열의 요소들을 **하나의 문자열로 합쳐서 반환**합니다.

```js
let arr5 = ["hi", "im", "Satomi"];
const joined = arr5.join();
console.log(joined); // "hi,im,Satomi"
```

- 기본 구분자는 콤마(,)
- 다른 구분자도 지정 가능:

```js
console.log(arr5.join(" ")); // "hi im Satomi"
console.log(arr5.join("-")); // "hi-im-Satomi"
```

- 데이터 출력, 태그 묶기, 문자열 가공에 매우 유용

---

## ✍️ 마무리 정리표

| 메서드     | 역할                              | 원본 변경 여부 | 반환값             |
| ---------- | --------------------------------- | -------------- | ------------------ |
| `filter`   | 조건에 맞는 요소만 추출           | ❌             | 새로운 배열        |
| `map`      | 각 요소를 가공해 새로운 배열 생성 | ❌             | 새로운 배열        |
| `sort`     | 요소 정렬 (기본: 문자열 기준)     | ✅             | 정렬된 배열 (원본) |
| `toSorted` | 정렬 (불변 방식)                  | ❌             | 정렬된 새 배열     |
| `join`     | 요소들을 하나의 문자열로 결합     | ❌             | 문자열             |
