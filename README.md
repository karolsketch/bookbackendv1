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
