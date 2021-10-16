---
title: 삽입 정렬(Insertion Sort)란?
categories:
- algorithm
last_modified_at: '2021-10-16 20:17:00 +0900'
---

## 정의
삽입 정렬은 2번째 원소부터 시작하여 그 앞(왼쪽)의 원소들과 비교하여 삽입할 위치를 지정한 후, 원소를 뒤로 옮기고 지정된 자리에 자료를 삽입 하여 정렬하는 알고리즘입니다.

<br>

## 구현
``` javascript
const arr = [4, 2, 7, 1, 25, 22, 55, 204, 8, 33, 87, 66];

for (let i = 1; i < arr.length; i++) {
	let current = arr[i];
	let prev = i - 1;

	while ((arr[prev] > current) && (prev >= 0)) {
		arr[prev + 1] = arr[prev];
		prev--;
	}

	arr[prev + 1] = current;
}

console.log(arr); // 오름차순 정렬
```
>  Big(O) 시간 복잡도는 O(n<sup>2</sup>) 입니다.   

<br>

### 참조
* [위키백과](https://ko.wikipedia.org/wiki/%EC%82%BD%EC%9E%85_%EC%A0%95%EB%A0%AC)
* [https://github.com/GimunLee/tech-refrigerator/blob/master/Algorithm/%EC%82%BD%EC%9E%85%20%EC%A0%95%EB%A0%AC%20(Insertion%20Sort).md#%EC%82%BD%EC%9E%85-%EC%A0%95%EB%A0%AC-insertion-sort](https://github.com/GimunLee/tech-refrigerator/blob/master/Algorithm/%EC%82%BD%EC%9E%85%20%EC%A0%95%EB%A0%AC%20(Insertion%20Sort).md#%EC%82%BD%EC%9E%85-%EC%A0%95%EB%A0%AC-insertion-sort)
