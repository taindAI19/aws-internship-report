---
title: "Worklog Tuần 4"
weight: 1
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu tuần 4

* Làm chủ cách **cấp quyền truy cập vào tài nguyên AWS** cho ứng dụng một cách an toàn.  
* Phân biệt rõ ràng cơ chế hoạt động giữa **Access Key/Secret Access Key** và **IAM Role**.  
* Biết quy trình **tạo và gán IAM Role cho EC2 Instance**, giúp ứng dụng truy cập dịch vụ AWS mà không cần gửi kèm thông tin xác thực trong mã nguồn.  
* Làm quen với môi trường phát triển dựa trên trình duyệt **AWS Cloud9**, nơi đã tích hợp sẵn AWS CLI.  
* Thực hành **viết mã, chạy thử, debug** và quản lý mã nguồn trực tiếp trên Cloud9.  

---

### Các công việc triển khai trong tuần

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --------- | ------------- | ---------------- | --------------- |
| 2 | - Tổng quan về **IAM** và cơ chế kiểm soát truy cập AWS <br> - Ôn lại khái niệm **User**, **Group**, **Policy**, **Role** <br> - Tìm hiểu cách AWS xác thực & ủy quyền truy cập | 22/09/2025 | 22/09/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | - Thử nghiệm cấp quyền bằng **Access Key/Secret Access Key** <br> - Kiểm thử ứng dụng truy cập AWS bằng Access Key <br> - Phân tích các rủi ro và điểm yếu khi nhúng Access Key trong ứng dụng | 23/09/2025 | 23/09/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Tạo **IAM Role dành cho EC2** <br> - Gán role cho instance và kiểm tra quyền truy cập S3/DynamoDB qua ứng dụng mẫu Node.js <br> - Kiểm tra lại ứng dụng sau khi thu hồi quyền | 24/09/2025 | 24/09/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Khởi tạo và làm quen với **Cloud9 IDE** <br> - Thiết lập workspace, cấu hình môi trường làm việc <br> - Trải nghiệm terminal, file explorer, debugger, syntax highlight | 25/09/2025 | 25/09/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - **Bài tập tổng hợp:** <br>&emsp; + Viết script thao tác AWS CLI trong Cloud9 <br>&emsp; + Xây dựng ứng dụng Node.js CRUD (User Management) chạy trực tiếp trên Cloud9 <br>&emsp; + Xóa tài nguyên để tránh tính phí | 26/09/2025 | 26/09/2025 | <https://cloudjourney.awsstudygroup.com/> |

---

### Kết quả đạt được trong tuần 4

* Nắm rõ điểm khác biệt giữa **IAM Role** và **Access Key**, cũng như lý do tại sao việc dùng role là lựa chọn an toàn hơn trong thực tế.  
* Biết cách tạo **IAM Role** với quyền hạn phù hợp, chẳng hạn truy cập đọc/ghi vào S3.  
* Gán IAM Role cho EC2 Instance và cho phép ứng dụng chạy trên đó truy cập dịch vụ AWS mà không cần thông tin đăng nhập cố định.  
* Sử dụng thành thạo **AWS Cloud9** để:  
  * Tạo workspace phát triển.  
  * Kết nối tới EC2.  
  * Chạy các lệnh AWS CLI, viết và kiểm thử mã trực tiếp.  
* Triển khai ứng dụng Node.js nhỏ kết nối với S3 hoặc DynamoDB ngay trong Cloud9.  
* Hiểu quy trình **thu hồi, xoá tài nguyên** sau bài thực hành nhằm tối ưu chi phí.  

---

### Tóm tắt kiến thức tích luỹ

- **IAM Role:** Cơ chế cấp quyền động, giảm rủi ro bảo mật do không cần dùng Access Key.  
- **Access Key:** Hiểu điểm yếu khi dùng trực tiếp trong code hoặc trên máy developer.  
- **AWS Cloud9:** Một môi trường lập trình linh hoạt trên browser, hỗ trợ nhiều ngôn ngữ và tích hợp AWS CLI.  
- **AWS CLI/SDK:** Công cụ để truy cập và thao tác dịch vụ AWS dựa trên IAM Role.  
- **Quy trình triển khai thực tế:** Thiết lập môi trường, viết và chạy ứng dụng, kiểm tra quyền truy cập, và dọn dẹp tài nguyên khi hoàn thành.  

---
