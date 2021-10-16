---
title: Bubble Sort(버블 정렬) 이란?
last_modified_at: '2021-10-16 19:01:00 +0900'
categories:
- algorithm
---

## 정의
버블 정렬은 서로 인접한 두 원소를 비교하여 조건에 맞지 않으면 자리를 교환하여 정렬하는 알고리즘 입니다.

<br>

## 구현
``` javascript
const arr = [4, 2, 7, 1, 25, 22, 55, 204, 8, 33, 87, 66];

for (let i = 0; i < arr.length; i++) {
	for (let j = 1; j < arr.length - i; j++) {
		if (arr[j] < arr[j - 1]) {
			[arr[j], arr[j - 1]] = [arr[j - 1], arr[j]];
		}
	}
}

console.log(arr); // 오름차순 정렬
```
>  Big(O) 시간 복잡도는 o(n<sup>2</sup>) 입니다.   

<br>

### 참조
* [위키백과](https://ko.wikipedia.org/wiki/%EA%B1%B0%ED%92%88_%EC%A0%95%EB%A0%AC)
