# webKR
** 1) Структура HTTP запроса, передающего логин и пароль пользователя **
  ```
  POST /test HTTP/1.1
  Host: foo.example.com
  Content-type: application/x-www-form-urlencoded
  Content-length: 24
  
  login=root&password=root
  ```
2) Написать код HTML-страницы, отправляющей номер вопроса и выбранный вариант ответа (латинская буква от “A” до “F”) после получения некоего текста.

  ```
  <!DOCTYPE html>
<html lang="en">
<head onload="getData()">
    <meta charset="UTF-8">
</head>

<form action="test.php" method="POST">
<ol>
    <li>
        <input type="hidden" value=1/>
        <label for="first" id="firstQ">first question</label>
        <select name="1" id="first">
            <option>A</option>
            <option>B</option>
            <option>C</option>
            <option>D</option>
            <option>E</option>
            <option>F</option>
        </select>


    </li>
    <li>
        <input type="hidden" value=2/>
        <label for="second">second question</label>
        <select name="2" id="second">
            <option>A</option>
            <option>B</option>
            <option>C</option>
            <option>D</option>
            <option>E</option>
            <option>F</option>
        </select>
    </li>
    <li>
        <input type="hidden" value=3/>
        <label for="third">third question</label>
        <select name="3" id="third">
            <option>A</option>
            <option>B</option>
            <option>C</option>
            <option>D</option>
            <option>E</option>
            <option>F</option>
        </select>
    </li>
</ol>
    <button type="submit">lets go</button>
</form>
</body>
</html>
  
  
  ```
    
3)  написать на JS функцию, которая на странице заменяет все тестовые поля ввода на кнопки
  ```
  function replace(){
  let nodes = document.querySelectorAll("input, textarea");
  for (let i = 0; i < nodes.length; i++){
      if (nodes[i].type === "text" || nodes[i].type === "textarea"){
        let button = document.createElement("button");
        nodes[i].replaceWith(button);
      }
    }
  }
  
  ```
4) написать css правило, которое повернёт все картинки в форме с id=sampleForm на 90 градусов по часовой стрелке
  ```
  #sampleForm img{
    transform: rotate(90deg);
  }
  ```

5) Написать CSS правило, которое будет обводить все картинки в классе news в рамку при наведении мышю
```
  .news:hover{
    borded-style: solid;
    border-color: red;
  }
  ```

6)  Jquery ajax запрос на сервлет, ответ от сервлета - объект json, вывести на страницу firstname, lastname, img_url
```
$(document).ready(function() {
  $.ajax({
    url: "/someServlet",
    async: true,
    type: "GET",
    success: function (response){
      let data = JSON.parse(response);
      document.writeln(data.firstName);
      document.writeln(data.lastName);
      document.writeln(data.img_url);
    }
  })
})
```
8)  Написать JS-функцию, которая запрещает вводить любые символы, кроме цифр и букв латинского алфавита
```
let regex = /[^0-9A-Za-z]/;
let inputs = document.querySelectorAll("input, textarea");
for (let i = 0; i < inputs.length; i++){
   if (inputs[i].type === "text" || inputs[i].type === "textarea"){
       inputs[i].oninput = function(){
       this.value = this.value.replace(regex, "");
     }
   }
}
   ```
8) Реализовать функцию на JavaScript, которая будет закрывать текущее окно, если в нем открыт https://www.google.ru
  ```
  function closeGoogle(){
    let link = document.URL;
    if (link === "https://www.google.ru"){
      window.close();
    }
  }
  ```
9) Написать js функцию, которая заменяет содержимое <div> с именем класса “nyan” на изображение по ссылке:
  ```
  function replace(){
    let img = document.createElement('img');
    img.src = 'http://www.example.com/nyancat.gif';
    let divs = docuemnt.querySelectorAll(".nyan");
    for (let i = 0; i < divs.length; i++){
      divs[i].innerHTML = '';
      divs[i].appendChild(img);                              
    }
  }
  ```
10)  Правило css, меняющее цвет фона на желтый, если ссылка посещена и не лежит в классе “news”
   ```
   a:visited:not(.news){
      color: yellow;                                 
   }
   ```
11) php скрипт, который достаёт из get запроса имя и фамилию и приветствует пользователя, выводя html страницу 
  ```
   <?php                                         
   $name = $_GET['name'];
   $surname = $_GET['surname']
   echo "Hello " . $name . " " . $surname; 
   ?>
  ```
12) написать на php класс
  ```
    <?php

    class User{
      private $name;
      private $surname;

      function __constructor($name, $surname){
        $this->name = $name;
        $this->surname = $surname;
      }

      function info(){
        return $this->name . " " . $this->surname;
      }
    }

    ?>
  ```
13) Написать конфигурацию сервлета (org.xxx.MyServlet) с помощью аннотации. Сервлет должен принимать все запросы от файлов .html .xhtml
  ```
  @WebServlet(name="MyServlet", value="/my-servlet", urlPatters = {"*.html","*.xhtml"})
  ```
14) сервлет перенаправляющий все запросы на страницу google
  ```
  class ToGoogleServlet extends HttpServlet{
        public void service(HttpServletRequest request, HttpServletResponse response) throws IOException, ServletException{
                response.sendRedirect("http://google.com1;")
        }
  }
  ```
15) Написать JSP страницу, которая будет возвращать количество сессий, обратившихся к ней за последние 60 секунд и формировать вывод в HTML
```
@WebServlet(name = "seconds", value = "/seconds")
public class SecondsListener extends HttpServlet implements HttpSessionListener {
    private static List<Long> list = new ArrayList<>();

    @Override
    public void sessionCreated(HttpSessionEvent se){
        list.add(System.currentTimeMillis());
    }

    @Override
    public void sessionDestroyed(HttpSessionEvent se){

    }

    public long getCount(){
        return list.stream().filter(time -> System.currentTimeMillis() - time <= 60 * 1000).count();
    }

    @Override
    public void doGet(HttpServletRequest request, HttpServletResponse response) throws IOException, ServletException {
        ServletContext context = request.getServletContext();

        context.setAttribute("count", getCount());

        request.getRequestDispatcher("/test.jsp").forward(request, response);

    }

}
  
```
web.xml                                                      
```    
<listener>
  <listener-class>SecondsListener</listener-class>
</listener>
                                                      
``` 
jsp
```
  <%
    out.println(request.getServletContext().getAttribute("count")); 
  %>  
``` 
  
16) Написать сервлет, который принимает из http запроса параметр name и выводит его. Если параметр не обнаружен то вывести Anonymous user
  ```
  class HelloServlet extends HttpServlet{
        public void service(HttpServletRequest request, HttpServletResponse response) throws IOException, ServletException{
  
                String name = request.getParameter("name");
                PrintWriter out = response.getWriter();
 
                name = name==null?"Anonymous user":name;
                out.println("<h1>Hello " + name + "</h1>");
                out.close();
        }
  }
  ```
17)  Страница JSP, проверяющая есть ли /какой-то параметр/ в запросе и если нету - выводящая сообщение об ошибке
  ```
  <%@ page contentType="text/html; charset=UTF-8" pageEncoding="UTF-8" language="java" %>
  <%= request.getParameter("someParameter") == null ? "400 - you didn't set the Parameter" : request.getParameter("someParameter") %>
  ```
18) Код фильтра запросов, запрещающий доступ к приложению неавторизированным пользователям(у неавт пол в запросе отсутствует заголовок x-application-user)
```
public class TestFilter implements Filter {
@Override
public void init(FilterConfig filterConfig) throws ServletException {
    Filter.super.init(filterConfig);
}
@Override
public void doFilter(ServletRequest servletRequest, ServletResponse servletResponse, FilterChain filterChain) throws IOException, ServletException {
    HttpServletRequest request = (HttpServletRequest) servletRequest;
    String auth = request.getHeader("x-application-user");
    if (auth == null || auth.equals("")){
         PrintWriter out = servletResponse.getWriter();
         servletResponse.setContentType("text/html; charset=UTF-8");
         out.println("you didnt authorize");
     }
     else{
        filterChain.doFilter(servletRequest, servletResponse);
     }
    }
@Override
public void destroy() {
    Filter.super.destroy();
  }
}
```
    
19)  Код jsp-страницы показывающий содержимое корзины юзера. Содержимое корзины - коллекциия объектов класса ShoppingItem который содержит имя, стоимость и количество заказанного товара - хранится в отдельном managed bean. 
```
   <@page contentType="text/html; charset=UTF-8" pageEncoding="UTF-8" language="java" %>
   <@page import ShoppingItem %>
   <@page import java.util.Collection %>
   <jsp:useBean name="managed" class="ShoopingItem" />
   <html>
      <head>
        <meta charset="UTF-8">
     </head>
     <body>
       <table>
          <thead>
             <tr>
                <th>
                  name
                </th>
                <th>
                  price
                </th>
                <th>
                  count
                </th>
             </tr>
          </thead>
          <% Collection<ShoppingItem> basket = managed.getBasket();
          for (ShoppingItem current : basket){ %>
              <tr>
                <td> <%current.getName()%></td>
                <td> <%current.getPrice()%></td>
                <td> <%current.getCount()%></td>
              </tr>  
          <%}%>
       </table
     </body>
   </html>
   
```    
20) написать css правило, которое при клике на ссылку добавляет ей подчеркивание, всем кроме ссылок в теге h1
  ```
  a:active:not(h1){
    text-decoration-line: underline;
  }
  ```
21) Написать php скрипт, формирующий форму для ввода логина и пароля и отправляющий запрос сервису authorize.php с помощью UserAgent. Если пользователь корректный, то скрипт должен редиректить на страницу pagename.php.

**html**

```
<form method="POST" onsubmit="authorize.php">
  <input id="login" type="text"/>
  <input id="password" type="text"/>
  <button type="submit">send</button>
</form>
```

**js**
```
function send() {
  let login = document.getElementById("login");
  let password = document.getElementById("password");
  request.post("authorize.php")
  .send({login, password})
  .then(res => {
    location.href = "pagename.php"
  })
  .catch(err => {
    console.log(err)
  })
}
```


22)  Написать html страницу и сервлет, возвращающий странице количество активных сессий
```
@WebServlet(name = "listener", value = "/listener")
public class ListenerServlet extends HttpServlet implements HttpSessionListener{
    private static int counter;

    public void sessionCreated(HttpSessionEvent se) {
        counter++;
    }

    public void sessionDestroyed(HttpSessionEvent se) {
        counter--;
    }

    public int getCounter(){
        return counter;
    }

    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException{

        ServletContext context = request.getServletContext();

        context.setAttribute("sessions", counter);

        request.getRequestDispatcher("/test.jsp").forward(request, response);
    }
}   
```
web.xml и jsp аналогично вопросу про количество активных сессией за последние 60 секунд
         
         
23)  с помощью jquery посчитать количество div с классом lecture содержащие «де-факто»
         ```
         
         
         $("div.lecture:contains('де-факто')").length;
