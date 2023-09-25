# Syncronous vs Asyncronous

## 비동기 Asyncronous

비동기란 현재 실행 중인 명령이 종료되지 않아도 다음 명령이 실행 가능한 것을 의미합니다. <br>
Callback 함수를 통해 결과를 확인할 수 있습니다. (ex) Ajax, Thread <br>

```java
class User {
  private int userNo = 0;

  // 임계 영역이 되어야하는 메소드
  public void add(String name) {
    System.out.println(name + " : " + userNo++);
  }
}

class UserThread extends Thread {
  User user;

  UserThread(User user, String name) {
    super(name);
    this.user = user;
  }

  public void run() {
    try {
      for (int i = 0; i < 3; i++) {
        user.add(getName());
        sleep(500);
      }
    } catch(InterruptedException e) {
      System.err.println(e.getMessage());
    }
  }
}

public class SyncThread {
  public static void name(String[] args) {
    User user = new User();

    // 3개의 스레드 객체 생성
    UserThread p1 = new UserThread(user, "A");
    UserThread p2 = new UserThread(user, "B");
    UserThread p3 = new UserThread(user, "C");

    // 스레드 스케줄링 : 우선순위 부여
    p1.setPriority(p1.MAX_PRIORITY);
    p2.setPriority(p2.NORM_PRIORITY);
    p3.setPriority(p3.MIN_PRIORITY);

    p1.start();
    p2.start();
    p3.start();
  }
}
```

```java
// 결과 => 순서 뒤죽박죽
A : 0번째 사용
B : 1번째 사용
C : 2번째 사용
A : 3번째 사용
C : 5번째 사용
B : 4번째 사용
C : 7번째 사용
A : 6번째 사용
B : 8번째 사용
```

## 동기 Syncronous

동기란 한 자원에 동시에 접근하는 것을 제한하여 순차적으로 진행되도록 하는 것을 의미합니다. <br>
다음에 실행될 명령은 현재 실행 중인 명령 종료 시까지 대기하고 대기시간이 발생하여 버퍼링이 생길 수 있습니다. <br>
서버와 클라이언트가 주고 받는 것이 동시에 이루어지는 형태로, 현금 인출기와 같이 시간적인 동기화가 필요한 경우 사용합니다. <br><br>

Java에서 `synchronized` 키워드를 사용하여 멀티 스레드 접근 제한을 할 수 있습니다. <br>

```java
public synchronized void add(String name) {
    System.out.println(name + " : " + userNo++);
  }
```

메소드, 블록 단위로 적용이 가능하고, 메소드 단위로 지정할 경우 메소드 전체에 lock이 걸리기 때문에 임계 영역이 너무 커서 가능하면 블록 영역을 활용하는 것이 좋습니다. <br>

```java
💡 Synchronized Collection을 사용하는 경우
List 대신 Vector, Map 대신 HashTable 등 synchronized 키워드를 기반으로 구현된 Collection를 사용할 수 있습니다.
하지만 이 Collection들은 제공하는 API가 적고 성능이 좋지 않을 수 있습니다.

따라서 이 경우에는 Collections라는 util 클래스에서 제공되는 메소드를 사용할 수 있습니다.
synchronizedList(), synchronizedSet(), synchronizedMap() 등이 존재합니다.

JDK 1.7 부터 concurrent package를 통해 ConcurrentHashMap이라는 구현체 또한 제공합니다.
이는 Collections util 보다 synchronized 키워드 적용 범위가 좁아서 보다 좋은 성능을 낼 수 있는 자료구조입니다.
```
