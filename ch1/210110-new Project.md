
### 오늘 본 강의 제목 
1. 강의 소개
2. 프로젝트 생성
    - 사전 준비물
        - IntelliJ, Java 11
        - 해당 사이트에서 spring 프로젝트 기초 작성
        
       🔗 [Spring Initializr](https://start.spring.io/)
        
        ![springInitializr](/img/springInitializr.png)
        
        - Gradle Project - 요즘 대세는 대부분 Gradle로 사용됨
        - Spring Boot - M1은 아직 상용화 안됨? , SNAPSHOT은 개발 중
        - Group - 기업 도메인명 같은 거 씀
        - Artifact - 빌드된 결과물, 프로젝트 명과 유사 
        
        <br>
        
        ![dependencies](/img/dependencies.png)
        
        - **Dependencies - 어떤 라이브러리를 사용할지 적는 부분 매우 중요**
            - Spring Web - 웹사이트를 만들기 때문에 사용
            - Thymeleaf - HTML을 사용하기 위한 템플릿 엔진, 회사마다 다름 <br>
    - 설정을 마친 후 압축을 풀어 open folder
    - run을 누르면 실행됨
    - [http://localhost:8080/](http://localhost:8080/) 를 웹사이트에 입력하면 Error Page가 뜸 그럼 정상적으로 실행된거.
    
    ![errorPage](/img/errorPage.png)
