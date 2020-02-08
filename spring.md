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

# Security
1. 사용하는 이유
> - 인증 및 접근 할때에 사용한다. ex)로그인 / 페이지 접근
> - 이전 원시적인 방법으로는 로그인한 유저가 아닌거를 쿠키나 세션으로 판단하여 처리를 하였다.

이것도 java 와 xml 방법이 있다.
현재는 xml 방법으로 공부하고 있지만 java 방법을 공부하여 할 생각이다.

## xml
1. 필터 등록
```
 <filter>
  <filter-name>
  springSecurityFilterChain
  </filter-name>
  <filter-class> org.springframework.web.filter.DelegatingFilterProxy
  </filter-class>
  </filter>
    <filter-mapping>
     <filter-name>
     springSecurityFilterChain
     </filter-name>
     <url-pattern>
     /*
     </url-pattern>
     </filter-mapping>
```
2. 설정파일(web.xml) 설정
3. (로그인 중복방지를 위한 기능) 리스너 추가
```
<listener>
  <listener-class> org.springframework.security.web.session.HttpSessionEventPublisher
  </listener-class>
</listener>
```
4. xml 설정 (security-context.xml)
- login-page : 로그인 페이지 주소를 지정
- username-parameter : 로그인 페이지 form에 있는 username을 저장할 변수이름 지정 (ID값)
- password-parameter : 로그인 페이지 form에 있는 password를 저장할 변수이름 지정
- login-processing-url : 로그인 페이지 form에 action에 입력할 주소 지정

ex)
 ```
<form name="loginform" method="post" action="loginProcess">
```
- default-target-url : 로그인 성공시 호출할 주소 지정
- authentication-failure-url : 로그인 실패시 호출할 주소 지정
