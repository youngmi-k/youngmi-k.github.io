---
layout: single
title: "[JavaScript]Date 객체 완벽 정리"
categories: JavaScript
tag: [JavaScript, Date]
date: 2025-05-31
published: true
toc: true # 목차 생성
author_profile: true # 사용자 프로필
search: true # false로 설정하면 검색시 내용이 뜨지 않는다.
---

# 자바스크립트 `Date` 객체 완벽 정리 📅

이번 글에서는 자바스크립트의 `Date` 객체를 다루는 기본 개념과 실습 예제를 정리해보겠습니다.  
날짜와 시간을 다루는 건 모든 프론트엔드/백엔드 개발에서 **꼭 필요한 기본기**입니다!

---

## ✅ 1. `Date` 객체 생성하기

### 기본 생성

```js
let date1 = new Date(); // 현재 날짜와 시간
console.log("date1:", date1);
```

- 아무 인자 없이 호출하면 **현재 시각**을 기준으로 `Date` 객체가 생성됩니다.

---

### 문자열로 날짜 생성

```js
let date2 = new Date("2009-02-01");
console.log("date2:", date2);
```

- 문자열 형식은 `YYYY-MM-DD` / `YYYY.MM.DD` / `YYYY/MM/DD` 등 다양하게 가능
- 시간까지 포함도 가능

```js
let date3 = new Date("2009/02/01/10:10:10");
console.log("date3:", date3);
```

---

### 숫자 인자로 생성

```js
let date4 = new Date(2009, 2, 1, 10, 10, 10);
console.log("date4:", date4);
```

- 순서: `연도, 월(0부터 시작), 일, 시, 분, 초`
- 주의: **월은 0부터 시작** → `2`는 3월!

---

## ⏱️ 2. 타임스탬프 (Timestamp)

> 타임스탬프는 `1970-01-01T00:00:00Z`(UTC) 기준으로 **몇 밀리초가 지났는지를 나타내는 숫자**입니다.

```js
let ts1 = date1.getTime();
console.log("타임스탬프:", ts1);
```

- 주로 시간 비교, 정렬, 저장 등에 사용

### 타임스탬프 → Date 객체로 변환

```js
let date5 = new Date(ts1);
console.log("복원된 date:", date5);
```

---

## 🔍 3. 날짜/시간 요소 추출하기

```js
let year = date1.getFullYear();    // 연도
let month = date1.getMonth() + 1;  // 월 (주의: 0부터 시작하므로 +1 필요)
let date = date1.getDate();        // 일

let hour = date1.getHours();       // 시
let minutes = date1.getMinutes();  // 분
let seconds = date1.getSeconds();  // 초

console.log(year, month, date, hour, minutes, seconds);
```

📌 대부분의 요소는 **숫자로 반환**되며, 직접 포맷팅해서 사용해야 합니다.

---

## ✏️ 4. 날짜/시간 수정하기

```js
date1.setFullYear(2023);
date1.setMonth(4);        // 5월 (0부터 시작)
date1.setDate(7);
date1.setHours(23);
date1.setMinutes(59);
date1.setSeconds(59);

console.log("수정된 날짜:", date1);
```

- `.setXXX()` 메서드들을 사용해서 각각의 요소를 직접 수정할 수 있습니다.

---

## 📆 5. 다양한 포맷으로 출력하기

```js
console.log(date1.toDateString());     // 예: "Sun May 07 2023"
console.log(date1.toLocaleString());   // 예: "2023. 5. 7. 오후 11:59:59"
```

| 메서드 | 설명 |
|--------|------|
| `toDateString()` | 요일 포함된 날짜 문자열 |
| `toLocaleString()` | 사용자의 로컬 시간대 기준으로 날짜와 시간 표시 |

### 💡 추가 유용 메서드

- `toISOString()` → `2023-05-07T14:59:59.000Z` (서버 저장 시 많이 사용)
- `toUTCString()` → UTC 기준 문자열 출력
- `Date.now()` → 현재 시각의 타임스탬프 반환 (new 없이 사용 가능)

---

## 🧠 요약

| 기능 | 메서드 |
|------|--------|
| 날짜 생성 | `new Date()`, `new Date("YYYY-MM-DD")` |
| 타임스탬프 | `.getTime()`, `Date.now()` |
| 요소 추출 | `.getFullYear()`, `.getMonth()`, ... |
| 요소 수정 | `.setFullYear()`, `.setMonth()`, ... |
| 문자열 출력 | `.toDateString()`, `.toLocaleString()` 등 |

---

## ✍️ 느낀 점

날짜와 시간은 간단해 보여도, **월은 0부터 시작**, **타임스탬프는 ms 단위**, **출력 포맷 다양성** 등 때문에 실수하기 쉬운 영역입니다.  
이번에 직접 실습하면서 개념을 정리하니 더 확실하게 이해가 되었고, 실제 프로젝트에서도 훨씬 자신 있게 다룰 수 있을 것 같아요.
