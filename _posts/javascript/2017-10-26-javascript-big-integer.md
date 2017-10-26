---
title: "자바스크립트에서 big integer"
categories:
  - Javascript
tags:
  - Javascript
---

자바스크립트에서 숫자는 모두 number 타입이다. 다른 언의의 double 느낌이다.
정수 기준으로 2^53 까지만 유효하게 표현될 수 있다.
저걸 넘어가는 아주 큰 수를 다뤄야 할 때는, 다른 처리가 필요하다.

이미 [관련 라이브러리](https://github.com/peterolson/BigInteger.js)가 많이 있으니, 그것을 쓰면 되겠다.


## Reference
- <http://weicomes.tistory.com/126>
- <https://github.com/peterolson/BigInteger.js>
- <http://peterolson.github.io/BigInteger.js/benchmark/>