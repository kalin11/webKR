# webKR
1) Структура HTTP запроса, передающего логин и пароль пользователя
  ```
  POST /test HTTP/1.1
  Host: foo.example.com
  Content-type: application/x-www-form-urlencoded
  Content-length: 24
  
  login=root&password=root
  ```
2) Написать код HTML-страницы, отправляющей номер вопроса и выбранный вариант ответа (латинская буква от “A” до “F”) после получения некоего текста.
  
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
  #sampleForm{
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
7)  Написать JS-функцию, которая запрещает вводить любые символы, кроме цифр и букв латинского алфавита
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
14) сервлет перенаправляющий все запросы на страницу google
  ```
  class ToGoogleServlet extends HttpServlet{
        public void service(HttpServletRequest request, HttpServletResponse response) throws IOException, ServletException{
                response.sendRedirect("http://google.com1;")
        }
  }
  ```
15) Написать JSP страницу, которая будет возвращать количество сессий, обратившихся к ней за последние 60 секунд и формировать вывод в HTML
  
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
18) Код фильтра запросов, запрещающий доступ к приложению неавторизированным пользователям(у неавт пол в запросе отсутствует заголовок x-application-user)
19)  Код jsp-страницы показывающий содержимое корзины юзера. Содержимое корзины - коллекциия объектов класса ShoppingItem который содержит имя, стоимость и количество заказанного товара - хранится в отдельном managed bean. 
20) написать css правило, которое при клике на ссылку добавляет ей подчеркивание, всем кроме ссылок в теге h1
21) Написать php скрипт, формирующий форму для ввода логина и пароля и отправляющий запрос сервису authorize.php с помощью UserAgent. Если пользователь корректный, то скрипт должен редиректить на страницу pagename.php.
22)  Написать html страницу и сервлет, возвращающий странице количество активных сессий
23)  с помощью jquery посчитать количество div с классом lecture содержащие «де-факто»
