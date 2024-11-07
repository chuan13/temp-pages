# 面試準備：問答<br>Java EE

## 題目
1. [Java EE 中有哪些 XML 設定檔？](#1-java-ee-中有哪些-xml-設定檔)
2. [什麼是 Singleton？](#2-什麼是-singleton)
3. [Servlet 是什麼？](#3-servlet-是什麼)
4. [Controller 是什麼？如何找到正確的 Controller？](#4-controller-是什麼如何找到正確的-controller)
5. [Servlet 的生命週期？](#5-servlet-的生命週期)
6. [Servlet 和 JSP 的差異？](#6-servlet-和-jsp-的差異)
7. [forward 和 redirect 的差異？](#7-forward-和-redirect-的差異)

<br>

## 對應知識

### 1. Java EE 中有哪些 xml 設定檔？
- web.xml
    - 設定於 WebApplication 專案
    - 配置 Servlet 與 URL mapping、Filter、Listener 等等
- context.xml
    - 設定於容器（如 Tomcat）
    - 配置 DataSource（JNDI）

<br>

### 2. 什麼是 Singleton？
- 在這個 WebApplication 執行過程中，只會建立一個物件實例
- 要使用此物件，不是使用 `new` 創建新的，而是直接引用此共用的物件

<br>

### 3. Servlet 是什麼？
- 根據 URL mapping 設定接收 HTTP request，在 `doGet()` 等方法內處理內容、產生 HTTP response 給 client。
- 由容器（如 Tomcat）管理。

<br>

### 4. Controller 是什麼？如何找到正確的 Controller？
- 在 MVC 架構中，負責接收 request、根據設計的功能呼叫對應 Service 處理。
- 根據 URL mapping 設定，request 會被分派到不同的 Controller 處理。

<br>

### 5. Servlet 的生命週期？
- 在第一次接收到 request 時，創建一個 Singleton 物件，並呼叫 `init()`。
- 每次接收到 request 時，呼叫 `service()`、接著去呼叫對應 method 的 `doGet()`、`doPost()` 等等方法。
- WebApplication 關閉時，呼叫 `destroy()` 、然後消滅。

<br>

### 6. Servlet 和 JSP 的差異？
- JSP 也是 Servlet，只是寫法不同、比較像 HTML。
- 通常用於 MVC 架構中的 View、產生最後給 client 的 HTML response。
- 整個 jsp 檔除了 Java 程式的文字內容，就是 `doGet()` 或 `doPost()` 等方法裡的 response。
- Java 程式部分則是 `doGet()` 或 `doPost()` 等方法裡的程式。

<br>

### 7. forward 和 redirect 的差異？
- forward
    - 在 server 內部轉發 request 與 response，由 forward 指定的 Servlet 接續處理
    - client 取得回傳時，顯示的網址是最一開始發出 request 的網址。
-redirect
    - 發送 response 給 client、請 client 發送一個新的 request 去指定網址／Servlet。
    - 由於是新的 request，無法從上一個 Servlet 夾帶內容給下一個 Servlet。
    - client 取得最後的回傳時，顯示的網址是 redirect 指定的網址。

<br>
