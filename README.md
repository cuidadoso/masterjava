# Многопоточность. Веб сервисы.
### _Разработка полнофункционального многомодульного Maven проекта_
- веб приложение (Tomcat, JSP, jQuery)
- многопоточный почтовый сервиса (JavaMail, java.util.concurrent.*) и вспомогательные модули
- связь модулей через веб-сервисы (SOAP, JAX-WS) и по REST (JAX-RS)
- сохранение данных в RMDBS (H2) и динамическое конфигурирование модулей по JMX.

### Требование к участникам
Опыт программирования на Java. Базовые знания Maven.

## Необходимое на курсе ПО
-  <a href="http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html">JDK8</a>
-  <a href="http://git-scm.com/downloads">Git</a>
-  <a href="http://www.jetbrains.com/idea/download/index.html">IntelliJ IDEA</a>

> Выбирать Ultimate, 30 days trial (работа с JavaScript, Tomcat, JSP). Учебный ключ к Ultimate выдается на первом занятии.

## Многопоточность
![Concurrent vs Parallel](https://joearms.github.io/images/con_and_par.jpg)
- <a href="http://www.javaspecialist.ru/2011/06/java-memory-model.html">Java Memory Model</a>
- <a href="http://www.skipy.ru/technics/synchronization.html">Синхронизация потоков</a>
- <a href="https://habrahabr.ru/company/luxoft/blog/157273">Обзор java.util.concurrent.*</a>
- <a href="http://articles.javatalks.ru/articles/17">Использование ThreadLocal переменных</a>

#### Основы, доп. материалы
- Intuit, <a href="http://www.intuit.ru/studies/courses/16/16/lecture/27127">Потоки выполнения. Синхронизация</a>
- Алексей Владыкин, <a href="https://www.youtube.com/watch?v=zxZ0BXlTys0&list=PLlb7e2G7aSpRSBWi5jbGjIe-v_CjRO_Ug">Основы многопоточность в Java</a>
- Виталий Чибриков, <a href="https://www.youtube.com/watch?v=dLDhB6SRXzw&list=PLrCZzMib1e9qkzxEuU_huxtSAxrW1t9NZ">Java. Многопоточность</a>
- Computer Science Center, курс <a href="https://compscicenter.ru/courses/hp-course/2016-spring">Параллельное программирование</a>
- Юрий Ткач, курс <a href="https://www.youtube.com/playlist?list=PL6jg6AGdCNaXo06LjCBmRao-qJdf38oKp">Advanced Java - Concurrency</a>
- Головач, курс <a href="https://www.youtube.com/playlist?list=PLoij6udfBncgVRq487Me6yQa1kqtxobZS">Java Multithreading</a>

---
# Вступительное задание:
Вычекать этот проект:
```git clone  https://github.com/JavaOPs/masterjava.git```

Реализовать класс `MainMatrix`, позволяющий многопоточно <a href="https://ru.wikipedia.org/wiki/Умножение_матриц">перемножать квадратные матрицы N*N</a>.
- Количество дочерних потоков ограничено M (M<N).
- Учесть что-нибудь из <a href="https://habrahabr.ru/post/114797/">оптимизации</a>
- Сделать несколько вариантов решения:
  - Объязательно: используя только механизмы синхронизации Java 1.4
  - Опционально: без ограничений

-----
# Программа курса
> **возможны изменения, окончательная программа будет перед стартом курса**

### Concurrent and Parallel Programming
- Thread safety. Java Memory Model/ JSR 133. Happens-before.
- Публикация объектов. Использование ThreadLocal переменных
- Initialization on demand holder / Double-checked locking
- Обзор java.util.concurrent.*

### Сервис-ориентированная архитектура, Микросервисы
- JMS, альтернативы
- Варианты разворачивания сервисов. Работа с базой. Связывание сервисов.

### Maven. Многомодульный Maven проект
- Build Lifecycle
- Dependency Mechanism
- Зависимости, профили, написание плагина
- The Reactor. Snapshots

### Создание/тестирование веб-приложения.
- Сборка, запуск, локальный и удаленный debug проекта, способы деплоя в Tomcat
- tomcat7-maven-plugin

### Веб-сервисы
- Веб-сервисы. SOAP. Преимущества/недостатки веб-сервисов. Расширения.
- Реализация веб-сервисов в Java. JAX-RPC, JAX-WS, CFX, Axis. Стили WSDL
- Создание API и реализации веб-сервиса MailService.
- Деплой и тестирование через SoapUI.

### Доработка веб-сервиса. Кастомизация WSDL.
- Работа с JAXB.
- Передача по SOAP Exception
- Включение wsdl в сервис для публикации.
- Генерация java кода по WSDL

### Реализация клиент веб-сервиса.
- Публикация веб сервиса из main(). Дабавление wsdl
- Выделение из wsdl общей части
- Создание клиента почтового сервиса.
- Тестирование с помощью JUnit 4
- Интеграционное тестирование, maven-failsafe-plugin

### JAX-WS Handlers
- Logical/protocol handlers.
- Логирование SOAP на стороне клиента.
- Логирование и статистика трафика опубликованного веб-сервиса.
- wsimport binding.
- SoapHandler аутентификация.
Добавляем файлы вложения. Mail-Service.

### Создаем вложения почты
- Генерация обновленного WSDL через wsgen
- Веб-сервисы: JAX-WS attachment with MTOM
- Тестирование вложений через SoapUi.

### Загрузка файлов.
- Стандарт MIME. Обрабатываем вложения на форме: commons-fileupload
- Загрузка файла вместе в полями формы.
- Вызов клиента с вложениями.

### Персистентность.
- NoSQL or RDBMS. Обзор NoSQL систем. CAP
- Обзор Java persistence solution: commons-dbutils, Spring JdbcTemplate, MyBatis, JOOQ, ORM (Hibernate, TopLink, ElipseLink, EBean used in Playframework). JPA. JPA Performance Benchmark
- Работа с базой: создание базы, настройка IDEA Database.
- Работа с DB через DataSource, настройка tomcat. HikariCP
- Настройка работы с DataSource из JUnit.

### REST веб сервис.
- JAX-RS. Интеграция с Jersey
- Поддержка Json. Jackson

### Асинхронность.
- @OneWay vs Java Execution framework
- Добавление в клиенте асинхронных вызовов.
- Асинхронные сервлеты 3.x в Tomcat

### Динамическое конфигурирование. JMX
- Maven Groovy cкрптинг.  groovy-maven-plugin
- Настройка Tomcat на удаленное администрирование по JMX

### Проблема MemoryLeak. Поиск утечки памяти.
