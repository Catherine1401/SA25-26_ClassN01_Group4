# 📱 Ứng dụng Nhắn Tin Trên Thiết Bị Di Động

**(Monolithic Architecture)**

---

## 1. Giới thiệu dự án (Introduction to the Project)

Dự án nhằm xây dựng một **ứng dụng nhắn tin trên thiết bị di động** cho phép người dùng giao tiếp với nhau **theo thời gian thực**.

Hệ thống được thiết kế theo **kiến trúc Monolithic**, trong đó toàn bộ các chức năng được triển khai trong **một khối ứng dụng thống nhất**.

Dự án được thực hiện trong khuôn khổ học phần **Kiến trúc phần mềm**, tập trung vào:

* Phân tích các **quyết định kiến trúc**
* Đánh giá **thuộc tính chất lượng** của hệ thống

---

## 2. Tóm tắt điều hành (Executive Summary)

Ứng dụng nhắn tin cho phép người dùng:

* Kết nối hệ thống bằng **tên người dùng duy nhất**
* Gửi và nhận **tin nhắn văn bản theo thời gian thực**
* Giao tiếp **đồng thời với nhiều người dùng**

Hệ thống sử dụng kiến trúc **Client – Server**, trong đó **server được xây dựng theo mô hình Monolithic**.

Toàn bộ logic xử lý bao gồm:

* Quản lý kết nối người dùng
* Xử lý và phân phối tin nhắn

Tất cả được tích hợp trong **một ứng dụng duy nhất**, giúp:

* Đơn giản hóa triển khai
* Phù hợp cho giai đoạn phát triển ban đầu

---

## 3. Yêu cầu & Mục tiêu dự án (Project Requirements & Goals)

### 3.1 Yêu cầu chức năng

* Người dùng có thể kết nối đến server bằng **một tên người dùng duy nhất**
* Gửi và nhận **tin nhắn văn bản**
* Tin nhắn được truyền **theo thời gian thực**
* Hỗ trợ **nhiều người dùng hoạt động đồng thời**

### 3.2 Yêu cầu phi chức năng

* **Độ trễ thấp**: Tin nhắn được truyền gần như tức thời
* **Độ tin cậy**: Hệ thống hoạt động ổn định trong điều kiện bình thường
* **Dễ triển khai**: Phù hợp với nhóm phát triển nhỏ
* **Dễ bảo trì**: Cấu trúc đơn giản, dễ hiểu

### 3.3 Mục tiêu

* Áp dụng **kiến trúc Monolithic** cho hệ thống thời gian thực
* Đánh giá **ưu điểm và hạn chế** của kiến trúc Monolithic
* Đáp ứng các **thuộc tính chất lượng** quan trọng của ứng dụng nhắn tin

---

## 4. Thiết kế & Triển khai kiến trúc

*(Architectural Design & Implementation)*

### 4.1 Tổng quan kiến trúc

Hệ thống được thiết kế theo **Client – Server Architecture**, bao gồm:

#### 📱 Client (Mobile / Web)

* Hiển thị giao diện người dùng
* Gửi và nhận tin nhắn

#### 🖥️ Monolithic Server

* Quản lý kết nối người dùng
* Xử lý logic nghiệp vụ
* Phân phối tin nhắn theo thời gian thực

*(Tùy chọn)*: Lưu trữ dữ liệu

➡️ Toàn bộ thành phần phía server được triển khai trong **một ứng dụng duy nhất**.

---

### 4.2 Sơ đồ kiến trúc Monolithic

```
+------------------------------------------------------+
|                Mobile / Web Client                   |
|   (Android / Flutter / React Native / Web Browser)   |
+------------------------------------------------------+
                        |
                        |  WebSocket / Socket.IO
                        v
+------------------------------------------------------+
|               Monolithic Chat Server                 |
|------------------------------------------------------|
| - User Connection Management                         |
| - Message Handling Logic                             |
| - Real-time Event Processing                         |
| - (Optional) Data Access Layer                       |
+------------------------------------------------------+
                        |
                        v
+------------------------------------------------------+
|                 Database / Memory                    |
+------------------------------------------------------+
```

#### Giải thích kiến trúc

* Client giao tiếp **trực tiếp** với server
* Server xử lý **toàn bộ chức năng** trong một khối thống nhất
* Giao tiếp thời gian thực thông qua **WebSocket / Socket.IO**

---

### 4.3 Công nghệ sử dụng

| Thành phần | Công nghệ                        |
| ---------- | -------------------------------- |
| Client     | Android / Flutter / React Native |
| Server     | Supabase (Monolithic Application) |
| Giao tiếp  | Socket.IO (WebSocket)            |
| Lưu trữ    | In-memory / Database (mở rộng)   |

---

### 4.4 Lý do lựa chọn kiến trúc Monolithic

Kiến trúc **Monolithic** được lựa chọn vì:

* Phù hợp với **quy mô dự án nhỏ – trung bình**
* **Dễ phát triển và triển khai**
* Giảm **độ phức tạp** trong thiết kế kiến trúc
* Thuận lợi cho **mục tiêu học tập và phân tích kiến trúc**

---

## 5. Kiểm thử & Đánh giá (Testing & Verification)

### 5.1 Chiến lược kiểm thử

* **Unit Test**: Kiểm tra các hàm xử lý tin nhắn
* **Integration Test**: Kiểm tra kết nối client – server
* **Performance Test**: Đo độ trễ khi nhiều người dùng gửi tin nhắn đồng thời

### 5.2 Kết quả

* Tin nhắn được truyền **gần như tức thời**
* Hệ thống hoạt động **ổn định với nhiều kết nối**
* Kiến trúc Monolithic **đáp ứng tốt yêu cầu hiện tại** của dự án

---

## 6. Kết luận & Nhận xét (Conclusion & Reflection)

Dự án đã xây dựng thành công **ứng dụng nhắn tin thời gian thực trên thiết bị di động** dựa trên **kiến trúc Monolithic**.

Kiến trúc này phù hợp với:

* Mục tiêu học tập
* Quy mô dự án

Đồng thời giúp nhóm hiểu rõ mối quan hệ giữa **quyết định kiến trúc** và **thuộc tính chất lượng** của hệ thống.

### Hướng phát triển trong tương lai

* Tách các module khi hệ thống mở rộng
* Nâng cấp sang **Microservices** khi số lượng người dùng lớn
* Bổ sung **chat nhóm** và **gửi đa phương tiện**

