---
title: 합병 정렬(Merge Sort)란?
categories:
- algorithm
last_modified_at: '2021-10-17 12:57:00 +0900'
---

## 정의
합병 정렬은 요소를 분할하여 하나의 길이의 배열로 만든후 다시 병합하면서 정렬하는 알고리즘이다.

**분할 정복이란?**
> 큰 문제를 작은 문제 단위로 쪼개면서 해결해나가는 방식

<br>

## 구현
``` javascript
const arr = [4, 2, 7, 1, 25, 22, 55, 204, 8, 33, 87, 66];

function mergeSort(arr) {
	if (arr.length < 2) return arr;
	const pivot = Math.floor(arr.length / 2);
	const left = arr.slice(0, pivot);
	const right = arr.slice(pivot);
	return merge(mergeSort(left), mergeSort(right));
}

function merge(left, right) {
	const arr = [];

	while (left.length && right.length) {
		if (left[0] < right[0]) {
			arr.push(left.shift());
		} else {
			arr.push(right.shift());
		}
	}

	if (left.length) arr.push(...left);
	if (right.length) arr.push(...right);
	return arr;
}

console.log(mergeSort(arr)); // 오름차순 정렬
```
>  시간 복잡도는 O(nlogn) 입니다.  

<br>

### 참조
* [위키백과](https://ko.wikipedia.org/wiki/%ED%95%A9%EB%B3%91_%EC%A0%95%EB%A0%AC)
* [https://github.com/gyoogle/tech-interview-for-developer/blob/master/Algorithm/MergeSort.md](https://github.com/gyoogle/tech-interview-for-developer/blob/master/Algorithm/MergeSort.md)
* [https://www.zerocho.com/category/Algorithm/post/57ee1fc107c0b40015045cb4](https://www.zerocho.com/category/Algorithm/post/57ee1fc107c0b40015045cb4)
