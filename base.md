# Spring / tiles / Mybatis 3가지 공부

# 궁금한것
1. Controller와 Service 스캔을 따로두는이유??

# 궁금한것에 대한 자료 & 공부

```
1.
<context:component-scan base-package="com.ex.ex1.*" use-default-filters="false">
	<context:include-filter        type="annotation" expression="org.springframework.stereotype.Controller" />
</context:component-scan>
// 컨트롤러만 스캔한다. 참고로 default 는 @Controller , @Service , @Repository , @Component이다.
여기서 use-default-filters 는 default애들을 스캔할껀지 확인하는 거다.
false 는 스캔하지 않고 true는 스캔한다.

2.
	<bean class="org.springframework.web.servlet.view.UrlBasedViewResolver">
		<property name="viewClass" value="org.springframework.web.servlet.view.JstlView"/>
		<property name="prefix" value="/WEB-INF/views/"/>
		<property name="suffix" value=".jsp"/>
	</bean>

여기서 UrlBasedViewResolver는 사용자들에게 보여줄 view를 생성할 때, prefix와 suffix 를 지정할수 있다.

예를들어 ModelAndView 에 ViewName이 index 라면 자동으로 prefix 에있는 곳에 index.jsp를 찾아준다.

3.
<resources mapping="/css/**" location="/resources/css/">
이것은 예를들어 jsp에서 /css/base.css 일떄 자동으로 주소를 resources/css/base.css 로 가준다. 하지만 실무에선 별로 안쓰인다고 한다.

4. Tiles
tiles 란 뷰 단의 탑, 사이드 , 메인 , 하단 등 을 페이지 include 방식으로 나누는 기존 구조를 쉽게 적용하기 위한 템플릿 프레임워크입니다. xml로 하여 편하게 작업할 수 있다.

5. Lombok
lombok이란 getter setter toString 등 여러가지를 합쳐놓은게 lombok이다. 사용방법은 우선 의존 라이브러리를 다운 받고 @getter @setter 등등을 사용할 수 있다. 전체다 사용하는 방법은 @Data 이다.


```
https://isstory83.tistory.com/117 : View Resolver
https://its-easy.tistory.com/13 : Spring Tiles
