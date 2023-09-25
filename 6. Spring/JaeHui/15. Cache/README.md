# [Cache](https://kchanguk.tistory.com/145)

캐싱(Caching)은 애플리케이션의 처리 속도를 높여줍니다. <br>
이미 가져온 데이터나 계산된 결과값의 복사본을 저장함으로써 처리 속도를 향상시키며, 이를 통해 향후 요청을 더 빠르게 처리할 수 있습니다. <br>
대부분의 프로그램이 동일한 데이터나 명령어에 반복해서 엑세스하기 때문에 캐싱은 효율적인 아키텍처 패턴입니다.<br>

```
💡 cache hit
참조하려는 데이터가 캐시에 존재할 때 cache hit라고 합니다.
💡 cache miss
참조하려는 데이터가 캐시에 존재 하지 않을 때 cache miss라고 합니다.
💡cache hit ratio(캐시 히트율)
(cache hit 횟수)/(전체참조횟수) = (cache hit 횟수)/(cache hit 횟수 + cache miss 횟수)
```

## [Local Cache](https://velog.io/@qotndus43/Cache)

Local Cache는 서버마다 캐시를 따로 저장하는 방식으로, Memory, Disk와 같은 로컬 서버 장비의 Resource를 이용합니다. <br>
<img src="./img/local cache.png" width="600"><br>
서버 내에서 작동하기 때문에 속도가 빠른 장점이 있지만, 다른 서버의 캐시를 참조하기 어렵다는 단점도 존재합니다. <br>
캐시에 저장된 데이터가 변경되는 경우에는 해당 서버를 제외한 모든 peer에 변경사항을 전달하고 복사하는 과정을 거칩니다.<br>
이 때문에 WAS 인스턴스가 늘어나고, 만약 캐시 저장 데이터 크기가 커지면 성능이 저하되기도 합니다.<br>

### Ehcache

EhCache는 Spring에서 사용 가능한 자바 기반 오픈 소스 기반의 Local Cache입니다. <br>
기본 JVM메모리에 저장되어, 레디스처럼 별도의 서버 설치 없이 가볍게 사용하기 편리합니다. <br>
EHcache는 로컬캐시로서 특정 서버에 종속되기 때문에, 멀티 서버 환경에서는 데이터 싱크가 필요합니다. <br>
따라서 동기화가 속도에 영향을 줄 수 있고, 데이터 유실 가능성이 있다는 단점이 있습니다. <br>

```java
@Cacheable: 캐시할 수 있는 메소드를 지정
@CachePut: 메소드 실행에 영향을 주지 않고 캐시를 갱신
@CacheEvict: 캐시에서 오래되거나 사용하지 않는 데이터를 제거하는 메소드를 지정, void 반환형에서만 사용 가능
@Caching 어노테이션을 여러 개 사용할 때 사용
```

## Global Cache - Redis

Global Cache는 여러 서버에서 캐시 서버에 접근하여 참조하는 방법입니다. <br>
별도의 캐시 서버를 이용하기 때문에 서버 간 데이터 공유가 쉽고 데이터를 분산하여 저장할 수 있습니다. <br>
<img src="./img/global cache.png" width="600"><br>
하지만 네트워크 트래픽을 사용해야 해서 Local Cache보다는 속도가 느립니다. <br>
Local Cache와 다르게 캐시에 저장된 데이터가 변경되더라도 추가적인 작업이 별도로 필요하지 않습니다.<br>

### Redis

Redis란 Key, Value 구조의 비정형 데이터를 저장하고 관리하기 위한 오픈 소스 기반의 비관계형 데이터 베이스 관리 시스템 (DBMS)입니다. <br>
데이터베이스, 캐시, 메세지 브로커로 사용되며 인메모리 데이터 구조를 가진 저장소입니다.<br>

```
✅ 캐시 서버 구현 패턴
💡 Look aside cache
1. 클라이언트가 데이터를 요청
2. 웹서버는 데이터가 존재하는지 Cache 서버에 먼저 확인
3. Cache 서버에 데이터가 있으면 DB에 데이터를 조회하지 않고 Cache 서버에 있는 결과값을 클라이언트에게 바로 반환 (Cache Hit)
4. Cache 서버에 데이터가 없으면 DB에 데이터를 조회하여 Cache 서버에 저장하고 결과값을 클라이언트에게 반환 (Cache Miss)

💡 Write Back
1. 웹서버는 모든 데이터를 Cache 서버에 저장
2. Cache 서버에 특정 시간 동안 데이터가 저장됨
3. Cache 서버에 있는 데이터를 DB에 저장
4. DB에 저장된 Cache 서버의 데이터를 삭제
```
