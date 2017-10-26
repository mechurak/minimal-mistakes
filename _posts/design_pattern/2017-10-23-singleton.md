---
title: "Singleton 패턴"
categories:
  - DesignPattern
tags:
  - Singleton
---

싱글턴 패턴은 해당 클래스의 인스턴스가 하나만 만들어지고, 어디서든지 그 인스턴스에 접근할 수 있도록 하기 위한 패턴.


### 고전적인 싱글턴 패턴

```java
public class Singleton {
	private static Singleton uniqueInstance;
	
	// 기타 인스턴스 변수
	
	private Singleton() {}
	
	public static Singleton getInstance() {
		if (uniqueInstance == null) {  // null 체크 시점으로 인해 멀티 스레딩 이슈 발생 가능
			uniqueInstance = new Singleton();
		}
		return uniqueInstance;
	}
	
	// 기타 메서드
}
```

### 멀티스레딩 해결

```java
public class Singleton {
	private static Singleton uniqueInstance;
	
	// 기타 인스턴스 변수
	
	private Singleton() {}
	
	public static synchronized Singleton getInstance() {  // synchronized 키워드 추가
		if (uniqueInstance == null) {
			uniqueInstance = new Singleton();
		}
		return uniqueInstance;
	}
	
	// 기타 메서드
}
```

하지만 동기화를 하는데 비용이 아깝다는 생각이 든다. 사실 동기화가 꼭 필요한 시점은 이 메서드가 맨 처음 불릴 때 뿐이다.

### 성능 고려

#### 1. getInstance()의 속도가 그리 중요하지 않다면 그냥 둔다
큰 부담이 없다면 그냥 놔둬도 된다. 다만 메소드를 동기화하면 성능이 100배 정도 저하된다고 한다.
이 부분이 병목으로 작용한다면 다른 방법을 생각해 봐야 함.


#### 2. 인스턴스를 필요할 때 생성하지 말고, 처음부터 만들어 버린다.
해당 Singleton의 인스턴스가 무조건 생성되고 사용된다면, 정적 초기화 부분에서 처음부터 만들어 버린다.
이렇게 하면 스레드를 써도 문제 없음

```java
public class Singleton {
	private static Singleton uniqueInstance = new Singleton();  // 정적 초기화 부분(static initializer)에서 인스턴스 생성
	
	private Singleton() {}
	
	public static Singleton getInstance() {
		return uniqueInstance;  // 인스턴스가 이미 있으므로 그냥 리턴
	}
}
```


#### 3. DCL(Double-Checking Locking)을 써서 getInstance()에서 동기화 되는 부분을 줄인다.

```java
public class Singleton {
	// volatile 키워드를 사용해야 멀티스레딩 환경에서 문제가 없음
	private volatile static Singleton uniqueInstance;
	
	private Singleton() {}
	
	public static Singleton getInstance() {
		if (uniqueInstance == null) {
			synchronized (Singleton.class) {
				if (uniqueInstance == null) {
					uniqueInstance = new Singleton();
				}
			}
		}
		return uniqueInstance;
	}
}
```




## Reference
- [Head First Design Patterns](http://book.naver.com/bookdb/book_detail.nhn?bid=1882446)
    + 5 Singleton 패턴
- [java에서 volatile키워드](http://blog.naver.com/jwmoon74/100157579221)