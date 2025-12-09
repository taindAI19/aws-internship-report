---
title: "Worklog Tuần 9"

weight: 1
chapter: false
pre: " <b> 1.9. </b> "
---
---

### Mục tiêu tuần 9:

**Phần 1 – Tối ưu chi phí EC2 bằng Lambda Function**

* Nắm được cơ chế tự động bật/tắt EC2 nhằm giảm chi phí vận hành.
* Tạo hệ thống tag để xác định các máy chủ cần được xử lý theo lịch.
* Xây dựng Lambda Function quản lý Start/Stop EC2 dựa trên tag.
* Tạo lịch chạy định kỳ bằng EventBridge Scheduler.
* Theo dõi hoạt động thực tế thông qua CloudWatch Logs.
* Thu hồi toàn bộ tài nguyên sau khi thử nghiệm xong.

**Phần 2 – Tối ưu chi phí EC2 với Savings Plan**

* Tìm hiểu Savings Plan và nguyên tắc giảm giá dựa trên mức cam kết.
* Phân biệt Compute Savings Plans và EC2 Instance Savings Plans.
* Hiểu cơ chế commit USD/giờ và cách công cụ estimator tính toán.
* Biết quy trình mua và áp dụng Savings Plan theo chuẩn AWS.
* Thực hành ước tính chi phí qua AWS Pricing Calculator.

---

### Các công việc triển khai trong tuần

| Thứ | Công việc chi tiết | Bắt đầu | Hoàn thành | Nguồn |
| --- | ------------------ | ------- | ---------- | ------ |
| 2 | **Phân tích mô hình tối ưu hóa EC2**<br>• Xác định vấn đề lãng phí khi EC2 chạy 24/7 nhưng khối lượng sử dụng ít.<br>• Mô tả luồng hoạt động: User → EventBridge → Lambda → EC2 API.<br>• Nhận dạng workload phù hợp với cơ chế tự động Start/Stop.<br>• Xem xét rủi ro và giới hạn của việc bật/tắt EC2. | 03/11/2025 | 03/11/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | **Tạo Tag phân loại EC2**<br>• Thiết lập Tag Key: `Schedule`.<br>• Tag Value mẫu: `office-hours`, `training-only`, `weekend-shutdown`.<br>• Gán tag vào các EC2 cần tự động hóa.<br>• Kiểm tra bằng CLI: `describe-instances --filters tag:Schedule=office-hours`. | 04/11/2025 | 04/11/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | **Tạo IAM Role cho Lambda**<br>• Tạo role: `LambdaEC2ScheduleRole`.<br>• Gán policy: `AmazonEC2FullAccess` (dùng cho mục đích lab).<br>• Thêm quyền ghi log: `AWSLambdaBasicExecutionRole`.<br>• Kiểm tra trust relationship với `lambda.amazonaws.com`. | 05/11/2025 | 05/11/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | **Phát triển Lambda Start/Stop EC2**<br>• Viết code Python (boto3) để StartInstances/StopInstances.<br>• Thêm logic lọc instance theo tag `<Schedule>`.<br>• Ghi log instance ID được bật/tắt.<br>• Kiểm thử bằng “Test event”. | 06/11/2025 | 06/11/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | **Tích hợp EventBridge Scheduler**<br>• Tạo rule bật EC2 lúc 08:00 AM.<br>• Tạo rule tắt EC2 lúc 18:00 PM.<br>• Gán Lambda làm target.<br>• Xem log trong CloudWatch để xác nhận hoạt động. | 07/11/2025 | 07/11/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 7 | **Kiểm thử & Dọn dẹp**<br>• Xác minh EC2 bật/tắt đúng lịch.<br>• Theo dõi CloudWatch Logs để xử lý lỗi quyền hạn.<br>• Xóa rule, Lambda Function và IAM Role sau khi hoàn tất.<br>• So sánh chi phí EC2 trước và sau tối ưu hóa. | 08/11/2025 | 08/11/2025 | <https://cloudjourney.awsstudygroup.com/> |

---

### Kết quả đạt được trong tuần 9

**1. Tối ưu chi phí EC2 qua Lambda**

* Thiết lập thành công quy trình bật/tắt EC2 dựa trên giờ làm việc.
* Hiểu rõ cách dùng Tag để nhóm EC2 cần tối ưu hóa.
* Viết Lambda Function điều khiển Start/Stop bằng boto3.
* Tự động hóa hoàn toàn thông qua EventBridge Scheduler.
* Ghi nhận log đầy đủ: thời gian, instance ID, lỗi permission.
* Tiết kiệm được 50–70% chi phí đối với workload không chạy liên tục.

---

**2. Tối ưu chi phí với Savings Plan**

* Hiểu cơ chế giảm giá của Savings Plan dựa trên cam kết USD/giờ.
* Sử dụng Pricing Calculator để ước tính mức commit phù hợp.
* Nắm rõ sự khác nhau giữa hai loại Savings Plan:  
  * **Compute Savings Plan** – linh hoạt, áp dụng đa dịch vụ.  
  * **EC2 Instance Savings Plan** – tiết kiệm cao nhưng ràng buộc hơn.  
* Nắm quy trình đăng ký và kích hoạt Savings Plan.
* Thấy rõ lợi ích tiết kiệm có thể đạt đến ~66%.

---

### Tóm tắt kiến thức đạt được

**AWS Lambda + EC2 Automation**

* Vận hành tự động bật/tắt EC2 bằng Lambda.  
* Sử dụng Boto3 để tương tác với API EC2.  
* Dùng EventBridge Scheduler để đặt lịch chạy.  
* CloudWatch Logs để kiểm tra và xử lý lỗi.

**AWS Savings Plans**

* Cơ chế commit chi phí để giảm giá sử dụng hạ tầng.  
* Áp dụng phù hợp cho workload chạy liên tục 24/7.  
* Phân loại Compute và EC2 Plans.  
* Kết hợp Savings Plan + Auto Scheduling để tối ưu chi phí toàn diện.

---
