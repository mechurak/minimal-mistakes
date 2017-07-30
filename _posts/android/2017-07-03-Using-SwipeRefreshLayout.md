---
title: "SwipeRefreshLayout 활용"
categories:
  - Android
tags:
  - UI
  - Android
  - SwipeRefreshLayout
---

SwipeRefreshLayout은 사용자가 위에서 아래로 스와이프 했을 때, 조그만 동그라미가 돌아가면서 화면의 내용을 업데이트할 수 있도록 한다. UI에 익숙하지 않은 필자도 간단하게 적용할 수 있었다.
기존에 FloatingActionButton 으로 리프레쉬 버튼을 만들어 뒀었는데, SwipeRefreshLayout을 사용하니 훨씬 깔끔해진 느낌이다.

대략 아래 느낌으로 구현한다. (아래 Reference의 링크 참고)
1. 레이아웃 파일에서 ListView 등을 감싸도록 함
2. OnRefreshListner.onRefresh() 에서 업데이트 호출
3. ActionBar 의 메뉴 버튼도 구현
    - 스와이프를 이용 못 하는 케이스가 있을 수 있음
    - showAsAction="never" 추천 (메뉴가 바로 보이면 swipe와 다른 동작으로 생각할 수 있음)
    - setRefreshing(true) 명시적 호출 필요
4. 업데이트가 완료되면, setRefresh(false) 호출하여 indicator 종료

## Reference
- <https://developer.android.com/training/swipe/index.html>: Developer 사이트
- <http://blog.miyu.kr/163>: 사용방법 블로그
- [MyCoinTong 프로젝트에 적용](https://github.com/mechurak/MyCoinTong/commit/2b1b650e30ed8020399ba25c992c72ef01b0a342)
