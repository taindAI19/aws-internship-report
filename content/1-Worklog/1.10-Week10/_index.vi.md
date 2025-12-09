---
title: "Worklog Tuần 10"
weight: 2
chapter: false
pre: " <b> 1.10. </b> "
---

---

### Mục tiêu tuần 10:

#### Phần 1 – Xây dựng backend Document Management System (DMS) với Lambda và DynamoDB

- Nắm được kiến trúc hoạt động của một hệ thống quản lý tài liệu.
- Thiết kế bảng DynamoDB dựa trên nhu cầu truy cập thực tế của ứng dụng.
- Viết các Lambda Function đảm nhiệm việc tạo mới, lấy danh sách, truy vấn chi tiết và xoá tài liệu.
- Cấu hình IAM Role cho Lambda theo nguyên tắc tối thiểu quyền.
- Thực hiện kiểm thử thông qua test event và giám sát bằng CloudWatch Logs.
- Chuẩn bị phần backend để tuần sau tích hợp thêm API Gateway và Amplify.

#### Phần 2 – Hiểu cách DMS sẽ được mở rộng trong những tuần kế tiếp

- Nắm rõ vai trò của Cognito, Amplify Storage trong hệ thống.
- Biết cách DynamoDB Streams được dùng để đồng bộ dữ liệu sang OpenSearch phục vụ tìm kiếm.
- Hình dung cách toàn bộ backend sẽ được triển khai bằng AWS SAM.
- Hiểu luồng CI/CD dự kiến vận hành trên AWS CodePipeline.

---

### Các công việc đã thực hiện trong tuần

| Thứ | Nội dung triển khai                                                                                                                                                                                                                                                                                                                       | Bắt đầu | Hoàn thành | Nguồn |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------- | ---------- | ------ |
| 2   | **Phân tích toàn bộ kiến trúc DMS**<br>• Làm rõ mục tiêu: upload, xem, tải về, xoá và tìm kiếm tài liệu.<br>• Xác định các dịch vụ chính: Lambda, DynamoDB, S3, Cognito, API Gateway.<br>• Phân tích luồng xử lý từ lúc upload đến khi lưu metadata và phục vụ tìm kiếm.<br>• Xây dựng danh sách API cần có cho backend.                      | 10/11/2025   | 10/11/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 3   | **Thiết kế bảng DynamoDB dùng cho metadata tài liệu**<br>• Tạo bảng `Documents` (PK: `userId`, SK: `documentId`).<br>• Xác định các attributes như filename, fileType, size, tags, createdAt, updatedAt.<br>• Phân tích access patterns: truy vấn theo user, lấy chi tiết theo documentId, lọc theo tag.<br>• Chuẩn bị data mẫu và thử nghiệm bằng Console/CLI. | 11/11/2025   | 11/11/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | **Tạo IAM Role dành cho Lambda**<br>• Khởi tạo role `DMSLambdaRole`.<br>• Cấp quyền DynamoDB CRUD (GetItem, Query, PutItem, DeleteItem).<br>• Cho phép ghi log vào CloudWatch Logs.<br>• Rà lại trust policy cho Lambda.<br>• Xác nhận role hoạt động đúng bằng cách test trực tiếp trong Lambda.                                                | 12/11/2025   | 12/11/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | **Viết Lambda CreateDocument**<br>• Kiểm tra input do người dùng gửi lên.<br>• Sinh `documentId` dạng UUID.<br>• Lưu metadata vào bảng thông qua `put_item`.<br>• Ghi log để phục vụ theo dõi.<br>• Kiểm thử qua test event và CloudWatch Logs.<br>• Xử lý lỗi nhập thiếu, lỗi DynamoDB hoặc lỗi bất thường.                                      | 13/11/2025   | 13/11/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | **Viết Lambda GetDocuments và GetDocumentById**<br>• Viết logic Query toàn bộ tài liệu theo userId.<br>• Thêm khả năng phân trang bằng LastEvaluatedKey.<br>• Viết hàm lấy chi tiết một document theo documentId.<br>• Chuẩn hoá JSON trả về để khớp với front-end.<br>• Kiểm thử bằng dữ liệu thật trong DynamoDB.                              | 14/11/2025   | 14/11/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 7   | **Viết Lambda DeleteDocument và cleanup dữ liệu**<br>• Kiểm tra sự tồn tại của tài liệu trước khi xoá.<br>• Xoá metadata bằng `delete_item`.<br>• Chuẩn bị logic xoá file S3 (sẽ làm trong tuần tới).<br>• Ghi log chi tiết quá trình xoá.<br>• Dọn dẹp các bản ghi test không còn dùng.                                               | 15/11/2025   | 15/11/2025      | <https://cloudjourney.awsstudygroup.com/> |

---

### Kết quả đạt được trong tuần 10

#### 1. Hoàn chỉnh bảng DynamoDB với mô hình tối ưu

- Xây dựng bảng `Documents` đáp ứng trọn nhu cầu lưu metadata của DMS.
- Thiết kế khóa phân vùng/sắp xếp phù hợp với việc truy vấn theo user và lấy chi tiết tài liệu.
- Cấu trúc dữ liệu dễ mở rộng sang DynamoDB Streams hoặc tích hợp OpenSearch.

---

#### 2. Hoàn thành bộ Lambda CRUD cho hệ thống

- Tạo tài liệu mới bằng CreateDocument.
- Lấy danh sách tài liệu theo userId qua GetDocuments.
- Truy vấn chi tiết bằng GetDocumentById.
- Xoá tài liệu bằng DeleteDocument.
- Toàn bộ logic theo hướng serverless, log rõ ràng và có xử lý lại khi gặp lỗi.

---

#### 3. Triển khai đúng các best practices về bảo mật và giám sát

- IAM Role được cấu hình theo nguyên tắc “ít quyền nhất”.
- CloudWatch Logs phục vụ theo dõi toàn bộ quá trình xử lý.
- Bộ xử lý lỗi đủ rõ ràng: lỗi input, lỗi DynamoDB hoặc bản ghi không tồn tại.

---

#### 4. Hiểu đầy đủ kiến trúc tổng thể của hệ thống DMS

- Nắm được mối liên kết giữa Authentication – API – Storage – Metadata.
- Biết cách Lambda sẽ được tích hợp vào API Gateway ở tuần kế.
- Có nền tảng kỹ thuật để tuần sau tiếp tục với Amplify Authentication và Storage.

---

### Tóm tắt kiến thức trong tuần

#### AWS DynamoDB
- Thiết kế bảng theo access patterns.
- Dùng đúng Partition/Sort Key.
- Thành thạo các thao tác PutItem, GetItem, Query, DeleteItem (Boto3).

#### AWS Lambda
- Viết hàm serverless cho CRUD.
- Tạo IAM Role cùng policy phù hợp.
- Làm quen với logging và giám sát bằng CloudWatch.
- Xử lý lỗi theo chuẩn dùng trong sản phẩm.

#### Kiến trúc DMS
- Metadata nằm trong DynamoDB.
- File thực được lưu trên S3.
- Xác thực người dùng bằng Cognito.
- API định tuyến qua API Gateway và Lambda.

---
