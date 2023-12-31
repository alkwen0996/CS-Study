## 📝 Interview

#### 트랜잭션의 특성 4가지에 대해 설명하세요.

```
원자성, 일관성, 격리성, 지속성이 있으며, 이를 한꺼번에 ACID 특징이라고 합니다.
원자성이란 트랜잭션과 관련된 일이 모두 수행되었거나 되지 않았거나를 보장하는 특징입니다.
일관성이란 허용된 방식으로만 데이터를 변경해야 하는 것을 의미합니다.
격리성이란 트랜잭션 수행 시 서로 끼어들지 못하는 것을 말합니다. 복수의 병렬 트랜잭션은 서로 격리되어 마치 순차적으로 실행되는 것처럼 작동되어야 합니다.
지속성이란 성공적으로 수행된 트랜잭션은 영원히 반영되어야 하는 것을 의미합니다. 데이터베이스에 시스템 장애가 발생해도 원래 상태로 복구하는 회복 기능이 있어야 함을 뜻하며, 이를 위해 체크섬, 저널링, 롤백 등의 기능을 제공합니다.
```

<br>

#### 커밋과 롤백에 대해 설명하세요.

```
💡 커밋
여러 쿼리가 성공적으로 처리되었다고 확정하는 명령어입니다.
트랜잭션 단위로 수행되며 변경된 내용이 모두 영구적으로 저장되는 것을 말합니다.
커밋이 수행되었다는 의미는, 하나의 트랜잭션이 성공적으로 수행되었다는 의미와 같습니다.
update, insert, delete의 쿼리가 하나의 트랜잭션 단위로 수행되고 이후에 데이터베이스에 영구저장됩니다.

💡 롤백
에러나 여러 이슈 때문에 트랜잭션을 전으로 돌려야 할 때 사용하는 명령어입니다.
트랜잭션으로 처리한 하나의 묶음 과정을 일어나기 전으로돌리는 일을 말합니다.

이러한 커밋과 롤백 덕에 데이터의 무결성이 보장됩니다.
또한 데이터 변경 전에 변경 사항을 쉽게 확인할 수 있고 해당 작업을 그룹화할 수 있습니다.
```
