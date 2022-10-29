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
  let nodes = document.querySelectorAll("input, textarea");
  for (let i = 0; i < nodes.length; i++){
    if (nodes[i].type === "text" || nodes[i].type === "textarea"){
      let button = document.createElement("button");
      nodes[i].replaceWith(button);
    }
  }
  
  ```
