**Backend на Spring**:
- **Spring Boot** для создания REST API, которое будет обрабатывать запросы от фронтенда.
- **Spring Data JPA** для работы с базой данных (например, для хранения информации о товарах, избранном и контактных данных).
- **Spring Security** для обеспечения безопасности (например, для аутентификации и авторизации пользователей).
- Возможно, использование **Spring MVC** для работы с веб-страницами.

**Frontend**:
- Вы можете использовать **HTML/CSS/JavaScript** для создания интерфейса. Для одностраничного приложения идеально подойдет фреймворк **React**, **Vue.js** или **Angular**.
- Фронтенд будет обращаться к backend через **REST API**.

|Слой|Что делает|Где в Spring|
|---|---|---|
|Контроллеры|Отвечают за входящие HTTP-запросы|`controller/`|
|Сервисы|Бизнес-логика|`service/`|
|Репозитории|Работа с базой данных|`repository/`|
|Модели (Entity)|Отражение структуры таблиц в БД|`model/`|
|DTO|Формат обмена данными с фронтом|`dto/`|
|Конфигурация|Настройки Spring, бинов и т.д.|`config/` (если нужно)|

1. Controller (обработка конечного http-запрос)
2. Service (описание бизнес-логики)
3. Repository (работа с базами данных)
4. Model (представление таблиц БД в java - классы)
5. DTO (передача данных между фронтом и бэком) //p.s. это буквально модель которую мы в случае чего передаём во фронт

shop/
├── src/
│   └── main/
│       ├── java/
│       │   └── com.example.shop/
│       │       ├── controller/
│       │       │   ├── ProductController.java // /product
│       │       │   ├── ContactController.java // /contact
│       │       │   └── MainController.java // / (index.html)
│       │       │
│       │       ├── service/
│       │       │   └── ProductService.java //вся бизнес логика
│       │       │
│       │       ├── repository/
│       │       │   └── ProductRepository.java // достаём данные их БД
│       │       │
│       │       ├── model/
│       │       │   └── Product.java // само представление базы данных
│       │       │
│       │       ├── dto/
│       │       │   └── ProductDTO.java // 
│       │       │
│       │       └── ShopApplication.java
│       │
│       └── resources/
│           ├── static/              # если фронт простой (HTML/JS/CSS)
│           │   ├── index.html
│           │   └── js/
│           ├── templates/           # если Thymeleaf
│           │   └── index.html
│           ├── application.properties
│           └── data.sql             # тестовые товары (если нужно)
│
├── pom.xml

Надо посмотреть что такое докер компост 

- [ ] Надо сделать макет сайта
- [ ] Описать модели(базы данных которые будут у меня )
- [ ] надо посмотреть курс по фронту(хотябы чтобы понимать что там происходит https://www.youtube.com/watch?v=BVIffUyYlUk&pp=ygUHYW5ndWxhcg%3D%3D)
Товары:

| id              |     |
| --------------- | --- |
| name            |     |
| description     |     |
| photo(any size) |     |
|                 |     |
