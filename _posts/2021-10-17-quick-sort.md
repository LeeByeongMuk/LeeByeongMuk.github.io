---
title: 퀵 정렬(Quick Sort) 란?
categories:
- algorithm
last_modified_at: '2021-10-17 00:03:00 +0900'
---

## 정의
퀵 정렬은 pivot을 정해서 pivot보다 크면 오른쪽 작으면 왼쪽으로 분할하고 분할된 배열의 길이가 1이하 일때까지 반복하는 정렬이다 .

<br>

## 구현
``` javascript
const arr = [4, 2, 7, 1, 25, 22, 55, 204, 8, 33, 87, 66];

function quickSort(arr) {
	if (arr.length < 2) return arr;

	const pivot = arr[0];
	const pivots = [];
	const left = [];
	const right = [];

	for (let n of arr) {
		if (n < pivot) {
			left.push(n);
		} else if (n > pivot) {
			right.push(n);
		} else {
			pivots.push(n);
		}
	}

	return [
		...quickSort(left),
		...pivots,
		...quickSort(right)
	];
}

console.log(quickSort(arr)); // 오름차순 정렬
```
>  Big(O) 시간 복잡도는 O(n<sup>2</sup>) 입니다.  
>  평균, 최악일때의 시간복잡도는 O(nlogn) 입니다.

<br>

### 참조
* [위키백과](https://ko.wikipedia.org/wiki/%ED%80%B5_%EC%A0%95%EB%A0%AC)
* [https://im-developer.tistory.com/135](https://im-developer.tistory.com/135)
* [https://github.com/gyoogle/tech-interview-for-developer/blob/master/Algorithm/QuickSort.md](https://github.com/gyoogle/tech-interview-for-developer/blob/master/Algorithm/QuickSort.md)
