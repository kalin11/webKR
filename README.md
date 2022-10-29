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
  .news:hover{
    borded-style: solid;
    border-color: red;
  }

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
10) 
