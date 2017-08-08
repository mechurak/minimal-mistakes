---
title: "파이썬 os.system()과 time.strftime()"
categories:
  - Python
tags:
  - Python
---

주기적으로 안드로이드 단말의 meminfo 와 dbinfo 를 확인해야 되서 쉘스크립트를 만들까 했는데, 전혀 기억이 나지 않는다. ㅠㅜ
아무래도 쉘스크립트 문법 찾는 것보다 파이썬이 편할 것 같아 필요한 부분을 검색해서 아래와 같은 형태가 되었다.

```python
import os
import time

timestamp = time.strftime("%Y%m%d_%H%M%S.txt")    # ex) "20170808_160546.txt"
os.system("adb shell dumpsys meminfo [패키지명] > log/meminfo_" + timestamp)
os.system("adb shell dumpsys dbifo [패키지명] > log/dbinfo_" + timestamp)
```

필요할 때마다 위 파이썬 파일을 실행해서 원하는 로그를 시간 포함한 파일명으로 저장할 수 있었다.
역시 요런 작업은 파이썬이 제일 좋은 듯 하다.
