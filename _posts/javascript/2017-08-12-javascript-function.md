---
title: "자바스크립트의 함수"
categories:
  - Javascript
tags:
  - Javascript
---

자바스크립트에서 가장 중요한 개념은 함수라고 한다. 자바스크립트에서는 함수도 객체이다. 이로 인해 아래 동작들이 가능하다.

- 리터럴에 의한 생성
- 변수나 배열의 요소, 객체의 프로퍼티 등에 할당 가능
- 함수의 인자로 전달 가능
- 함수의 리턴 값으로 리턴 가능
- 동적으로 프로퍼티를 생성 및 할당 가능

이러한 특징이 있으므로, 일급 객체(first class object) 라고 부른다. 이, 일급 객체라는 특성으로 함수형 프로그래밍이 가능하다고 한다.

함수 생성은 변수에 함수를 할당하는 함수 표현식(Function Expression) 방식이 추천 된다. 변수의 선언이 함수 스코프의 맨 처음에 있는 것처럼 해석되는 function hoisting 으로 인한 혼동을 피하기 위해서이다.

자바스크립트의 모든 객체는 Object.prototype 을 최종 부모로 가지고 있다. 함수도 객체이므로 마찬가지이다. OOP의 상속 처럼 어떤 변수나 메서드가 자신의 객체에 없으면 부모 객체들을 차례로 확인한다.


```javascript
var test = 'This is test';
console.log(window.test);  // This is test. 전역 변수는 전역 객체(window)의 프로퍼티

var sayFoo = function () {
    console.log(this.test);
};

sayFoo();  // This is test
```

일반 함수 호출의 경우는 this가 위에서처럼 window 전역 객체에 바인딩되는 반면, 생성자 함수 호출의 경우 this는 새로 생성되는 빈 객체에 바인딩된다.  
자바스크립트에서는 일반 함수와 생성자 함수가 별도의 차이가 없다. 따라서 new를 잘 못 사용하면 오류가 발생할 수 있다.

혼동을 막기 위해 아래와 같은 패턴이 널리 쓰인다.

```javascript
function A(arg) {
    if (!(this instanceof A))  // !(this instanceof arguments.callee) 로 쓰기도 함
        return new A(arg);
    this.value = arg ? arg: 0;
}

var a = new A(100);
var b = A(10);  // 혹시 이렇게 잘 못 쓰더라도 강제로 인스턴스 생성

console.log(a.value);  // 100
console.log(b.value);  // 10
console.log(global.value);  // undefined
```


## Reference
- [인사이드 자바스크립트](http://book.naver.com/bookdb/book_detail.nhn?bid=7400243)
    + 4장. 함수와 프로토타입 체이닝
- <https://en.wikipedia.org/wiki/First-class_citizen> 일급 객체
- <http://bestalign.github.io/2015/10/18/first-class-object/> 일급 객체
