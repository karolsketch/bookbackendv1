# bookbackendv1
bookbackendv1

# 1. 專案簡介
本專案為「線上書店後端系統」，提供：
會員註冊 / 登入 / 更新資料 / 忘記密碼
會員歷史訂單查詢
後台員工登入、帳號管理（新增/修改/刪除/重設密碼）
書籍管理（新增 / 編輯 / 上下架 / 查詢）
訂單管理（條件篩選、查詢、匯出 CSV 報表）
首頁內容管理（輪播圖 + 推薦區：新上架 / 熱門 / 優惠）
採用 標準三層式架構（Controller → Service → Repository → Entity）
---

# 2. 開發環境與技術
| 類型         | 說明              |
| ---------- | --------------- |
| OS         | macOS           |
| IDE        | Eclipse         |
| JDK        | Java 17+        |
| Framework  | Spring Boot 3.x |
| DB         | MySQL           |
| ORM        | JPA + Hibernate |
| Build Tool | Maven           |
---
# 3. 專案結構

```text
src/main/java/com/demo
├── Bookbackendv1Application.java
│
├── controller
│   ├── MemberController.java
│   ├── MemberOrderController.java
│   ├── EmployeeAuthController.java
│   ├── EmployeeManageController.java
│   ├── BookManageController.java
│   ├── AdminOrderController.java
│   └── HomeContentController.java
│
├── service
│   ├── MemberService.java
│   ├── MemberOrderService.java
│   ├── EmployeeService.java
│   ├── BookService.java
│   ├── AdminOrderService.java
│   └── HomeContentService.java
│
├── repository
│   ├── MemberRepository.java
│   ├── EmployeeRepository.java
│   ├── BookRepository.java
│   ├── OrderRepository.java
│   ├── OrderDetailRepository.java
│   └── PaymentMethodRepository.java
│
├── entity
│   ├── Member.java
│   ├── Employee.java
│   ├── Book.java
│   ├── Order.java
│   ├── OrderDetail.java
│   └── PaymentMethod.java
│
└── dto
    ├── Member*.java
    ├── Employee*.java
    ├── Book*.java
    ├── AdminOrder*.java
    ├── HomeBannerResponse.java
    └── HomeRecommendBookResponse.java
```
# 4. application.properties（DB / JPA 設定）

spring.application.name=bookbackendv1

spring.datasource.url=jdbc:mysql://localhost:3306/ebook
spring.datasource.driverClassName=com.mysql.cj.jdbc.Driver
spring.datasource.username=root
spring.datasource.password=YOUR_PASSWORD

spring.jpa.hibernate.ddl-auto=none
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true

spring.jpa.hibernate.naming.physical-strategy=\
org.hibernate.boot.model.naming.PhysicalNamingStrategyStandardImpl
---

# 5. 功能模組概述
5.1 會員功能
註冊 / 登入 / 登出
查詢目前登入會員
更新會員資料
忘記密碼（帳號 + 電話驗證，再使用 PasswordUtil 驗證新密碼）
5.2 會員訂單
依會員 Session 查詢歷史訂單列表
查詢指定訂單明細
5.3 後台員工登入 & 權限
ADMIN / STAFF 使用 Session 保存登入狀態
不同 Controller 自動判斷權限
只有 ADMIN 能管理員工帳號
ADMIN & STAFF 可管理書籍、訂單、首頁資料
5.4 書籍管理
查詢所有書籍（可依上/下架狀態）
新增書籍 / 編輯書籍
上架或下架書籍
5.5 訂單管理
依日期、訂單狀態、訂單編號等條件搜尋
查詢訂單明細
匯出 CSV 報表
5.6 首頁內容管理
輪播 Banner
推薦書籍：new、hot、discount
熱門書籍透過 OrderDetail 統計銷售量取得
---
# 6. Session 設計
| 角色   | Session Key       | 說明                |
| ---- | ----------------- | ----------------- |
| 會員   | `LOGIN_MEMBER_ID` | 用於會員操作            |
| 員工   | `LOGIN_EMP_ID`    | 員工登入識別            |
| 員工角色 | `LOGIN_EMP_ROLE`  | `ADMIN` / `STAFF` |
---
# 7. 專案啟動方式
git clone <your github url>
cd bookbackendv1
./mvnw spring-boot:run
或 Eclipse → Run As → Spring Boot App
---

