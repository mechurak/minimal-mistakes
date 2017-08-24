---
title: "자바스크립트와 함수형 프로그래밍"
categories:
  - Javascript
tags:
  - Javascript
---

함수형 프로그래밍은 함수의 조합으로 작업을 수행함을 의미한다. 중요한 것은 이 작업이 이루어지는 동안 작업에 필요한 데이터와 상태는 변하지 않는다는 점이다. 변할 수 있는 건 오로지 함수 뿐이다. 이 함수가 바로 연산의 대상이 된다.  

이렇게 외부에 아무런 영향을 미치지 않는 함수를 Pure fucntion(순수 함수)라고 한다. 외부에 영향을 미치지 않으므로 이미 작성된 순수 함수로 다른 작업에 활용해도 문제가 없다.

함수를 또 하나의 값으로 간주하여 함수의 인자 혹인 반환 값으로 사용할 수 있는 함수를 Higher-order function(고계 함수)라고 한다.

내부 데이터 및 상태는 그대로 둔 채 제어할 함수를 변경 및 조합함으로써 원하는 결과를 얻어내는 것이 함수형 프로그래밍의 중요한 특성이다. 이 특성은 높은 수준의 모듈화가 가능하다는 점에서 큰 장점이 된다.

함수형 프로그래밍의 반대되는 개념을 명령형 프로그래밍(Imperative Programing) 이라고 한다. 입력 값을 받아 출력 값을 계산하는 순수한 의미의 함수도 있지만, 특정 작업을 수행하는 여러 가지 명령이 기술되어 있는 함수도 있다. 이러한 종류의 함수를 프로시저(Procedure) 라고 한다.  
`printf` 함수를 보면, 리턴 값이 있지만 이 값은 동작이 제대로 수행되었는지를 알려주는 보조적인 역할을 할뿐, 실제로는 화면에 출력하는 동작이 중요하다.

자바스크립트에서도 함수형 프로그래밍이 가능한데, 자바스크립트가 다음을 지원하기 때문이다.  
- 일급 객체로서의 함수
- 클로저


```javascript
var cacher = function(cache, func) {  // 클로저를 이용하여 cache를 캐시로 활용
    var calculate = function(n) {
        if (typeof(cache[n] === 'number') {  // 메모이제이션을 통한 성능 향상
            result = cache[n];
        } else {
            result = cache[n] = func(calculate, n);
        }
        return result;
    }
    return calculate;
};

var fact = cacher({ '0':1 }, function(func, n) {
    return n * func(n-1);
});
var fibo = cacher({ '0':0, '1':1 }, function(func, n) {
    return func(n-1) + func(n-2);
});

console.log(fact(10));
console.log(fibo(10));
```

함수형 프로그래밍이 수학에서 출발한 문제 해결 방법론이므로 수학 문제를 프로그래밍으로 해결하는 데 있어서 상당한 이득을 볼 수 있다.

자바스크립트로 함수형 프로그래밍에서 제시하는 방법론 중 일부는 구현이 가능하지만 순수한 함수형 프로그래밍 언어라고 말하지는 않는다. 함수형 프로그래밍에 좀 더 관심이 있다면 Lisp나 Haskell과 같은 언어를 들여다 봐야 한다.

## Reference
- [인사이드 자바스크립트](http://book.naver.com/bookdb/book_detail.nhn?bid=7400243)
    + 7장. 함수형 프로그래밍