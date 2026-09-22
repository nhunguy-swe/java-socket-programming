# Java Socket Programming (TCP/UDP)

Bộ ví dụ minh họa lập trình mạng nâng cao trong Java, tập trung vào **Socket Programming** với cả giao thức **TCP** (Echo Server/Client, xử lý đơn luồng và đa luồng) và **UDP Multicast**. Dự án dùng cho mục đích học tập, quản lý bằng **Maven**.

---

## Giới thiệu (About)

**Homework2** mở rộng từ Homework1, đi sâu vào cách Java xây dựng ứng dụng client-server bằng `Socket` và `ServerSocket` (TCP), cũng như `MulticastSocket` (UDP). Dự án minh họa 3 mô hình chính:

1. **Echo Server/Client cơ bản** – gửi và phản hồi (echo) một thông điệp duy nhất.
2. **Chat Server đơn luồng** – server xử lý lần lượt từng client, minh họa hạn chế khi không dùng đa luồng.
3. **Chat Server đa luồng** – server tạo một `WorkerThread` riêng cho mỗi client, cho phép phục vụ nhiều kết nối đồng thời.
4. **UDP Multicast** – gửi một thông điệp tới nhiều máy nhận cùng lúc trong cùng nhóm multicast.

---

## Tính năng chính

| Nhóm | File | Mô tả |
|---|---|---|
| Echo cơ bản | `EchoServer.java`, `EchoClient.java` | Server/Client TCP đơn giản, phản hồi lại đúng nội dung nhận được |
| Chat đơn luồng | `EchoChatSingleServer.java`, `EchoChatClient.java` | Server xử lý tuần tự từng client (blocking, một client tại một thời điểm) |
| Chat đa luồng | `EchoChatMultiServer.java`, `WorkerThread.java`, `EchoChatClient.java` | Server tạo thread riêng cho mỗi client, hỗ trợ nhiều kết nối song song |
| UDP Multicast | `MulticastSender.java`, `MulticastReceiver.java` | Gửi/nhận dữ liệu broadcast tới nhóm multicast qua UDP |

---

## Công nghệ sử dụng

| Thành phần | Phiên bản / Công cụ |
|---|---|
| Ngôn ngữ | Java 17+ |
| Build tool | Maven |
| Gói chính | `java.net` (`Socket`, `ServerSocket`, `MulticastSocket`), `java.io` |
| IDE khuyến nghị | IntelliJ IDEA (Community/Ultimate), Eclipse hoặc VS Code |

---

## Cấu trúc dự án

```
Homework2/
├── .idea/                                   # Cấu hình IntelliJ IDEA
├── src/
│   └── main/
│       └── java/
│           └── com/gpcoder/tcp/
│               ├── EchoServer.java
│               ├── EchoClient.java
│               ├── EchoChatSingleServer.java
│               ├── EchoChatMultiServer.java
│               ├── EchoChatClient.java
│               ├── WorkerThread.java
│               ├── MulticastSender.java
│               └── MulticastReceiver.java
├── .gitignore
├── pom.xml                                  # Cấu hình Maven
└── README.md
```

---

## Bắt đầu (Getting Started)

### Yêu cầu

- [JDK 17+](https://www.oracle.com/java/technologies/downloads/)
- [Maven](https://maven.apache.org/)
- IntelliJ IDEA / Eclipse / VS Code (tùy chọn)

### Cài đặt

```bash
git clone https://github.com/nhunguy-swe/Homework2.git
cd Homework2
```

### Chạy chương trình

**1. Echo Server/Client cơ bản**

```bash
# Terminal 1 — chạy server trước
java com.gpcoder.tcp.EchoServer

# Terminal 2 — chạy client
java com.gpcoder.tcp.EchoClient
```

**2. Chat Server đơn luồng**

```bash
# Terminal 1
java com.gpcoder.tcp.EchoChatSingleServer

# Terminal 2 (có thể mở nhiều terminal client)
java com.gpcoder.tcp.EchoChatClient
```

**3. Chat Server đa luồng**

```bash
# Terminal 1
java com.gpcoder.tcp.EchoChatMultiServer

# Nhiều terminal client kết nối đồng thời
java com.gpcoder.tcp.EchoChatClient
```

**4. UDP Multicast**

```bash
# Terminal 1 — máy nhận
java com.gpcoder.tcp.MulticastReceiver

# Terminal 2 — máy gửi
java com.gpcoder.tcp.MulticastSender
```

> Có thể chạy trực tiếp từng file bằng nút **Run** trong IntelliJ IDEA/Eclipse thay vì dùng terminal.

EchoChatClient.java
---
<img width="750" alt="image" src="https://github.com/user-attachments/assets/09de0acc-61ff-482f-b93c-18a6e4b9df3d" />

EchoChatSingleServer.java
---
<img width="750" alt="image" src="https://github.com/user-attachments/assets/1376f7dc-7f56-4361-9949-da0ee41fa403" />

<img width="750" alt="image" src="https://github.com/user-attachments/assets/2752bbd2-6604-4e5e-aeb6-993fe72b86ac" />

Run EchoChatSingleServer.java
---
<img width="750" alt="image" src="https://github.com/user-attachments/assets/c979c02b-c936-4732-8dff-000c3e1cf2fe" />

Run EchoChatClient.java
---
<img width="750" alt="image" src="https://github.com/user-attachments/assets/840353bc-1f20-41c8-b5e2-c42be3c4f2d3" />

Run EchoChatSingleServer.java
---
<img width="750" alt="image" src="https://github.com/user-attachments/assets/79f4de4f-3138-4111-b683-ebf4d30e66fc" />


---

EchoChatMultiServer.java
---
<img width="750" alt="image" src="https://github.com/user-attachments/assets/5b823753-fd13-4d35-874e-c6f5c4364716" />

<img width="750" alt="image" src="https://github.com/user-attachments/assets/a2f47550-eb14-4103-839a-7bcbd0e285f8" />

WorkerThread.java
---
<img width="750" alt="image" src="https://github.com/user-attachments/assets/09e4a63b-d123-48d7-a38a-c3222547cf71" />

Run EchoChatMultiServer.java
---
<img width="750" alt="image" src="https://github.com/user-attachments/assets/23ffa8fe-2890-4a79-901e-652b8a222b1f" />

Run EchoChatClient.java
---
<img width="750" alt="image" src="https://github.com/user-attachments/assets/2635d6b3-430e-45a3-94e3-5565239c2cdc" />

Run EchoChatMultiServer.java
---
<img width="750" alt="image" src="https://github.com/user-attachments/assets/0701c19a-83f0-43f2-8362-c11ed5dd4c08" />

---

EchoServer.java
---
<img width="750" alt="image" src="https://github.com/user-attachments/assets/e3d43121-1b75-45a9-b20b-83237cd6db2d" />

<img width="750" alt="image" src="https://github.com/user-attachments/assets/2e9df899-f0c5-4cde-8668-2f3ac29cbae9" />

EchoClient.java
---
<img width="750" alt="image" src="https://github.com/user-attachments/assets/65e0e845-d6a9-4b64-a2c4-edeaa91a6198" />

<img width="750" alt="image" src="https://github.com/user-attachments/assets/68e4eabc-4c8c-44a7-98e3-23bfe2c564ab" />

Run EchoServer.java
---
<img width="750" alt="image" src="https://github.com/user-attachments/assets/16020c0b-e809-4976-a3be-793bbd39d1ff" />

Run EchoClient.java
---
<img width="750" alt="image" src="https://github.com/user-attachments/assets/6196e275-0a7b-4cac-b06c-536a317937f2" />

Tại Client, nhập nội dung message là Hello
--- 
<img width="750" alt="image" src="https://github.com/user-attachments/assets/99357efe-ca54-4f89-bc2d-20eedab32069" />

Tại Server
---
<img width="750" alt="image" src="https://github.com/user-attachments/assets/de48b67d-97b7-4d5d-b854-223371c1ff08" />

Tại Cient, tiếp tục nhập nội dung là How are you
---
<img width="750" alt="image" src="https://github.com/user-attachments/assets/61dad9da-1dc2-4f71-a562-d208cae7a5fe" />

Tại Server
---
<img width="750" alt="image" src="https://github.com/user-attachments/assets/28376ea3-669b-497e-b1f0-7687fe232fa1" />

---

MulticastSender.java
---
<img width="750" alt="image" src="https://github.com/user-attachments/assets/e7104e25-1f08-4e2c-81e3-73e8fd83f423" />

MulticastReceiver.java
---
<img width="750" alt="image" src="https://github.com/user-attachments/assets/e3b2dcfb-8b57-4104-9f77-60dec66e7ea1" />

Run MulticastSender.java
---
<img width="750" alt="image" src="https://github.com/user-attachments/assets/0efd51fb-9eda-4df1-aebc-e7ec464ec8ac" />

Run MulticastReceiver.java
---
<img width="750" alt="image" src="https://github.com/user-attachments/assets/6c269ad4-9392-4e12-b695-cbd5079f893d" />

--- 
<img width="750" alt="image" src="https://github.com/user-attachments/assets/f8bf3ba5-2f21-4a3a-b1ba-b8f7b5d5151f" />

<img width="750" alt="image" src="https://github.com/user-attachments/assets/8836a932-b470-4daf-9106-bcfc3b05b287" />

---

## Tài liệu tham khảo

- [Xây dựng ứng dụng Client-Server với Socket trong Java – gpcoder.com](https://gpcoder.com/3679-xay-dung-ung-dung-client-server-voi-socket-trong-java/)

---

## Tác giả

- GitHub: [@nhunguy-swe](https://github.com/nhunguy-swe)

---

## Giấy phép

Dự án này được thực hiện cho mục đích học tập/bài tập cá nhân. Bạn có thể tham khảo, sử dụng lại code cho mục đích học tập.

