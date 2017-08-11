---
title: "자바스크립트의 배열"
categories:
  - Javascript
tags:
  - Javascript
---

자바스크립트에서 배열은 객체의 특별한 형태이다.  
객체 리터럴 방식으로 생성한 객체의 경우, Object.prototype 객체가 프로토타입이다.  
반면에 배열의 경우, Array.prototype 객체가 프로토타입이 된다. Array.prototype 객체의 프로토타입은 Object.prototype이다.

배열을 선언할 때 특별히 크기를 지정하지 않아도 되며, 어떤 위치에 어느 타입의 데이터를 저장하더라도 에러가 발생하지 않는다.  
배열도 객체이기 때문에 인덱스가 숫자인 배열 원소 이외에도 객체처럼 동적으로 프로퍼티를 추가할 수 있다.

```javascript
var emptyArr = [];
console.log(emptyArr[0]);  // 출력: undefined

emptyArr[0] = 100;
emptyArr[3] = 'eight';
emptyArr[7] = true;
console.log(emptyArr);  // 출력: [100, undefined x 2, "eight", undefined x 3, true]
console.log(emptyArr.length);  // 출력: 8

emptyArr.color = 'blue';
emptyArr.name = 'number_array';
console.log(empArr.length);  // 출력: 8


console.dir(emptyArr)  // 요 값을 보면, 배열도 객체와 마찬가지로 key: value 형태로 배열 원소 및 프로퍼티 등이 있음을 확인할 수 있다.
```

## Reference
- [인사이드 자바스크립트](http://book.naver.com/bookdb/book_detail.nhn?bid=7400243)
    + 3.5 배열
