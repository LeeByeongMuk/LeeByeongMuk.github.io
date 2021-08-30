---
title: 자바 스크립트 Infinite scrolling
categories:
- javascript
last_modified_at: '2021-08-31 01:24:00 +0900'
---

infinite scroll 구현을 할때마다 항상 검색의 의존 하는거 같아 정리를 해보려고 한다.

## height
#### scrollHeight
**엘리먼트의 높이**를 나타내는 값이다.   
`box-model`이 있다고 할때 `padding` 영역까지의 높이

#### clientHeight
스크롤바 안쪽의 있는 엘리먼트의 높이이다. 
엘리먼트가 스크롤바 크기 보다 작을때 `padding`영역까지 포함한다.

#### scrollTop
scrollHeight 높이에서 clientHeight 높이를 빼면 나오는 값이다.   
상단에서 스크롤 이 떨어진 위치의 값


## scroll event 활용
**스크롤 이벤트**를 활용하여 스크롤이 특정 영역에 왔을때 이벤트를 발생 시키는 패턴이다.
``` html
<div id="main">
	<div class="item"></div>
	<div class="item"></div>
	<div class="item"></div>
</div>
```

``` javascript
window.addEventListener('scroll', (e) => {
	const {scrollHeight, scrollTop, clientHeight} = e.target.scrollingElement;

	if (scrollHeight - scrollTop <= clientHeight) {
		const item = document.createElement('div');
		item.className = 'item';
		document.querySelector('#main').appendChild(item);
	}
});
```
마지막까지 스크롤시 새로운 `div`를 생성하는 패턴이다.

#### 쓰로틀링(Throttling)
스크롤 이벤트 활용시 많이 쓰는 패턴이다.
``` javascript
let timer;
window.addEventListener('scroll', (e) => {
	if (!timer) {
		timer = setTimeout(() => {
			timer = null;
			const {scrollHeight, scrollTop, clientHeight} = e.target.scrollingElement;

			if (scrollHeight - scrollTop <= clientHeight) {
				const item = document.createElement('div');
				item.className = 'item';
				document.querySelector('#main').appendChild(item);
			}
		}, 250);
	}
});
```
연속 적으로 스크롤시  코드 실행 후 2.5초뒤 다시 실행된다.

## Intersection Observer API
타겟 요소와 상위 요소 또는 최상위 document 의 viewport 사이의 intersection 내의 변화를 비동기적으로 관찰하는 방법입니다.
```javascript
const items = document.querySelectorAll('.item');
const options = {
	root: null,
	rootMargin: '0px',
	threshold: 0.5
};
const callback = (entries, observer) = {
	entries.forEach(entry => {
		if (entry.isIntersecting) {
			entry.target.classList.add('show');
		} else {
			entry.target.classList.remove('show');
		}
		
		// infinite scrolling 구현
		if (entry.isIntersecting)
		
	});
};
let observer = new IntersectionObserver(callback, options);
items.forEach(item => observer.observe(item));
```
#### 활용법
* 이미지나 다른 컨텐츠의 지연 로딩(Lazy Loading)
* infinite-scroll 을 구현
* 광고 수익을 계산하기 위한 용도로 광고의 가시성 보고
* 사용자에게 결과가 표시되는 여부에 따라 작업이나 애니메이션을 수행할 지 여부를 결정

### 참고
[MDN Web Docs](https://developer.mozilla.org/ko/docs/Web/API/Intersection_Observer_API)
