# 面試準備：技術問答<br>Java 基礎
<br>

### 1. Java 的特色是？
概念：Java 執行環境
- 物件導向
- 跨平台
    - 由 compiler 編譯為二進制檔（class 檔）
    - 在每個裝置上由 JVM 執行

<br>

### 2. 什麼時候會進行 Garbage Collection？
概念：Garbage Collection
- 自動執行，通常於記憶體不足時
- 掃描 heap，清除沒有被 reference 的物件資料

<br>

### 3. `System.out.print`、`System.out.println`、`System.out.printf` 的差別？
概念：System.out
- 若為變數，自動呼叫 `toString()`
- System.out.print
    - 於 console 輸出，不換行
- System.out.println
    - 於 console 輸出並換行
- System.out.printf
    - 於 console 輸出，可以使用佔位符傳入參數。

<br>

### 4. 有哪些基本資料型態？
概念：基本資料型態
- （待補）

<br>

### 5. i++ 與 ++i 的比較？
概念：運算子
- （待補）

<br>

### 6. String 的特性
概念：String
- String pool
    - 如果使用 `String variable = "string";`，會先進 String pool 判斷是否有內容相同的字串——如果有、就使用同一份；如果沒有，再在 String pool 創建新的。
- immutable
    - 如果又用 `=` 賦值，會創建新的 String 物件。

<br>

### 7. String 的 `==` 和 `equals()`？
概念：String  
<b style="color: red;">常考</b>
- `==`：判斷記憶體位址是否相同
    - 若是以 `String variable = "string";` 這種方式宣告的，由於 String pool 特性、相同內容的字串記憶體位址也會相同。
- `equals()`：判斷內容

<br>

### 8. 什麼是物件？
概念：物件
- 可以有屬性與方法，並有 constructor 以建立物件
- 在 Java，除了基本資料型態、其餘都是物件

<br>

### 9. Stack 與 Heap
概念：Stack 與 Heap
- Stack
    - 儲存變數名稱對應的東西
        - 基本資料型態：儲存內容
        - 物件型態：儲存實際內容在 Heap 的記憶體位址
- Heap
    - 儲存物件的實際內容
  
- 補充：local variable 的實際內容儲存在 stack

<br>

### 10. Java 是 Pass by Value（傳值）還是 Pass by Reference（傳址）？
概念：賦值
- Java 是 Pass by Value（Copy by Value），複製一份 stack 內的資料去賦值。
    - 如果該變數是基本資料型態，會複製一份資料內容過去，兩個變數的操作互不干涉。
    - 如果該變數是物件，就會複製記憶體位址過去，導致兩個變數實際操作的內容是同一個物件。

<br>

### 11. Object 的 `==` 與 `equals()`？
- 都是判斷記憶體位址。

<br>

### 12. 什麼是物件導向？／物件導向三大特性？
概念：物件導向  
<b style="color: red;">常考</b>
- 所有東西都是物件
- 封裝、繼承、多型

<br>

### 13. 什麼是封裝？
概念：封裝  
<b style="color: red;">常考</b>
- 將物件的屬性設為 private、讓其他 class 不能直接存取
- 建立 getter 與 setter 讓其他 class 透過這些 method 與此物件的屬性互動

<br>

### 14. 什麼是繼承？
概念：繼承  
<b style="color: red;">常考</b>
- `extend` 繼承 superclass
- 會繼承 superclass 已經定義好的屬性與方法
- 只能繼承一個 class
- 舉例：Animal 是 superclass、已經定義了 age 屬性和 walk() 方法；Cat 繼承了 Animal、是 subclass，不需額外定義就擁有 age 屬性、可以使用 walk() 方法。

<br>

### 15. 什麼是 Override？
概念：繼承  
<b style="color: red;">常考</b>
- 繼承而來的方法，可以改寫它的內容，使用時會使用到 override 的內容

<br>

### 16. 什麼是 Overload？
概念：方法  
<b style="color: red;">常考</b>
- 同個 class 可以有多個同名的方法、但是帶入不同參數（型態、數量）
- 呼叫時會根據參數的型態與數量判斷實際呼叫的是哪個方法

<br>

### 17. 抽象方法是什麼？
概念：抽象
- 此方法沒有實作，要由 `extend`／`implement` 這個物件／介面的 class 去　override 實作才能使用。

<br>

### 18. Abstract class（抽象類別）與 Interface（介面）的比較？
概念：抽象、介面
- Abstract class
    - 用途：這些 class 都屬於的 class
        - 舉例：Cat、Dog 都是 Animal
    - 不能被 `new`
    - 一個 class 只能繼承一個 class
    - 可以定義屬性（實例變數）
    - 可以有已實作的方法和抽象方法
- Interface
    - 用途：這些 class 都擁有的行為
        - 舉例：Cat、Dog 都可以 Run（`implement Runnable`）
    - 不能被 `new`
    - 一個 class 可以實作多個 interface
    - 只能定義常數（`public static final`）
    - 只能定義抽象方法

<br>

### 19. 什麼是多型（Polymorphism）？
概念：多型  
<b style="color: red;">常考</b>
- 用 superclass／interface 操作物件，實際上的內容被定義在繼承／實作的 class 裡
    - 舉例：
        ```Java
        List<String> strings = new ArrayList<String>();
        strings.add("New Element");
        ```
        其中 `add()` 的實際內容是定義在 ArrayList 裡、但這裡 strings 的型態是 List、用 interface 型態操作。

<br>

### 20. 常見的集合（Collection）有哪些？
- List
    - 每個元素是一個物件
    - 有序
    - 可重複
    - 常用實作：ArrayList、LinkedList
- Set
    - 每個元素是一個物件
    - 無序（HashSet）／有序（TreeSet、LinkedHashSet）
    - 不可重複
    - 常用實作：HashSet、TreeSet、LinkedHashSet
- Map
    - 每個元素是一組 key-value、兩者都是物件
    - 無序（HashMap）／有序（TreeMap、LinkedHashMap）
    - key 不可重複、value 可重複
    - 常用實作：HashMap、TreeMap、LinkedHashMap
- 所有的集合，元素都是物件、不能放基本資料型態。

<br>

### 21. ArrayList 與 LinkedList 的比較？
概念：資料結構
- ArrayList
    - 底層是陣列
    - 查詢：快
    - 增刪：慢
- LinkedList
    - 底層是鏈表
    - 查詢：慢
    - 增刪：快

<br>

### 22. 什麼是泛型？
概念：泛型
- 限制此物件內裝著的物件是什麼型態
- 只能放物件、不能放基本資料型態
- 舉例：
    ```Java
    List<String> strings = new ArrayList<String>();
    ```
    這個 List 限制了只能裝 String 型態的物件。

<br>

### 23. Exception 分為哪幾種？
概念：Exception
- （待補）

<br>

### 24. throw 與 throws？
概念：Exception
- throw
    - 在方法裡
    - 主動 throw 一個自己創建的 Exception 物件。
- throws
    - 在方法宣告上
    - 表示此方法可能會 throws 哪些 class 的 Exception，呼叫此方法的地方要處理。

<br>

### 25. try-catch-finally 的執行順序？
概念：Exception
- （待補）

<br>

### 26. Java 如何跟資料庫連線？
概念：JDBC
- （待補）

<br>

### 27. 什麼是 SQL Injection？要如何預防？
概念：JDBC
- （待補）

<br>
