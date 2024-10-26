# 面試準備：技術問答<br>Java 框架
<br>

### 1. 什麼是 ORM？
概念：ORM
- Object-Relational Mapping
- 將 Java Object（Entity）映射至資料庫中的 Table
- 讓程式設計師不用寫 SQL 指令，改用映射的 Entity 操控資料
- 方便替換資料庫

<br>

### 2. 常見的 ORM 框架？
概念：ORM
- JPA 規範：對於 ORM 的標準，實際由各個 ORM 框架實作
    - Hibernate
    - Spring Data JPA：進一步封裝 JPA、提供更方便的功能（如 JPARepository）
- MyBatis
    - 不是實作 JPA 規範、不算 ORM，但也是個資料庫訪問框架

<br>

### 3. `@Transactional` 是什麼？應該下在哪裡？
概念：JPA
- 指定在此方法內對 Entity 的動作要包含在當前 Transaction 內
- 基本上，在方法內操作 Entity 就會需要

<br>

### 4. Spring 是什麼？為什麼要用 Spring？
概念：Spring
- 簡化 IoC 與 DI、AOP 的流程

<br>

### 5. IoC 與 DI 是什麼？
概念：IoC 與 DI
- 目的：解藕，使程式更容易維護、方便測試
- IoC：Inversion of Control，控制反轉
    - 將物件的創建交由第三方容器控制，而不是自己創建
    - 需要使用該物件時，向第三方容器拿——DI
- DI：Dependency Injection，依賴注入
    - 有依賴該物件的 class，向第三方容器取得
- 舉例：
    - `小明` 是個喜歡叫麥當勞的人，所以他每天都會打給 `他家附近的麥當勞` 叫麥當勞來吃
        - 若是有天 `他家附近的麥當勞` 公休了，那小明就要另外再找麥當勞，由此可知小明耦合他家附近的麥當勞
    - 如果今天 `小明` 是把他的要求給 `外送公司`，那麼 `外送公司` 就會幫他尋找營業中的麥當勞
        - 若是 `他家附近的麥當勞` 公休了，`外送公司` 就會自動找另一間營業中的麥當勞
    - 原本 `小明` 需耦合於 `他家附近的麥當勞`，現在被 `外送公司` 做了控制反轉，由 `外送公司` 來提供麥當勞
    - `小明` 不用管 `他家附近的麥當勞` 是否公休，`外送公司` 會幫他找到營業中的麥當勞
    - `小明`：依賴物件
    - `他家附近的麥當勞`：被依賴物件
    - `外送公司`：IoC 容器
    - 舉例來源：[[筆記] 依賴注入 DI、控制反轉 IoC、依賴反轉原則 DIP](https://hackmd.io/@kenny88881234/rJwqJbT4S)

<br>

### 6. Spring Bean 的生命週期？
概念：Spring
- 交由 Spring 容器控管的物件，就稱為 Spring Bean
- 通常為 Singleton
- 創建：在專案啟動時由 Spring 創建
- DI：注入至依賴的 class
- init：（如果有設定）執行 init()
- （專案執行中）
- destroy：容器關閉前，（如果有設定）先執行 destroy()，接著 destroy 這個物件。

<br>

### 7. AOP 是什麼？
概念：AOP
- Aspect-Oriented Programming
- 在符合指定條件的方法前後，多做一些事情
- 可免去在每個方法裡重複寫程式碼的麻煩
- 用途：log、某些商業邏輯

<br>

### 8. Spring、Spring MVC、Spring Boot 的關係？
概念：Spring、Spring Boot
- Spring：IoC 與 DI、AOP
- Spring MVC：網路功能，`@Controller`、`@RequestMapping` 等等
- Spring Boot：啟動器（starter），整合了 ORM、Spring Framework 等 Library，並內建 Server（Tomcat 等等），將設定過程簡化、且能更快速地啟動

<br>

### 9. Spring Data JPA 的 JPARepository 是什麼？
概念：Spring Data JPA
- 自己寫繼承自 JPARepository 的介面、在泛型內填入 Entity 和 Entity id 的型別
- Spring 會生成一個 class 實作自己寫的介面
- 已經有 findAll()、findById()、save() 等等方法，且 findAll() 可以用 Pageable（分頁）、Specification（篩選條件）

### 10.
