---
title: "Worklog Tuần 11"
weight: 2
chapter: false
pre: " <b> 1.11. </b> "
---

---

### Mục tiêu tuần 11:

#### Phần 1 – Serverless với Amplify Authentication và Storage

- Tìm hiểu cách hoạt động của Amplify Libraries, đặc biệt là Amplify Auth và Storage.
- Kết nối ứng dụng web với Cognito để quản lý người dùng.
- Xây dựng chức năng upload từ frontend và lưu file trực tiếp vào S3 thông qua Amplify Storage.
- Hiểu rõ ba chế độ truy cập file: public, protected và private.
- Nắm được cơ chế giao tiếp giữa Cognito – S3 – Amplify trong một ứng dụng serverless.

#### Phần 2 – Serverless: Xây dựng Frontend giao tiếp với API Gateway

- Hiểu cách tạo API Gateway và ánh xạ request đến Lambda.
- Viết frontend (JavaScript/React) để gọi API Gateway → Lambda → DynamoDB.
- Kiểm thử API bằng Postman và từ chính frontend.
- Nắm chắc quy trình toàn bộ đường đi của dữ liệu:  
  **Frontend → API Gateway → Lambda → DynamoDB**.

---

### Các công việc đã thực hiện trong tuần

| Thứ | Nội dung | Bắt đầu | Hoàn thành | Nguồn |
| --- | -------- | ------- | ---------- | ------ |
| 2 | **Khởi động Amplify và chuẩn bị môi trường**<br>• Tìm hiểu Amplify Libraries, CLI và UI Components.<br>• Khởi tạo project tích hợp Amplify.<br>• Cài đặt `aws-amplify` và `@aws-amplify/ui`.<br>• Cấu hình AWS trong local. | 17/11/2025 | 17/11/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | **Xác thực người dùng với Amplify Auth**<br>• Tạo User Pool và Identity Pool.<br>• Thiết lập cấu hình Amplify Auth trong frontend.<br>• Sử dụng Amplify UI Components để tạo giao diện login.<br>• Thử luồng tạo tài khoản, đăng nhập, xác nhận mã và đổi mật khẩu. | 18/11/2025 | 18/11/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | **Lưu trữ file qua Amplify Storage**<br>• Tạo S3 bucket bằng Amplify.<br>• Cài đặt quyền truy cập public/protected/private.<br>• Viết chức năng upload từ frontend lên S3.<br>• Kiểm tra lại trên S3 console.<br>• Viết logic list file và lấy URL. | 19/11/2025 | 19/11/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | **Tạo API Gateway kết nối Lambda**<br>• Xây dựng REST API.<br>• Gắn các route CRUD vào Lambda.<br>• Bật CORS cho frontend.<br>• Cập nhật ARN mới cho Lambda functions. | 20/11/2025 | 20/11/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | **Kiểm thử API bằng Postman**<br>• Gửi request với các method GET/POST/DELETE.<br>• Đính kèm token Cognito trong header.<br>• Theo dõi log bằng CloudWatch.<br>• Fix lỗi CORS và quyền IAM. | 21/11/2025 | 21/11/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 7 | **Tích hợp frontend với API Gateway**<br>• Viết service JS gọi API Gateway.<br>• Tự động gắn token Cognito.<br>• Hiển thị dữ liệu trả về từ Lambda/DynamoDB.<br>• Hoàn thiện quy trình end-to-end: Frontend → API → Lambda → DynamoDB.<br>• Dọn dữ liệu test. | 22/11/2025 | 22/11/2025 | <https://cloudjourney.awsstudygroup.com/> |

---

### Kết quả đạt được trong tuần 11

#### 1. Thiết lập thành công Authentication bằng Amplify + Cognito

- Hoàn thiện đầy đủ các luồng: đăng nhập, đăng ký, xác thực bằng mã và đặt lại mật khẩu.
- Frontend lấy được JWT token để sử dụng khi gọi API Gateway.
- Hiểu rõ cách Cognito quản lý danh tính qua User Pool và Identity Pool.

---

#### 2. Lưu trữ và quản lý file bằng Amplify Storage + S3

- Upload file trực tiếp từ frontend lên S3 thành công.
- Bucket S3 được tạo tự động bởi Amplify.
- Thử nghiệm đầy đủ 3 loại quyền truy cập.
- Hoàn thiện các hàm xử lý file: upload, list, get URL, và tùy chọn delete.

---

#### 3. Xây dựng API Gateway phục vụ hệ thống DMS

- Tạo REST API hoàn chỉnh với các route CRUD.
- Kết nối trực tiếp đến Lambda của tuần trước.
- Cấu hình CORS chuẩn cho frontend.
- Gửi request kèm JWT token và kiểm thử toàn bộ bằng Postman.

---

#### 4. Tích hợp frontend với API Gateway

- Viết logic frontend gửi request kèm token Cognito.
- Hiển thị danh sách metadata từ DynamoDB.
- Hoàn thiện luồng tổng thể:

---

### Tóm tắt kiến thức trong tuần

#### Amplify
- Amplify Auth sử dụng Cognito làm hệ thống xác thực.
- Amplify Storage hỗ trợ thao tác S3 đơn giản từ frontend.
- Bộ UI component giúp tạo trang login nhanh.

#### Cognito (Authentication)
- User Pool: quản lý tài khoản.
- Identity Pool: cấp quyền truy cập tài nguyên AWS.
- JWT token dùng khi gửi request đến API Gateway.

#### S3 (Storage)
- Hỗ trợ phân quyền file theo public / protected / private.
- Upload trực tiếp từ client thông qua Amplify.

#### API Gateway
- Điều phối request đến Lambda.
- CORS rất quan trọng để frontend hoạt động.
- Có thể yêu cầu xác thực bằng token Cognito.

#### Lambda + DynamoDB
- Lambda thực thi các hàm CRUD.
- DynamoDB lưu metadata tài liệu.
- Frontend chỉ giao tiếp qua API Gateway.

---