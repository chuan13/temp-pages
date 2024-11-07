# 面試準備：問答<br>Java 框架

## 題目

1. [什麼是 JavaBean？](#1-什麼是-javabean)
2. [Spring 是什麼？](#2-spring-是什麼)
3. [IoC 與 DI 是什麼？](#3-ioc-與-di-是什麼)
4. [AOP 是什麼？](#4-aop-是什麼)
5. [Spring、Spring MVC、Spring Boot 的關係？](#5-springspring-mvcspring-boot-的關係)
6. [Spring Bean 的生命週期？](#6-spring-bean-的生命週期)
7. [哪些 annotation 可以取代 Bean？](#7-哪些-annotation-可以取代-bean)
8. [Spring 如何進行 DI（依賴注入）？](#8-spring-如何進行-di依賴注入)
9. [`@SpringBootApplication` 包含了哪些 annotation 的功能？](#9-springbootapplication-包含了哪些-annotation-的功能)  
10. [什麼是 ORM？](#10-什麼是-orm)  
11. [常見的 ORM 框架？](#11-常見的-orm-框架)  
12. [多對多關係要怎麼處理？為什麼需要中介表？](#12-多對多關係要怎麼處理為什麼需要中介表)  
13. [什麼是 Persistent Class？](#13-什麼是-persistent-class)  
14. [`@Transactional` 是什麼？應該下在哪裡？](#14-transactional-是什麼應該下在哪裡)  
15. [Spring Data JPA 的 JPARepository 是什麼？](#15-spring-data-jpa-的-jparepository-是什麼)  
16. [如何利用 JPA 達成複合式查詢？](#16-如何利用-jpa-達成複合式查詢)  
17. [`@ResponseBody` 與 `@ResponseEntity` 分別是什麼？](#17-responsebody-與-responseentity-分別是什麼)  
18. [`@RequestMapping` 與 `@GetMapping` 分別是什麼？](#18-requestmapping-與-getmapping-分別是什麼)  

<br>

## 對應知識

### 1. 什麼是 JavaBean？
概念：JavaBean
- 是一種 class 的設計規範
- 屬性必須為 private，並要有 public 的 getter 與 setter
- 要有無參數建構子
- implement `Serializable`

<br>

### 2. Spring 是什麼？
概念：Spring
- IoC／DI 的容器
- 簡化 AOP 的實作流程

<br>

### 3. IoC 與 DI 是什麼？
概念：IoC 與 DI  
<b style="color: red;">常考</b>
- 目的：解耦，使程式更容易維護、方便測試
- IoC：Inversion of Control，控制反轉
    - 將物件的創建交由第三方容器控制，而不是自己創建
    - 需要使用該物件時，向第三方容器拿——DI
- DI：Dependency Injection，依賴注入
    - 有依賴該物件的 class，向第三方容器取得

延伸閱讀（其他網站）：[[筆記] 依賴注入 DI、控制反轉 IoC、依賴反轉原則 DIP](https://hackmd.io/@kenny88881234/rJwqJbT4S)

<br>

### 4. AOP 是什麼？
概念：AOP  
<b style="color: red;">常考</b>
- Aspect-Oriented Programming
- 在符合指定條件的方法前後，多做一些事情
- 可免去在每個方法裡重複寫程式碼的麻煩
- 用途：log、某些商業邏輯

<br>

### 5. Spring、Spring MVC、Spring Boot 的關係？
概念：Spring、Spring Boot
- Spring：IoC／DI 的容器、簡化 AOP 的實作。
- Spring MVC：網路功能，包含 `@Controller`、`@RequestMapping` 等等。
- Spring Boot：啟動器（starter），整合了 ORM、Spring Framework 等 Library，並內建 Server容器（如 Tomcat）；有「約定優於配置」原則，將設定過程簡化、且能更快速地啟動。

<br>

### 6. Spring Bean 的生命週期？
概念：Spring
- 交由 Spring 容器控管的物件，就稱為 Spring Bean
- 通常為 Singleton
- 創建：在 Application 啟動時由 Spring 創建
- DI：注入至依賴的 class
- init：（如果有設定）執行 init()
- （專案執行中）
- destroy：容器關閉前，（如果有設定）先執行 destroy()，接著銷毀這個物件。

<br>

### 7. 哪些 annotation 表示這個 class 是要交由 Spring 管理的 Spring Bean？
概念：Spring  
（待補）  
`@Controller`、`@Service`、`@Repository`、`@Component`，以及在 `@Configuration` 裡面標註 `@Bean` 的方法。

<br>

### 8. Spring 如何進行 DI（依賴注入）？
概念：Spring  
（待補）

<br>

### 9. `@SpringBootApplication` 包含了哪些 annotation 的功能？
概念：Spring Boot  
（待補）  
- `@Configuration`: Tags the class as a source of bean definitions for the application context.
- `@EnableAutoConfiguration`: Tells Spring Boot to start adding beans based on classpath settings, other beans, and various property settings. For example, if spring-webmvc is on the classpath, this annotation flags the application as a web application and activates key behaviors, such as setting up a DispatcherServlet.
- `@ComponentScan`: Tells Spring to look for other components, configurations, and services in the hello package, letting it find the controllers.

<br>

### 10. 什麼是 ORM？
概念：ORM
- Object-Relational Mapping
- 將 Java Object（Entity）映射至資料庫中的 Table
- 讓程式設計師不用寫 SQL 指令，改用映射的 Entity 操控資料
- 方便替換資料庫

<br>

### 11. 常見的 ORM 框架？
概念：ORM
- JPA 規範：對於 ORM 的標準，實際由各個 ORM 框架實作
    - Hibernate
    - Spring Data JPA：進一步封裝 JPA、提供更方便的功能（如 JPARepository）
- MyBatis
    - 不是實作 JPA 規範、不算 ORM，但也是個資料庫訪問框架

<br>

### 12. 多對多關係要怎麼處理？為什麼需要中介表？
概念：ORM  
（待補）

<br>

### 13. 什麼是 Persistent Class？
概念：ORM  
（待補）

<br>

### 14. `@Transactional` 是什麼？應該下在哪裡？
概念：JPA
- 指定在此方法內對 Entity 的動作要包含在當前 Transaction 內
- 基本上，在方法內操作 Entity 就會需要

<br>

### 15. Spring Data JPA 的 JPARepository 是什麼？
概念：Spring Data JPA
- 自己寫繼承自 JPARepository 的介面、在泛型內填入 Entity 和 Entity id 的型別
- Spring 會生成一個 class 實作自己寫的介面
- 已經有 findAll()、findById()、save() 等等方法，且 findAll() 可以用 Pageable（分頁）、Specification（篩選條件）

<br>

### 16. 如何利用 JPA 達成動態條件查詢？
概念：Spring Data JPA
（待補）  
- 使用 Specification 類別，每個 Specification 是一個條件，可以使用 equals、greaterThan 等等條件、設定要比較的對象。

<br>

### 17. `@ResponseBody` 與 `@ResponseEntity` 分別是什麼？
概念：Spring MVC  
（待補）

<br>

### 18. `@RequestMapping` 與 `@GetMapping` 分別是什麼？
概念：Spring MVC  
（待補）

<br>
