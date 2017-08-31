---
title: "Intent의 extra 값들 확인"
categories:
  - Android
tags:
  - Android
---

전달받은 인텐트 값에 어떤 extra 값들이 있는지 확인해보고 싶은 경우가 있다.
아래 형태로 로그를 찍어볼 수 있다.
```java
@Override
public void onReceive(Context context, Intent intent) {
    String action = intent.getAction();
    Log.e("TempTag", "action: " + action);
    
    Bundle extras = intent.getExtras();
    if (extras != null) {
        for (String key: extras.keySet()) {
            Log.e("TempTag", "  " + key + ": " + extras.get(key));
        }
    }
}
```

보기 좀 힘들수도 있을 것 같은데, 아래 한 줄로도 가능하다.
```java
Log.e("intent URI", intent.toUri(0));
```

## Reference
- <http://wkqqn.tistory.com/entry/Android-Intent-%EB%A1%9C%EA%B7%B8-%EC%B0%8D%EA%B8%B0>
- <https://stackoverflow.com/a/39543548>
- <https://developer.android.com/reference/android/content/Intent.html#toUri(int)>
