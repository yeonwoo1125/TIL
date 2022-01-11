# 2022-01-11

### **라이브러리 살펴보기**

- Gradle은 의존 관계가 있는 라이브러리를 함께 다운함

**스프링 부트 라이브러리**

- spring-boot-starter-web
    - spring-boot-starter-tomcat : 톰캣(웹서버)
    - spring-webmvc : 스프링 웹 MVC
- spring-boot-starter-thymeleaf : 타임리트 템플릿 엔진(View)
- spring-boot-starter(공통) : 스프링 부트 + 스프링 코어 + 로깅
    - spring-boot
        - spring-core
    - spring-boot-starter-logging
        - logback, slf4j

**테스트 라이브러리**

- spring-starter-test
    - junit : 테스트 프레임워크
    - mockito : 목 라이브러리
    - assertj : 테스트 코드를 좀 더 편하게 작성하게 도와주는 라이브러리
    - spring-test : 스프링 통합 테스트 지원
    

### **View 환경설정**

- Welcom Page 만들기(resources/static/index.html) - home 화면
    - 아직은 링크를 타면 errorPage가 뜸

```java
<!DOCTYPE HTML>
<html>
<head>
    <title>Hello</title>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8"/>
</head>

<body>
    Hello
    <a href="/hello">hello</a>
</body>
</html>
```

- 스프링 부트가 제공하는 Welcome Page 기능
    - static/index.html을 올려두면 Welcome page 기능을 제공

- Hello.Hellospring/controller/HelloController
    
    ```java
    package Hello.hellospring.controller;
    
    import org.springframework.stereotype.Controller;
    import org.springframework.ui.Model;
    import org.springframework.web.bind.annotation.GetMapping;
    
    @Controller
    public class HelloController {
    
        @GetMapping("hello")
        public String hello(Model model){
            model.addAttribute("data","hello!!");
            return "hello";
        }
    }
    ```
    
    - model.addAttribute("data","hello!!"); - data는 key, hello는 value
    - return “hello”는 템플릿에 있는 이름이 똑같은 파일 실행→ hello.html을 실행시킴
        - 컨트롤러에서 리턴값으로 문자 반환하면 화면을 찾아서 처리
            - 스프링 부트 템플릿 엔진 기본 viewName 매핑
                - resouers:templates/+{viewName}+.html

- resoures/templates/hello.html
    
    ```java
    <!DOCTYPE HTML>
    <html xmlns:th="http://www.thymeleaf.org">
    	<head>
        <title>Hello</title>
        <meta http-equiv="Content-Type" content="text/html; charset=UTF-8"/>
    	</head>
    <body>
    	<p th:text="'안녕하세요.   '+${data}">안녕하세요. 손님</p>
    </body>
    </html>
    ```
    
    - <html xmlns:th="http://www.thymeleaf.org"> - thymeleaf 템플릿 문법을 사용할 수 있게 도와줌
    - <p th:text - 템플릿 문법 사용
    
- [http://localhost:8080/hello](http://localhost:8080/hello) 에 접속

![welcomepage](/img/welcomepage.png)

- hello!!는 HelloController에서 전달된 value가 ${data}로 치환됨
