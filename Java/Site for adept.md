**Backend на Spring**:
- **Spring Boot** для создания REST API, которое будет обрабатывать запросы от фронтенда.
- **Spring Data JPA** для работы с базой данных (например, для хранения информации о товарах, избранном и контактных данных).
- **Spring Security** для обеспечения безопасности (например, для аутентификации и авторизации пользователей).
- Возможно, использование **Spring MVC** для работы с веб-страницами.

**Frontend**:
- Вы можете использовать **HTML/CSS/JavaScript** для создания интерфейса. Для одностраничного приложения идеально подойдет фреймворк **React**, **Vue.js** или **Angular**.
- Фронтенд будет обращаться к backend через **REST API**.

| Слой            | Что делает                        | Где в Spring           |
| --------------- | --------------------------------- | ---------------------- |
| Контроллеры     | Отвечают за входящие HTTP-запросы | `controller/`          |
| Сервисы         | Бизнес-логика                     | `service/`             |
| Репозитории     | Работа с базой данных             | `repository/`          |
| Модели (Entity) | Отражение структуры таблиц в БД   | `model/`               |
| DTO             | Формат обмена данными с фронтом   | `dto/`                 |
| Конфигурация    | Настройки Spring, бинов и т.д.    | `config/` (если нужно) |

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
│       │       │   └── ContactController.java // /contact
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

![[Pasted image 20250512111801.png]]

- model - как будет выглядеть база данных, только на java
Пример:
```java
@Entity
@Table(name = "tutorials")
public class Tutorial {

    @Id
    @GeneratedValue
    private long id;

    @Column(name = "title")
    private String title;

    @Column(name = "description")
    private String description;

    @Column(name = "published")
    private boolean published;

    public Tutorial() {

    }

    public Tutorial(String title, String description, boolean published) {
        this.title = title;
        this.description = description;
        this.published = published;
    }

    public long getId() {
        return id;
    }

    public String getTitle() {
        return title;
    }

    public void setTitle(String title) {
        this.title = title;
    }

    public String getDescription() {
        return description;
    }

    public void setDescription(String description) {
        this.description = description;
    }

    public boolean isPublished() {
        return published;
    }

    public void setPublished(boolean published) {
        this.published = published;
    }

    @Override
    public String toString() {
        return "Tutorial{" +
                "id=" + id +
                ", title='" + title + '\'' +
                ", description='" + description + '\'' +
                ", published=" + published +
                '}';
    }
}
```
- repository - то, как база данных будет себя вести
Пример:
```java
public interface TutorialReposutory extends JpaRepository<Tutorial, Long> {
    List<Tutorial> findByPublished(boolean published);
    List<Tutorial> findByTitleContaining(String title);
}
```