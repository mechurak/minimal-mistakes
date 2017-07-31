---
title: "SQLite 인덱싱 이용하기"
categories:
  - android
tags:
  - android
  - sqlite
  - memory_leak
  - performance
---

메모리릭의 원인을 찾고 있는데, UI없이 서비스로 이루어진 앱이라서 그런지 생각처럼 쉽지 않다.
일단 `adb shell dumpsys meminfo [패키지명]` 의 추이를 봤을 때, `Native Heap` 이 증가하는 모습이 보여서 C++ 쪽을 보면 될 거라 생객했다.
그런데 다른 항목들도 같이 보니, `Native Heap` 추이가 SQL쪽의 `MEMORY_USED`, `PAGECACHE_OVERFLOW` 항목의 추이와 같이 가는 모습을 보였다. (C++ 쪽에는 db 사용 부분은 없다.)

일단, `adb shell dumpsys dbinfo [패키지명]` 으로, 최근 몇 개의 쿼리 실행 내역과 순서, 속도를 확인 할 수 있다.
그리고 단말에서 뽑아낸 db 파일을 [SqliteBrower](http://sqlitebrowser.org/)로 열어서, 해당 쿼리문들의 실행 계획을 확인해 보았다.
`EXPLAIN QUERY PLAN [원래 SELECT 구문]` 을 실행하여 `SCAN TABLE` 으로 시작하면 인덱스를 사용하지 않은 것이고,
`SEARCH TABLE [테이블명] USING [인덱스명]` 으로 나오면 인덱스를 사용하고 있는 것이다.

db쪽을 잘 모르지만, 적절한 인덱스를 사용해서 db 사이즈를 조금 늘리는 대신 속도가 빨라진다는 것은 이해가 되는데,
이것이 메모리릭과 어떤 관련이 있을지는 아직 정확히 모르겠다.
인덱싱을 잘 함으로써 캐시에 올리는 빈도가 낮아지는 것일까?
어쨋든 시도해보자.

루팅되지 않은 단말에서는,
[Stetho](http://facebook.github.io/stetho/) 를 통해서 SQL 구문을 실행해 볼 수 있다고 한다.
<https://stackoverflow.com/questions/9997976/android-pulling-sqlite-database-android-device> 의 방법들도 확인해 보면 좋을 듯 하다.


## Reference
- [안드로이드 개발 레벨업 교과서](http://book.naver.com/bookdb/book_detail.nhn?bid=12107989)
    + 14.5 그 밖의 최적화 방법을 이해하자
- [안드로이드 프로그래밍 Next Step](http://book.naver.com/bookdb/book_detail.nhn?bid=12096889)
    + 7.3 SQLite/ContentProvider 관련 팁
- [IOS에서 유사 이슈](https://stackoverflow.com/questions/14404052/sqlite-page-cache-keeps-growing-performance-drops)
