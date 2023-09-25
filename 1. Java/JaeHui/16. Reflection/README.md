# Reflection

리플렉션이란 구체적인 클래스 타입을 알지 못하더라도 그 클래스의 메서드, 타입, 변수들에 접근할 수 있도록 해주는 자바 API입니다. <br>
컴파일 시간이 아닌 실행 시간에 동적으로 특정 클래스의 정보를 추출할 수 있는 프로그래밍 기법입니다. <br>
리플렉션을 사용하여 가져올 수 있는 정보는 `Class`, `Constructor`, `Method`, `Field` 가 있습니다.<br><br>

리플렉션은 동적으로 클래스를 사용해야 할 경우, 즉 작성 시점에는 어떤 클래스를 사용할지 모르지만 런타임 시점에서 가져와 실행하는 경우 필요합니다. <br>
프레임워크나 IDE에서 Spring Annotation, IntelliJ 자동 완성 기능 등의 이런 동적 바인딩을 이용한 기능을 제공합니다. <br><br>

## [사용 방법](https://github.com/WeareSoft/tech-interview/blob/master/contents/java.md#java%EC%9D%98-%EB%A6%AC%ED%94%8C%EB%A0%89%EC%85%98-%EC%9D%B4%EB%9E%80)

`Class.forName("클래스이름")`을 통해 인스턴스를 생성할 수 있고 클래스의 정보를 가져올 수 있습니다.<br>

```java
public class DoHee {
    public String name;
    public int number;
    public void setDoHee (String name, int number) {
      this.name = name;
      this.number = number;
    }
    public void setNumber(int number) {
        this.number = number;
    }
    public void sayHello(String name) {
      System.out.println("Hello, " + name);
  }
}
```

```java
import java.lang.reflect.Method;
import java.lang.reflect.Field;

public class ReflectionTest {
    public void reflectionTest() {
        try {
            Class myClass = Class.forName("DoHee");
            Method[] methods = myClass.getDeclaredMethods();

            /* 클래스 내 선언된 메서드의 목록 출력 */
            /* 출력 : public void DoHee.setDoHee(java.lang.String,int)
                     public void DoHee.setNumber(int)
                     public void DoHee.sayHello(java.lang.String) */
            for (Method method : methods) {
                System.out.println(method.toString());
            }

            /* 메서드의 매개변수와 반환 타입 확인 */
            /* 출력 : Class Name : class DoHee
                     Method Name : setDoHee
                     Return Type : void */
            Method method = methods[0];
            System.out.println("Class Name : " + method.getDeclaringClass());
            System.out.println("Method Name : " + method.getName());
            System.out.println("Return Type : " + method.getReturnType());

            /* 출력 : Param Type : class java.lang.String
                     Param Type : int */
            Class[] paramTypes = method.getParameterTypes();
            for(Class paramType : paramTypes) {
                System.out.println("Param Type : " + paramType);
            }

            /* 메서드 이름으로 호출 */
            Method sayHelloMethod = myClass.getMethod("sayHello", String.class);
            sayHelloMethod.invoke(myClass.newInstance(), new String("DoHee")); // 출력 : Hello, DoHee

            /* 다른 클래스의 멤버 필드의 값 수정 */
            Field field = myClass.getField("number");
            DoHee obj = (DoHee) myClass.newInstance();
            obj.setNumber(5);
            System.out.println("Before Number : " + field.get(obj)); // 출력 : Before Number : 5
            field.set(obj, 10);
            System.out.println("After Number : " + field.get(obj)); // 출력 : After Number : 10
        } catch (Exception e) {
            // Exception Handling
        }
    }

    public static void main(String[] args) {
        new ReflectionTest().reflectionTest();
    }
}
```
