---
title: "api key 와 .gitignore"
categories:
  - General
tags:
  - git
---

자신의 api key 는 git 저장소에 올라가면 안된다.
특정 파일에 해당 내용을 적고, 해당 파일을 .gitignore 에 포함해서 저장소에 올리지 않는 방식을 사용한다.

Android 의 경우, .gitignore 에 keys.xml 을 추가하고, 아래처럼 사용할 수 있다.


```xml
<!-- app/src/main/res/values/keys.xml -->
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <string name="connect_key">qwer1234qwer1234qwer1234qwer1234</string>
    <string name="secret_key">qwer1234qwer1234qwer1234qwer1234</string>
</resources>
```

```java
String connectKey = getResources().getString(R.string.connect_key);
String secretKey = getResources().getString(R.string.secret_key);
Log.d(TAG, "connectKey: " + connectKey +", secretKey: " + secretKey);
```

## Reference
- <https://stackoverflow.com/a/29804824>