---
title: "Worklog Tuần 6"

weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---

---

### Mục tiêu tuần 6:

* Làm quen với phương thức **giám sát, phân tích hiệu năng** qua Performance Insights, Monitoring và Enhanced Logging.  
* Hiểu rõ kiến trúc tổng thể của **Amazon RDS**, bao gồm các loại engine như MySQL, PostgreSQL, MariaDB, SQL Server…  
* Thực hành **backup – restore – snapshot – automated backup – failover** để đảm bảo khả năng phục hồi dữ liệu.  
* Tạo, cấu hình và vận hành một **RDS Instance** từ bước nền tảng đến cấu hình nâng cao.  
* Xây dựng **parameter group**, **subnet group**, **security group** dành riêng cho RDS.  
* Thiết lập kết nối giữa RDS và các môi trường như **EC2**, **Cloud9**, hoặc máy local.  
* Thành thạo phương pháp **scale tài nguyên** và **tối ưu chi phí**, đồng thời biết cách dọn dẹp tài nguyên khi không còn nhu cầu sử dụng.

---

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc                                                                                                                                                                                              | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------ | --------------- | -------------- |
| 2   | **Giới thiệu RDS** <br>  + Các lựa chọn engine <br>  + Mô hình Multi-AZ và Read Replica <br>  + Chu kỳ backup & snapshot                                                                                 | 13/10/2025   | 13/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 3   | **Khởi tạo RDS Instance** <br>  + Xây dựng Subnet Group <br>  + Cấu hình Security Group dành cho Cloud9/EC2 <br>  + Chọn engine, dung lượng và loại instance                                           | 14/10/2025   | 14/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | **Kết nối & thao tác trên RDS** <br>  + Truy cập từ EC2 hoặc Cloud9 <br>  + Tạo schema & bảng dữ liệu <br>  + Hành động CRUD bằng MySQL hoặc PostgreSQL client                                         | 15/10/2025   | 15/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | **Monitoring – Backup – Restore** <br>  + Tạo snapshot thủ công <br>  + Khôi phục instance từ snapshot <br>  + Kiểm tra CPU, kết nối, throughput <br>  + Dùng Performance Insights phân tích truy vấn | 16/10/2025   | 16/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | **Scaling – Tối ưu hóa – Thu hồi tài nguyên** <br>  + Tăng/giảm instance class <br>  + Mở rộng dung lượng storage <br>  + Điều chỉnh backup retention hợp lý <br>  + Xoá snapshot & RDS không còn dùng | 17/10/2025   | 17/10/2025      | <https://cloudjourney.awsstudygroup.com/> |

---

### Kết quả đạt được trong tuần 6:

**1. Làm chủ quy trình Backup – Restore – Snapshot:**  
* Thực hiện tạo snapshot thủ công.  
* Khôi phục (restore) sang một RDS instance mới.  
* Quan sát thời điểm backup (backup window).  
* Xác nhận automated backup được tạo tự động mỗi ngày.

**2. Hiểu rõ cơ chế hoạt động của Amazon RDS:**  
* Nhận biết sự khác nhau giữa Single-AZ, Multi-AZ và Read Replica.  
* Nắm cách automated backup hoạt động và thời gian lưu trữ.  
* Hiểu snapshot là bản lưu trữ thủ công và không tự động xoá.

**3. Kết nối RDS từ local/EC2/Cloud9:**  
* Cài MySQL/PostgreSQL client để truy cập.  
* Kết nối bằng endpoint dạng: mysql -h endpoint.amazonaws.com -u admin -p
* Tạo database, table và thực hiện các câu lệnh CRUD:
  * `CREATE DATABASE demo;`  
  * `CREATE TABLE users (...);`  
  * `INSERT`, `SELECT`, `UPDATE`, `DELETE`

**4. Cấu hình một RDS Instance hoàn chỉnh:**  
* Tạo DB Subnet Group gồm 2 subnet ở hai AZ khác nhau.  
* Tạo Security Group cho phép kết nối (port 3306/5432).  
* Cài đặt:  
  * Engine MySQL/PostgreSQL  
  * Instance class db.t3.micro  
  * Storage gp3 20GB  
  * Backup retention  
  * Endpoint private hoặc public  

**5. Giám sát hiệu năng & hoạt động hệ thống:**  
* Theo dõi CPU, RAM, số lượng kết nối qua mục Monitoring.  
* Dùng Performance Insights để tìm truy vấn gây tải nặng.  
* Kiểm tra Slow Query Log khi được bật.

**6. Tối ưu chi phí và scale tài nguyên:**  
* Thay đổi instance class t3.micro → t3.small theo nhu cầu tải.  
* Kéo dung lượng storage lên 30GB khi cần.  
* Điều chỉnh thời gian giữ backup xuống 3 ngày để tiết kiệm chi phí.  
* Xóa snapshot không còn phục vụ mục đích lưu trữ.

**7. Dọn dẹp tài nguyên:**  
* Xóa RDS instance.  
* Xóa subnet group và security group tương ứng.  
* Dọn dẹp toàn bộ snapshot cũ.

---

### Tóm tắt kiến thức đạt được

* Hiểu cơ chế hoạt động của Amazon RDS và các engine phổ biến.  
* Tạo, vận hành và kết nối tới RDS từ Cloud9, EC2 hoặc máy local.  
* Nắm rõ nền tảng backup, snapshot và quá trình khôi phục.  
* Biết sử dụng Performance Insights để đánh giá hiệu năng truy vấn.  
* Làm quen với việc scale tài nguyên và tối ưu chi phí.  
* Thực hành dọn dẹp tài nguyên để tránh chi phí phát sinh.

---

