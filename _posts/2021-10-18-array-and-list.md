---
title: 배열와 리스트의 차이
categories:
- CS
last_modified_at: '2021-10-18 00:39:00 +0900'
---

배열(Array)과 연결 리스트(Linked List)의 차이를 정리해 보겠습니다.

<br>

## 배열의 특징
* 배열은 번호(인덱스)와 번호에 대응하는 데이터들로 이루어진 자료 구조를 나타냅니다.
* 일반적으로 배열에는 같은 종류의 데이터들이 순차적으로 저장되어, 값의 번호가 곧 배열의 시작점으로부터 값이 저장되어 있는 상대적인 위치가 됩니다.

<br>

#### 배열의 장점
* 인덱스를 통해 검색이 용이합니다. `O(n)`
* 연속적이므로 메모리 관리가 편합니다.

#### 배열의 단점
* 요소를 삭제시 빈 공간으로 남겨둬야해 메모리 낭비가 됩니다.
* 새로운 요소를 추가할 때, 여유 공간이 있는 경우엔 `O(1)`이지만, 여유공간이 없는 경우엔 `O(n)`입니다.


<br>

## 연결 리스트의 특징
* 각 노드가 데이터와 포인터를 가지고 한 줄로 연결되어 있는 방식으로 데이터를 저장하는 자료 구조입니다.
* 리스트는 빈 공간이 없이 요소를 관리합니다.

#### 연결 리스트의 장점
* 포인터를 통하여 다음 데이터를 가르키고 있어 삽입 삭제가 용이 합니다.`O(1)`
* 저장공간의 크기가 정해져 있지 않습니다.

#### 연결 리스트의 단점
* 검색 성능이 좋지 않습니다. `O(n)`

#### 코드 구현
```
class Node {
	constructor(data, next = null) {
		this.data = data;
		this.next = next;
	}
}

class LinkedList {
	constructor() {
		this.head = null; // 첫번 째 노드
		this.length = 0; // list 길이
	}

	addFirst(data) {
		this.head = new Node(data, this.head);
		this.length++;
	}

	addLast(data) {
		let current = this.head;
		const node = new Node(data);

		if (!this.head) {
			this.head = node;
		} else {
			while (current.next) {
				current = current.next;
			}

			current.next = node;
		}

		this.length++;
	}

	addAt(data, pos) {
		if (pos > this.length) return;
		if (pos === 0) {
			this.addFirst();
			return;
		}

		const node = new Node(data);
		let current = this.head;
		let count = 0;
		let before;

		while (count < pos) {
			before = current;
			count++;
			current = current.next;
		}

		node.next = current;
		before.next = node;
		this.length++;
	}

	search(pos) {
		let current = this.head;
		let count = 0;
		while (count < pos) {
			current = current.next;
			count++;
		}
		return current.data;
	}

	remove(pos) {
		let current = this.head;
		let count = 0;
		let before;

		if (pos === 0) {
			this.head = this.head.next;
		} else {
			while (count < pos) {
				before = current; // 이전 값을 현재 값으로 변경
				count++; // count++ 후 조건시 반복
				current = current.next; // 현재 값을 다음 값으로 변경
			}
			before.next = current.next; // 현재 값 이후 값을이 next 값으로 들어옴
		}

		this.length--;
	}
}

const list = new LinkedList();
list.addLast(1);
list.addLast(2);
list.addLast(3);
list.addFirst(7);
list.addAt(2222, 3);
```

<br>

### 참조
* [위키백과](https://ko.wikipedia.org/wiki/%EC%97%B0%EA%B2%B0_%EB%A6%AC%EC%8A%A4%ED%8A%B8)
* [위키백과](https://ko.wikipedia.org/wiki/%EB%B0%B0%EC%97%B4)
* [https://www.zerocho.com/category/Algorithm/post/58008a628475ed00152d6c4d](https://www.zerocho.com/category/Algorithm/post/58008a628475ed00152d6c4d)
* [https://velog.io/@kimkevin90/Javascript%EB%A5%BC-%EC%9D%B4%EC%9A%A9%ED%95%9C-Linked-List-%EA%B5%AC%ED%98%84](https://velog.io/@kimkevin90/Javascript%EB%A5%BC-%EC%9D%B4%EC%9A%A9%ED%95%9C-Linked-List-%EA%B5%AC%ED%98%84)
