---
title: "Application Context 접근"
categories:
  - Android
tags:
  - Android
---

Context 라는 녀석을 써야하는 경우가 꽤 있다.
- 함수 호출때 파라미터로 Context를 넘겨주거나
- 멤버 변수로 가지고 있거나
해야 하는데,
Singleton 으로 구현된 클래스가 Context를 멤버변수로 가지고 있으면 메모리릭이 발생할 수있다는 Lint 경고가 뜬다.

괜찮은 방법이 없나 찾아보다가 아래처럼 사용하기로 했다.  
Application 클래스의 onCreate()는 앱이 실행될 때, 다른 어떤 컴포넌트보다 먼저 만들어진다고 한다.  
특별히 다른 컴포넌트의 Context 가 필요한 상황이 아니라면, 요걸 쓰면 될 듯 하다.  

App.java
```java
public class App extends Application {
   private static App instance;
   public static App get() { return instance; }

   @Override
   public void onCreate() {
      super.onCreate();
      instance = this;
   }
}
```

AndroidManifest.xml
```
<application
    android:name=".App"
```

## Reference
- <https://stackoverflow.com/a/14057777>
- [Singleton을-위해-Application-Context를-제공하는-static-method를-둘까](http://azza.tistory.com/entry/Singleton%EC%9D%84-%EC%9C%84%ED%95%B4-Application-Context%EB%A5%BC-%EC%A0%9C%EA%B3%B5%ED%95%98%EB%8A%94-static-method%EB%A5%BC-%EB%91%98%EA%B9%8C)