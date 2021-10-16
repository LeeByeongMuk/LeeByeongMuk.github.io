---
title: 선택 정렬(Selection Sort) 이란?
---

## 정의
선택 정렬은 해당 순서에 원소를 넣을 위치는 이미 정해져 있고, 어떤 원소를 넣을지 선택하는 알고리즘입니다.

<br>

## 구현
``` javascript
const arr = [4, 2, 7, 1, 25, 22, 55, 204, 8, 33, 87, 66];

for (let i = 0; i < arr.length; i++) {
	let minIdx = i;
	for (let j = i + 1; j < arr.length; j++) {
		if (arr[j] < arr[minIdx]) {
			minIdx = j;
		}
	}
	[arr[i], arr[minIdx]] = [arr[minIdx], arr[i]];
}

console.log(arr); // 오름차순 정렬
```
>  Big(O) 시간 복잡도는 O(n<sup>2</sup>) 비교, O(n) 교환 입니다.   

<br>

### 참조
* [위키백과](https://ko.wikipedia.org/wiki/%EC%84%A0%ED%83%9D_%EC%A0%95%EB%A0%AC)
* [https://github.com/GimunLee/tech-refrigerator/blob/master/Algorithm/%EC%84%A0%ED%83%9D%20%EC%A0%95%EB%A0%AC%20(Selection%20Sort).md#%EC%84%A0%ED%83%9D-%EC%A0%95%EB%A0%AC-selection-sort](https://github.com/GimunLee/tech-refrigerator/blob/master/Algorithm/%EC%84%A0%ED%83%9D%20%EC%A0%95%EB%A0%AC%20(Selection%20Sort).md#%EC%84%A0%ED%83%9D-%EC%A0%95%EB%A0%AC-selection-sort)
