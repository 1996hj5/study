# AOP(Aspect Oriented Programming)
> 관점 지향 프로그래밍
> - 공통 기능과 핵심기능을 따로 나눠 코드를 수행
> - 다중 상속의 한계가 있어 나온게 AOP다.
> - OOP를 더 OOP답게 해준다.

> Aspect : 공통 기능
> Advice : Aspect의 기능 자체
> Jointpoint : Advice를 적용해야 하는 부분(ex. 필드 메소드)(스프링에서는 메소드에만 해당)
> Pointcut : Jointpoint 부분으로 실제로 Advice가 적용된 부분
> Weaving : Advice를 핵심 기능에 적용하는 행위

## Aop 구현방법
1. proxy 이용
> 즉, 컴파일하면서 모든 기능들을 불러와 가상의 proxy가 수행


## Aop 구현 종류
1. XML 이용
2. @Aspect 이용

## XML 기반의 AOP구현
1. &lt;aop:before&gt; : 메소드 실행 전에 advice 실행
2. &lt;aop:after-returning&gt; : 정상적으로 메소드 실행 후에 proxy 실행
3. &lt;aop:after-throwing&gt; : 메소드 실행중 exception 발생시 advice 실행
4. &lt;aop:after&gt; : 메소드 실행중 exception 발생하여도 advice 실행
5. &lt;aop:around&gt; : 메소드 실행 전/후 및 exception 발생시 advice 실행

## @Aspect 를 이용한 Aop 구현
> 3가지 표현식(AspectJ 문법)
> 1. \* : 모든
> 2. \. : 현재
> 3. \.. : 0개 이상

> 1. Execution
> 2. within
> 3. bean

> Execution (ex) : 접근권한 반환값 주소 메소드명(파라미터)
> - @Pointcut("execution(public void get*(..))") : 퍼블릭 void인 모든 get메소드
> - @Pointcut("execution(* com.java.ex.*.*())") : com.java.ex 패키지에 파라미터가 없는 모든 메소드
> - @Pointcut("execution(* com.java.ex..*.*())") : com.java.ex 패키지 & com.java.ex 하위 패키지에 파라미터가 없는 모든 메소드

> within (ex) : 주소
> - @Pointcut("within(com.java.ex.*)") : com.java.ex 패키지 안에 있는 모든 메소드
> - @Pointcut("within(com.java.ex..*)") : com.java.ex 패키지 및 하위 패키지 안에 있는 모든 메소드

> bean (ex) : 빈만 적용
> - @Pointcut("bean(student)") : student 빈에만 적용

# Security

# Other 어노테이션
1. @PathVariable : 시맨틱 url 파리미터를 얻을 수 있다.
> ex)
> - /ex/{ex1}  -- @PathVariable String ex1

2. 폼 데이터 검증
> - client에서 js로이용하여 검증하지만 서버 단에서는 이 메소드을 이용한다.
> - Validator : 추상 인터페이스 이므로 직접적인 메소드를 구현해야한다.
>> - 2가지의 추상 메소드가 나타나며
>> - boolean supports(Class<?> arg0)
>> - void validate(Object obj, Error errors) 가 나타단다.

여기까지가 기본적인 개념이지만
스프링 프레임워크에서는 어노테이션을 이용한다.
> - @Valid , @InitBinder





