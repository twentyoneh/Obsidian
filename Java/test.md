Приложение "Калькулятор отпускных".  
Микросервис на SpringBoot + Java 11 c одним API:  
GET "/calculacte"

Минимальные требования: Приложение принимает твою среднюю зарплату за 12 месяцев и количество дней отпуска - отвечает суммой отпускных, которые придут сотруднику.  
Доп. задание: При запросе также можно указать точные дни ухода в отпуск, тогда должен проводиться рассчет отпускных с учётом праздников и выходных.

Проверяться будет чистота кода, структура проекта, название полей\классов, правильность использования паттернов. Желательно написание юнит-тестов, проверяющих расчет.

- [ ] Создать объекты которые будут отвечать за:
- [ ] среднюю зарплату за 12 месяцев
- [ ] количество дней отпуска
- [ ] даты отпуска
- [ ] итоговая сумма отпускных
- [ ] Далее разбираемся со SpringBoot 

**Компоненты Spring Boot приложений**

[**1.1 Уровень интеграции компонентов**](https://habr.com/ru/articles/674858/#%D0%A3%D1%80%D0%BE%D0%B2%D0%B5%D0%BD%D1%8C%D0%98%D0%BD%D1%82%D0%B5%D0%B3%D1%80%D0%B0%D1%86%D0%B8%D0%B8)Spring Boot  
Spring Framework – Core  
[**1.2 Уровень бизнес-логики**](https://habr.com/ru/articles/674858/#%D0%A3%D1%80%D0%BE%D0%B2%D0%B5%D0%BD%D1%8C%D0%91%D0%B8%D0%B7%D0%BD%D0%B5%D1%81-%D0%BB%D0%BE%D0%B3%D0%B8%D0%BA%D0%B8)Spring Framework – Testing  
Spring Framework – Languages  
Spring Shell  
Spring Statemachine  
Spring Batch  
[**Spring Security**](https://habr.com/ru/articles/674858/#SpringSecurity)Spring Security  
Spring Security Kerberos  
Spring Authorization Server

[**2. Уровень обмена данными с хранилищами**](https://habr.com/ru/articles/674858/#%D0%A3%D1%80%D0%BE%D0%B2%D0%B5%D0%BD%D1%8C%D0%9E%D0%B1%D0%BC%D0%B5%D0%BD%D0%B0%D0%94%D0%B0%D0%BD%D0%BD%D1%8B%D0%BC%D0%B8%D0%A1%D0%A5%D1%80%D0%B0%D0%BD%D0%B8%D0%BB%D0%B8%D1%89%D0%B0%D0%BC%D0%B8)Spring Framework – Data Access  
Spring LDAP  
[**Spring Data**](https://habr.com/ru/articles/674858/#SpringData)Spring Data Commons  
[**Поддержка SQL БД**](https://habr.com/ru/articles/674858/#%D0%9F%D0%BE%D0%B4%D0%B4%D0%B5%D1%80%D0%B6%D0%BA%D0%B0SQL%D0%91%D0%94)Spring Data JPA  
Spring Data Envers  
Spring Data REST  
Spring Data JDBC  
Spring Data R2DBC  
Spring Data for Apache Solr (устарел)  
Spring Data JDBC Extensions (устарел)
[**Поддержка NoSQL БД**](https://habr.com/ru/articles/674858/#%D0%9F%D0%BE%D0%B4%D0%B4%D0%B5%D1%80%D0%B6%D0%BA%D0%B0NoSQL%D0%91%D0%94)Spring Data MongoDB  
Spring Data Elasticsearch  
Spring Data Redis  
Spring Data Neo4j  
Spring Data for Apache Cassandra  
Spring Data Couchbase  
Spring Data LDAP  
[**Поддержка Grid-хранилищ**](https://habr.com/ru/articles/674858/#%D0%9F%D0%BE%D0%B4%D0%B4%D0%B5%D1%80%D0%B6%D0%BA%D0%B0Grid%D0%A5%D1%80%D0%B0%D0%BD%D0%B8%D0%BB%D0%B8%D1%89)Spring Data for Apache Geode  
Spring Data for VMware Tanzu GemFire  
[**Интеграция с BigData**](https://habr.com/ru/articles/674858/#%D0%98%D0%BD%D1%82%D0%B5%D0%B3%D1%80%D0%B0%D1%86%D0%B8%D1%8F%D0%A1BigData)Spring for Apache Hadoop (устарел)

[**3. Уровень сетевого обмена данными**](https://habr.com/ru/articles/674858/#%D0%A3%D1%80%D0%BE%D0%B2%D0%B5%D0%BD%D1%8C%D0%A1%D0%B5%D1%82%D0%B5%D0%B2%D0%BE%D0%B3%D0%BE%D0%9E%D0%B1%D0%BC%D0%B5%D0%BD%D0%B0%D0%94%D0%B0%D0%BD%D0%BD%D1%8B%D0%BC%D0%B8)Spring Framework – Web MVC (Web Servlet)  
Spring Framework – WebFlux (Web Reactive)  
Spring Framework – Integration  
Spring Web Flow  
Spring HATEOAS  
Spring for GraphQL  
Spring Web Services  
Spring REST Docs  
[**MQ (Message Queue)**](https://habr.com/ru/articles/674858/#MQ)Spring AMQP  
Spring for Apache Kafka

[**4. Фреймворк корпоративной интеграции**](https://habr.com/ru/articles/674858/#%D0%A4%D1%80%D0%B5%D0%B9%D0%BC%D0%B2%D0%BE%D1%80%D0%BA%D0%9A%D0%BE%D1%80%D0%BF%D0%BE%D1%80%D0%B0%D1%82%D0%B8%D0%B2%D0%BD%D0%BE%D0%B9%D0%98%D0%BD%D1%82%D0%B5%D0%B3%D1%80%D0%B0%D1%86%D0%B8%D0%B8)

Spring Integration