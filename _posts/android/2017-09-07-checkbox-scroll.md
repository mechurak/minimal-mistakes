---
title: "스크롤로 인한 CheckBox 체크 상태 변경 이슈"
categories:
  - Android
tags:
  - Android
---

ListView 내에서 CheckBox를 사용하고 있는데,  
해당 아이템이 화면 밖으로 나가는 경우에 현재 체크 상태가 바뀌는 현상이 있었다.  
ListView가 성능상의 이유로 View를 재사용하기 때문에 생기는 문제라고 한다.

선택 여부는 따로 들고 있고,
OnCheckedChangeListener 대신에 OnClickListener 쓰는 것으로 처리 가능하다.

## Reference
- <http://blog.naver.com/ntjyp/220714424528>
- [MyCoinTong 프로젝트에 적용](https://github.com/mechurak/MyCoinTong/commit/bbf67e383d3e9457abe50ae6f0af89da1f668e73)