---
title: "자바스크립트의 클로저"
categories:
  - Javascript
tags:
  - Javascript
---

이미 생명 주기가 끝난 외부 함수의 변수를 참조하는 함수를 클로저라고 한다.  
클로저로 참조되는 외부 변수를 자유 변수(free variable)이라고 한다. closure라는 이름은 함수가 자유 변수에 닫혀 있다(closed, bound)는 의미인데, 우리 말로 의역하면 '자유 변수에 엮여 있는 함수' 정도라고 한다.

```javascript
// 자바스크립트로 클로저를 구현하는 전형적인 패턴

fucntion outerFunc() {
    var x = 1;  // 자유 변수
    
    return function() {
        /* x와 arguments를 활용한 로직 */
    }
}

var new_func = outerFunc();

// outerFunc 실행 컨텍스트는 끝남

new_func();
```


클로저는 자바스크립에만 있는 개념은 아니고, 여러 언어에서 차용되고 있는 특성이다. 특히 함수를 일급 객체로 취급하는 언어(보통 이를 함수형 언어라고 한다)에서 주요하게 사용되는 특성이다.

outerFunc을 호출했을 때 만들었던 변수 객체가 리턴된 함수(클로저)에 의해 참조되고 있으므로, GC 되지 않고 계속 남아 있는 상태이고, 각 변수를 클로저에서 접근해서 수정도 할 수 있는 상태 정도의 느낌이다.

여러 용도로 쓰인다고는 하지만, 아직 감이 잡히진 않는다. 코드 보는 데 어려움을 줄 수 있다면 가능하면 안 쓰는게 좋다고 생각하지만, 꼭 필요하고 유용한 부분이 있으니까 중요하다고 했지 싶다.  
일단 당장 쓸일은 없을 듯 하긴 하지만, 대략 어떤 내용인지는 알았다는 데 의의를 두자.


## Reference
- [인사이드 자바스크립트](http://book.naver.com/bookdb/book_detail.nhn?bid=7400243)
    + 5.4 클로저