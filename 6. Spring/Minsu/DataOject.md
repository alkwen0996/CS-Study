## DAO & DTO & VO & Entity

---

### DAO ( Data Access Object )

`DB`의 데이터에 접근할 때 사용하기 위한 객체로 직접 `DB`에 접근하여 데이터를 삽입, 삭제, 조회 등 조작할 수 있는 기능을 수행할 때 사용된다. `DB` 접근을 하기 위한 로직과 비즈니스 로직을 분리하기 위해 사용된다.

<br>

### DTO ( Data Transfer Object )

`DTO` 는 계층 간 데이터를 교환하기 위해 사용하는 객체로 로직을 가지지 않는 순수한 데이터 객체를 말한다. `getter/setter 메서드` 를 가질 수 있으며 주로 `View`와 `Controller` 사이에서 데이터를 주고 받을 때 활용한다. 단, 이 외의 비즈니스 로직은 포함하지 않는다.

```java
@Getter
public class UserRequest {
	private Long seq;
	private String id;
	private String nickname;
	private String email;
	private String password;

	public void setPassword(String password){
		this.password = password;
	}

	public User toEntity(Byte skin, String salt) {
		return User.builder()
			.seq(seq)
			.id(id)
			.nickname(nickname)
			.email(email)
			.password(password)
			.salt(salt)
			.catSkin(skin)
			.build();
	}

}
```

<br>

### VO ( Value Object )

`DTO`와 달리 `VO` 는 Read-Only 속성을 갖는 값 자체를 표현하는 객체를 말한다. `VO` 객체들은 객체의 주소가 달라도 값이 같으면 동일한 것으로 여긴다. `getter 메서드` 와 함께 비즈니스 로직도 포함될 수 있다. 하지만, `setter 메서드`는 가지지 않는다. 또한, 값 비교를 위해 `equals()`와 `hashCode()` 를 오버라이딩 해줘야 한다.

<br>

### Entity

실제 `DB 테이블`과 `1:1`로 매핑되는 핵심 클래스이다. 이를 기준으로 테이블이 생성되고 스키마가 변경된다. 따라서, 절대로 `Entity`를 요청이나 응답값을 전달하는 클래스로 사용하면 안된다. `Entity`는 `id`로 구분되며 비즈니스 로직을 포함할 수 있다. `DTO` 처럼 `setter`를 가지는 경우 가변객체로 활용될 수도 있다.

```java
@Getter
@Entity
@Table(name = "todos")
public class Todo {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long seq;

    @ManyToOne
    @JoinColumn(name="users_seq")
    private User user;

    @Column(name = "title")
    private String title;

    @Column(name="status")
    private Byte status;

    @Column(name = "total_second")
    private String totalSecond;

    @ManyToOne
    @JoinColumn(name = "categories_name")
    private Category category;

    @Builder
    public Todo(final Long seq, final User user, final String title, final Byte status, final String totalSecond, final Category category) {
        this.seq = seq;
        this.user = user;
        this.title = title;
        this.status = status;
        this.totalSecond = totalSecond;
        this.category = category;
    }
}
```

<br>

### Repository vs DAO

`Repository` 는 엔티티 객체를 보관하고 관리하는 저장소이며 `DAO`는 데이터에 접근하도록 `DB` 접근 관련 로직을 모아둔 객체이다. 개념적으로는 차이가 있으나 실제 개발시에는 비슷하게 사용되곤 한다.

<br>

### [ Reference ]

[DAO (Data Access Object)](https://hudi.blog/data-access-object/)
