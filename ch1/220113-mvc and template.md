# 2022-01-13

### MVC와 템플릿 엔진

- MVC : Model, View, Controller
- 요즘은 View와 Controller를 분리함

- Hello.Hellospring/controller/HelloController
    
    ```java
    ...
    @GetMapping("hello-mvc")
        public String helloMvc(@RequestParam("name") String name, Model model){
            model.addAttribute("name",name);
            return "hello-template";
        }
    ```
    

- resoures/templates/hello-template.html
    
    ```java
    <html xmlns:th="http://www.thmeleaf.org">
        <body>
            <p th:text="'hello '+${name}">Hello! empty</p>
        </body>
    </html>
    ```
    

<br>- [http://localhost:8080/hello-mvc](http://localhost:8080/hello-mvc) 로 이동 시 에러 페이지 보임

![Untitled](/img/hello-mvcError.png)

- WARRNING 문구 : Required request parameter 'name' for method parameter type String is not present
    - name 파라미터가 넘어오지 않았기 때문
- [http://localhost:8080/hello-mvc?name=spring](http://localhost:8080/hello-mvc?name=spring) 로 변경 시 제대로 나옴
    - 파라미터를 넘길 때는 **?변수이름=value** 형식으로 넘겨줌(Get 방식)<br>
    ![Untitled](/img/hello-mvc.png)
