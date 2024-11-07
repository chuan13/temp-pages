# 面試準備：問答<br>SQL

## 題目

1. [關聯式資料庫是什麼？](#1-關聯式資料庫是什麼)
2. [Transaction 是什麼？](#2-transaction-交易是什麼)
3. [什麼是 SQL Injection？要如何預防？](#3-什麼是-sql-injection要如何預防)
4. [`GROUP BY` 怎麼用？](#4-group-by-怎麼用)
5. [`COUNT`、`AVG` 怎麼用？](#5-countavg-怎麼用)
6. [資料庫有哪四個特性？](#6-資料庫有哪四個特性)
7. [什麼是索引？](#7-什麼是索引)
8. [何謂資料庫正規化？](#8-何謂資料庫正規化)
9. [預存程序（Stored Procedure）是什麼？](#9-預存程序stored-procedure是什麼)
10. [`INNER JOIN` 與 `LEFT／RIGHT JOIN` 的差別？](#10-inner-join-與-leftright-join-的差別)
11. [Redis 的特色是？](#11-redis-的特色是)

<br>

## 對應知識

### 1. 關聯式資料庫是什麼？
概念：關聯式資料庫  
（待補）

<br>

### 2. Transaction （交易）是什麼？
概念：交易  
（待補）

<br>

### 3. 什麼是 SQL Injection？要如何預防？
概念：SQL Injection  
<b style="color: red;">常考</b>  
- 直接將使用者輸入的字串直接放入 SQL 指令，如果有使用者輸入了特定字串、可以做到超出原本設計的功能、改動資料庫內容。
- 預防：使用 PreparedStatement
    - 先編譯好 SQL 指令、並在要輸入條件的欄位留空
    - 實際使用時將使用者輸入的字串放進對應欄位

<br>

### 4. `GROUP BY` 怎麼用？
概念：GROUP BY  
（待補）

<br>

### 5. `COUNT`、`AVG` 怎麼用？
概念：彙總函數  
（待補）

<br>

### 6. 資料庫有哪四個特性？
概念：ACID  
（待補）  
- 原子性（Atomicity）：一個事務（transaction）中的所有操作，或者全部完成，或者全部不完成，不會結束在中間某個環節。事務在執行過程中發生錯誤，會被回滾（Rollback）到事務開始前的狀態，就像這個事務從來沒有執行過一樣。即，事務不可分割、不可約簡。
- 一致性（Consistency）：在事務開始之前和事務結束以後，資料庫的完整性沒有被破壞。這表示寫入的資料必須完全符合所有的預設約束、觸發器、級聯回滾等。
- 事務隔離（Isolation）：資料庫允許多個並發事務同時對其數據進行讀寫和修改的能力，隔離性可以防止多個事務並發執行時由於交叉執行而導致數據的不一致。事務隔離分為不同級別，包括未提交讀（Read uncommitted）、提交讀（read committed）、可重複讀（repeatable read）和串行化（Serializable）。
- 持久性（Durability）：事務處理結束後，對數據的修改就是永久的，即便系統故障也不會丟失。

<br>

### 7. 什麼是索引？
概念：索引  
（待補）

<br>

### 8. 何謂資料庫正規化？
概念：資料庫正規化  
（待補）

<br>

### 9. 預存程序（Stored Procedure）是什麼？
概念：預存程序  
（待補）

<br>

### 10. `INNER JOIN` 與 `LEFT／RIGHT JOIN` 的差別？
概念：JOIN  
<b style="color: red;">常考</b>  
（待補）

<br>

### 11. Redis 的特色是？
概念：Redis  
（待補）  
只在記憶體裡運行，沒有進硬碟

<br>
