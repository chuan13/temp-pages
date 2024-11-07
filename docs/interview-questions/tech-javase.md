# 面試準備：問答<br>Java SE

## 題目
1. [Java 有什麼特色？](#1-java-有什麼特色)
2. [什麼時候會進行 Garbage Collection？](#2-什麼時候會進行-garbage-collection)
3. [`System.out.print`、`System.out.println`、`System.out.printf` 的差別？](#3-systemoutprintsystemoutprintlnsystemoutprintf-的差別)
4. [基本資料型態中，常用的整數及小數？](#4-基本資料型態中常用的整數及小數)
5. [i++ 與 ++i 的比較？](#5-i-與-i-的比較)
6. [String 的特性](#6-string-的特性)
7. [String 的 `==` 和 `equals()`？](#7-string-的--和-equals)
8. [什麼是物件？](#8-什麼是物件)
9. [Stack 與 Heap](#9-stack-與-heap)
10. [Java 是 Pass by Value（傳值）還是 Pass by Reference（傳址）？](#10-java-是-pass-by-value傳值還是-pass-by-reference傳址)
11. [Object 的 `==` 與 `equals()`？](#11-object-的--與-equals)
12. [什麼是物件導向？／物件導向三大特性？](#12-什麼是物件導向物件導向三大特性)
13. [什麼是封裝？](#13-什麼是封裝)
14. [什麼是繼承？](#14-什麼是繼承)
15. [什麼是 Override（覆寫）？](#15-什麼是-override覆寫)
16. [什麼是 Overload（多載）？](#16-什麼是-overload多載)
17. [`static` 是什麼？](#17-static-是什麼)
18. [存取修飾子是什麼？有哪些？](#18-存取修飾子是什麼有哪些)
19. [抽象方法是什麼？](#19-抽象方法是什麼)
20. [Abstract class（抽象類別）與 Interface（介面）的比較？](#20-abstract-class抽象類別與-interface介面的比較)
21. [什麼是多型（Polymorphism）？](#21-什麼是多型polymorphism)
22. [常見的集合（Collection）有哪些？](#22-常見的集合collection-有哪些)
23. [ArrayList 與 LinkedList 的比較？](#23-arraylist-與-linkedlist-的比較)
24. [什麼是泛型？](#24-什麼是泛型)
25. [Exception 分為哪幾種？](#25-exception-分為哪幾種)
26. [throw 與 throws？](#26-throw-與-throws)
27. [try-catch-finally 的執行順序？](#27-try-catch-finally-的執行順序)
28. [Java 如何跟資料庫連線？](#28-java-如何跟資料庫連線)

## 對應知識

### 1. Java 有什麼特色？
概念：物件導向、Java 執行環境
- 物件導向
- 跨平台
    - 由 compiler 編譯為二進制檔（class 檔）
    - 在每個裝置上由 JVM 執行

<br>

### 2. 什麼時候會進行 Garbage Collection？
概念：Garbage Collection
- 自動執行，比如於記憶體不足時
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

### 4. 基本資料型態中，常用的整數及小數？
概念：基本資料型態
- 整數：`int`
    - 佔 4 個 bytes，範圍是正負 2 的 31 次方以內、約為正負 21 億。
- 小數：`double`
    - 佔 8 個 bytes，小數點後可以到 15 位。

<br>

### 5. i++ 與 ++i 的比較？
概念：運算子
- 單獨一行時，是一樣的
- 同一行有賦值（`=`）時，「自增」與「賦值」的先後順序不同
    - i++
        - 先「賦值」再「自增」
        - ```Java
            int i = 5;
            int result = i++;
            // result 為 5，i 為 6
            ```
    - ++i
        - 先「自增」再「賦值」
        - ```Java
            int i = 5;
            int result = ++i;
            // result 為 6，i 為 6
            ```

<br>

### 6. String 的特性
概念：String
- String pool
    - 如果使用 `String variableName = "string";`，會先進 String pool 檢查是否有內容相同的字串——如果有、就 reference 到同一個物件；如果沒有，就在 String pool 創建新的字串物件。
- immutable
    - 如果又用 `=` 賦值，會創建新的 String 物件。

<br>

### 7. String 的 `==` 和 `equals()`？
概念：String  
<b style="color: red;">常考</b>
- `==`：比較 reference 的記憶體位址是否相同
    - 若是以 `String variable = "string";` 這種方式宣告的，由於 String pool 特性、相同內容的字串記憶體位址也會相同。
- `equals()`：比較內容
    - 是 `String` 這個 class override 的。

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
- 都是比較 reference 的記憶體位址。

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

### 15. 什麼是 Override（覆寫）？
概念：繼承  
<b style="color: red;">常考</b>
- 繼承而來的方法，可以改寫它的內容，使用時會使用到 override 的內容

<br>

### 16. 什麼是 Overload（多載）？
概念：方法  
<b style="color: red;">常考</b>
- 同個 class 可以有多個同名的方法、但是帶入不同參數（型態、數量）
- 呼叫時會根據參數的型態與數量判斷實際呼叫的是哪個方法

<br>

### 17. `static` 是什麼？
概念：方法
<b style="color: red;">常考</b>
- `static` 可以加在方法宣告上，表示這個方法不屬於此 class 的實例物件、而是屬於 class 本身。
- 載入此 class 時就會一併載入
- 不像平常的方法、要有此 class 的物件才能呼叫，而是用 class 名稱直接呼叫
    - ```Java
        Math.abs(-50);
        ```

<br>

### 18. 存取修飾子是什麼？有哪些？
概念：類別
- 可以加在屬性或方法宣告上
- `public`：任何 class 皆能存取
- （default）：同一 package 底下的 class 可以存取
- `protected`：僅有 superclass 與 subclass 可存取
- `private`：僅在同個 class 內可存取

<br>

### 19. 抽象方法是什麼？
概念：抽象  
- 此方法沒有實作，要由 `extend`／`implement` 這個物件／介面的 class／介面 去 override 實作才能使用。  

<br>

### 20. Abstract class（抽象類別）與 Interface（介面）的比較？
概念：抽象、介面  
- Abstract class  
    - 用途：這些 class 都屬於的 class  
        - 舉例：Cat、Dog 都是 Animal  
    - 不能被 `new`  
    - 一個 class 只能繼承一個 class  
    - 可以定義屬性（實例變數）  
    - 可以有抽象方法和已實作的方法  
- Interface  
    - 用途：這些 class 都擁有的行為  
        - 舉例：Cat、Dog 都可以 Run（`implement Runnable`）  
    - 不能被 `new`  
    - 一個 class 可以實作多個 interface  
    - 只能定義常數（`public static final`）  
    - 可以有抽象方法，也可以有已實作的方法、但必須在宣告方法加上 `default`  

<br>

### 21. 什麼是多型（Polymorphism）？
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

### 22. 常見的集合（Collection）有哪些？
概念：集合  
<b style="color: red;">常考</b>
- List  
    - 每個元素是一個物件  
    - 可重複  
    - 有序  
    - 常用實作：ArrayList、LinkedList  
- Set  
    - 每個元素是一個物件  
    - 不可重複  
    - 無序（HashSet）／有序（TreeSet、LinkedHashSet）  
    - 常用實作：HashSet、TreeSet、LinkedHashSet  
- Map  
    - 每個元素是一組 key-value、兩者都是物件  
    - key 不可重複、value 可重複  
    - 無序（HashMap）／有序（TreeMap、LinkedHashMap）  
    - 常用實作：HashMap、TreeMap、LinkedHashMap  
- 所有的集合，元素都是物件、不能放基本資料型態。  

<br>

### 23. ArrayList 與 LinkedList 的比較？
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

### 24. 什麼是泛型？
概念：泛型  
- 限制此物件內裝著的物件是什麼型態  
- 只能放物件、不能放基本資料型態  
- 舉例：  
    ```Java  
    List<String> strings = new ArrayList<String>();  
    ```  
    這個 List 限制了只能裝 String 型態的物件。  

<br>

### 25. Exception 分為哪幾種？
概念：Exception  
- Exception 為一個 superclass，implement `Throwable` 介面、所以可以被 throw。  
    - 內建 Exception  
        - Checked Exception  
            - compile 時就可預期發生，必須在程式裡準備好處理方式、否則無法通過 compile。  
            - 常見的  
                - IOException  
                - SQLException  
        - Unchecked Exception（`RuntimeException`）  
            - 執行時才會發生，不必預先準備處理方式即可 compile。  
            - 常見的  
                - ArithmeticException  
                - IndexOutOfBoundsException  
    - 自定義 Exception  
        - 如果要是 Checked Exception，就繼承 `Exception`  
        - 如果要是 Unchecked Exception，就繼承 `RuntimeException`  

<br>

### 26. throw 與 throws？
概念：Exception  
- throw  
    - 在方法裡  
    - 主動 throw 一個自己創建的 Exception 物件。  
- throws  
    - 在方法宣告上  
    - 表示此方法可能會 throws 哪幾種 class 的 Exception，呼叫此方法的地方要處理。  

<br>

### 27. try-catch-finally 的執行順序？
概念：Exception  
- 執行 try block  
    - 若有發生 Exception，不繼續執行  
    - 確認是否是指定要 catch 的對象 Exception，找到符合的就執行對應的 catch block  
- 無論 try block 和 catch block 執行到哪裡結束，最後都會執行 finally block  

<br>

### 28. Java 如何跟資料庫連線？
概念：JDBC  
- 使用對應資料庫的 JDBC Driver  
- 設定 Driver Class、連線 URL、使用者名稱、密碼  

<br>