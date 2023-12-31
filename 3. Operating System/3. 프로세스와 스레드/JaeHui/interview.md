## 📝 Interview

#### 프로세스와 스레드에 대해 설명하세요.

```
프로세스는 컴퓨터에서 실행되고 있는 프로그램으로, CPU 스케줄링의 대상이 되는 작업, task라는 용어와 같은 의미로 쓰입니다.
프로그램이 메모리에 올라가 인스턴스화된 것을 말합니다.
운영체제의 CPU 스케줄러에 따라 CPU가 프로세스를 실행합니다.

스레드는 프로세스 내 작업의 흐름을 말합니다.
프로세스의 실행 가능한 가장 작은 단위로, 프로세스는 여러 스레드를 가질 수 있습니다.

코드, 데이터, 스택, 힙을 각각 생성하는 프로세스와는 달리, 스레드는 코드, 데이터, 힙은 스레드끼리 서로 공유합니다.
```

<br>

#### 프로세스 컴파일 과정에 대해 설명하세요.

```
1️⃣ 전처리: 소스 코드의 주석을 제거하고 #include 등 헤더 파일을 병합하여 메크로를 치환합니다.
2️⃣ 컴파일러: 오류 처리, 코드 최적화 작업을 하며 어셈블리어로 변환합니다.
3️⃣ 어셈블러: 어셈블러를 통해 어셈블리어가 목적 코드(object code)로 변환됩니다. 리눅스에서는 확장자가 .o라는 파일이 만들어지게 됩니다.
4️⃣ 링커: 프로그램 내에 있는 라이브러리 함수 또는 다른 파일들과 목적 코드를 결합하여 실행 파일을 만듭니다. 확장자는 .exe 또는 .out이라는 확장자를 갖습니다.
```

<br>

#### fork()와 exec() 함수의 차이에 대해 설명하세요.

```
✅ fork()
부모 프로세스의 주소 공간을 그대로 복사하며, 새로운 자식 프로세스를 생성하는 함수입니다.
주소 공간만 복사할 뿐 부모 프로세스의 비동기 작업을 상속하지는 않습니다.

✅ exec()
새롭게 프로세스를 생성하는 함수입니다.
```

<br>

#### 프로세스 메모리 구조에서 스택와 힙에 대해 비교 설명하세요.

```
스택과 힙 모두 런타임 단계에서 메모리를 할당받는 동적 할당이 됩니다.

스택은 지역 변수, 매개 변수, 실행되는 함수에 의해 늘어나거나 줄어드는 메모리 영역입니다.
함수가 호출될 때마다 호출될 때의 환경 등 특정 정보가 스택에 계속해서 저장됩니다.

힙은 동적으로 관리되는 자료 구조의 경우 힙 영역을 사용하는데, malloc(), free() 함수를 통해 관리할 수 있습니다.
```

<br>

#### PCB란 무엇이며 목적에 대해 설명하세요.

```
프로세스 제어 블록으로, 운영체제에서 프로세스에 대한 메타데이터를 저장한 데이터를 말합니다.

프로그램이 실행되면 프로세스가 생성되고 프로세스 주소 값들에 앞서 설명한 스택, 힙 등의 구조를 기반으로 메모리가 할당됩니다.
이 프로세스의 메타데이터들이 PCB에 저장되어 관리됩니다.
이는 프로세스의 중요한 정보를 포함하고 있기 때문에 일반 사용자가 접근하지 못하도록 커널 스택의 가장 앞부분에서 관리됩니다.
```

<br>

#### 컨텍스트 스위칭(Context Switching)에 대해 설명하세요.

```
PCB를 교환하는 과정으로, 한 프로세스에 할당된 시간이 끝나거나 인터럽트에 의해 발생합니다.
많은 프로그램을 동시에 실행하는 것처럼 보이지만 어떠한 시점에서 실행되고 있는 프로세스는 단 한 개이며,
싱글 코어에서 많은 프로세스가 동시에 구동되는 것처럼 보이는 것은 다른 프로세스와의 컨텍스트 스위칭이 아주 빠른 속도로 실행되기 때문입니다.

컨텍스트 스위칭이 일어날 때 유휴 시간(idle time)과 캐시미스가 발생합니다.

💡 캐시미스
컨텍스트 스위칭이 일어날 때 프로세스가 가지고 있는 메모리 주소가 그대로 있으면,
잘못된 주소 변환이 생기므로 캐시클리어 과정을 겪게 되고, 이 때문에 캐시미스가 발생합니다.

💡 스레드 컨텍스트 스위칭
스레드는 스택 영역을 제외한 모든 메모리를 공유하기 때문에, 비용이 더 적고 시간도 더 적게 걸립니다.
```

<br>

#### 멀티스레딩에 대해 설명하세요.

```
프로세스 내 작업을 여러 개의 스레드, 멀티스레드로 처리하는 기법이며, 스레드끼리 서로 자원을 공유하기 때문에 효율성이 높습니다.
웹 요청을 처리할 때 새 프로세스를 생성하는 대신, 스레드를 사용하는 웹 서버의 경우, 훨씬 적은 리소스를 소비합니다.

한 스레드가 중단(blocked)되어도 다른 스레드는 실행(running) 상태일 수 있기 때문에 중단되지 않은 빠른 처리가 가능합니다.
또한 서로 독립적인 작업들을 작은 단위로 나누고 동시에 실행되는 것처럼 보여주는 동시성에도 큰 장점이 있습니다.

하지만 한 스레드에 문제가 생기면 다른 스레드에도 영향을 끼쳐, 스레드로 이루어져 있는 프로세스에 영향을 줄 수 있는 단점이 있습니다.
```

<br>

#### 임계 영역(critical section)에 대해 설명하세요.

```
둘 이상의 프로세스, 스레드가 공유 자원에 접근할 때 순서 등의 이유로 결과가 달라지는 코드 영역을 말합니다.
임계 영역을 해결하기 위한 방법은 크게 `뮤텍스`, `세마포어`, `모니터` 세 가지가 있으며, 이 방법 모두 상호 배제, 한정 대기, 융통성이란 조건을 만족합니다.
이 방법에 토대가 되는 매커니즘은 잠금(lock)입니다.

💡 상호 배제
한 프로세스가 임계 영역에 들어갔을 때 다른 프로세스는 들어갈 수 없습니다.

💡 한정 대기
특정 프로세스가 영원히 임계 영역에 들어가지 못하면 안 됩니다.

💡 융통성
한 프로세스가 다른 프로세스의 일을 방해해서는 안 됩니다.
```

<br>

#### 뮤텍스와 세마포어의 차이에 대해 설명하세요.

```
뮤텍스는 프로세스나 스레드가 공유 자원을 lock()을 통해 잠금 설정하고 사용한 후에는 unlock()을 통해 잠금 해제하는 객체입니다.
잠금이 설정되면 다른 프로세스나 스레드는 잠긴 코드 영역에 접근할 수 없고 해제는 그와 반대가 되어, 잠금 또는 잠금 해제라는 상태만을 가집니다.

세마포어는 일반화된 뮤텍스로, 간단한 정수 값과 두 가지 함수 wait(P 함수) 및 signal(V 함수)로 공유 자원에 대한 접근을 처리합니다.
wait()는 자신의 차례가 올 때까지 기다리는 함수이며, signal()은 다음 프로세스로 순서를 넘겨주는 함수입니다.
```

<br>

#### 교착 상태(deadlock)의 원인에 대해 설명하세요.

```
교착상태란 두 개 이상의 프로세스들이 서로가 가진 자원을 기다리며 중단된 상태를 의미합니다.

교착 상태의 원인으로는 상호 배제, 점유와 대기, 비선점, 환형 대기가 있습니다.
- 상호 배제: 한 프로세스가 자원을 독점하고 있으며 다른 프로세들은 접근이 불가능한 상태
- 점유 대기: 특정 프로세스가 점유한 자원을 다른 프로세스가 요청하는 상태
- 비선점: 다른 프로세스의 자원을 강제적으로 가져올 수 없는 상태
- 환형 대기: 프로세스 A가 프로세스의 B의 어떤 자원을 요청할 때, 프로세스 B도 프로세스 A가 점유하고 있는 자원을 요청하는 상황
```

<br>

#### 교착 상태의 해결 방법에 대해 설명하세요.

```
1. 자원 할당 시 위 조건이 성립되지 않도록 설계하는 것
2. 교착 상태 가능성이 없을 때만 자원 할당되며, 프로세스당 요청할 자원들의 최대치를 통해 자원 할당 가능 여부를 파악하는 `은행원 알고리즘`을 사용
3. 교착 상태가 발생하면 사이클이 있는지 찾아보고 이에 관련된 프로세스를 한 개씩 지움
4. 교착 상태 처리 비용이 크므로 교착 상태 발생 시 사용자가 작업을 종료시킴
```
