---
title: "Stetho를 이용한 디버깅"
categories:
  - Android
tags:
  - Android
---

단말에서 db 의 실제 값을 확인해보고 싶을 경우가 있다.
루팅된 단말이 아니라면 Stetho 를 이용하는 것이 답이 될 수 있을 것 같다.

db 외에도 네트워크 패킷 확인 등의 여러 기능이 제공된다고 한다.

release 빌드에서 단순 코멘트 아웃 말고 우아하게 적용을 안하는 방법을 연구해 보아야 겠다.

## Reference
- <http://gun0912.tistory.com/69>
- <https://facebook.github.io/stetho/>
- [MyCoinTong 프로젝트에 적용](https://github.com/mechurak/MyCoinTong/commit/2f2a5481b15d6fe399d8a7ca37feb07e6e77621f)