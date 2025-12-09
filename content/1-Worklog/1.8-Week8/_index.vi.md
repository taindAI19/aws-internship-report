---
title: "Worklog Tuần 8"
weight: 1
chapter: false
pre: " <b> 1.8. </b> "
---

### Mục tiêu tuần 8:

Tuần này tập trung vào hai nhóm nội dung: lưu trữ NoSQL với DynamoDB và bộ nhớ đệm tốc độ cao bằng Redis trong ElastiCache. Mục tiêu chính là hiểu cách hai dịch vụ này vận hành, cấu trúc dữ liệu, khả năng mở rộng, cùng việc kết hợp chúng để tăng tốc các tác vụ đọc trong hệ thống.

---

## Phần 1 – Amazon DynamoDB

* Khảo sát mô hình dữ liệu key–value và document, đặc trưng của DynamoDB.
* Tìm hiểu cơ chế phân vùng dữ liệu (partition), cách lựa chọn khóa để tránh điểm nóng.
* Đi sâu vào các khái niệm quan trọng: RCU/WCU, chế độ On-Demand, TTL, Streams, và Global Tables.
* Thiết kế bảng có Partition Key và Sort Key; thử cấu hình thêm GSI và LSI cho nhiều kiểu truy vấn khác nhau.
* Làm quen nhóm thao tác CRUD và truy vấn nâng cao qua Query/Scan, kết hợp FilterExpression và ConditionExpression.
* Sử dụng AWS CLI và file JSON để tương tác bảng.
* Nhập dữ liệu thử nghiệm nhằm đánh giá hiệu năng truy vấn.

---

## Phần 2 – Amazon ElastiCache for Redis

* Ôn lại nguyên lý của bộ nhớ đệm in-memory và cách Redis tổ chức cụm (cluster mode enabled/disabled).
* Tạo môi trường Redis: cấu hình node, subnet group, security group và parameter group.
* Kết nối từ EC2 thông qua redis-cli để kiểm tra hoạt động.
* Thử các lệnh cơ bản: SET/GET, TTL, EXPIRE, và snapshot RDB.
* Áp dụng mô hình Cache-Aside để kết hợp Redis với DynamoDB.
* So sánh độ trễ giữa truy vấn cache và truy vấn DynamoDB.
* Thu hồi tài nguyên sau khi hoàn thành.

---

### Các công việc thực hiện

| Thứ | Nội dung triển khai | Bắt đầu | Hoàn thành | Tài liệu |
| --- | ------------------- | ------- | ---------- | -------- |
| 2 | **Tổng quan DynamoDB** <br> Khám phá cấu trúc NoSQL, cơ chế phân vùng, throughput, và các thành phần như GSI/LSI, TTL, Streams. Hiểu cách DynamoDB phân phối dữ liệu theo Partition Key và tác động của lựa chọn khóa đến hiệu năng. | 27/10/2025 | 27/10/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | **Thiết kế bảng & truy vấn** <br> Tạo bảng với khóa phân vùng và khóa sắp xếp; bổ sung GSI để mở rộng đường truy vấn. Kiểm tra cơ chế TTL, thực hiện đủ CRUD và so sánh Query/Scan trong các tình huống thực tế. | 28/10/2025 | 28/11/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | **Làm việc với CLI** <br> Khởi tạo bảng bằng CLI, nhập dữ liệu JSON mẫu, chạy truy vấn bằng KeyConditionExpression, cập nhật có điều kiện và theo dõi mức tiêu thụ throughput. | 29/10/2025 | 29/10/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | **Redis – Cấu trúc và triển khai** <br> Chuẩn bị subnet group, security group, tạo cụm Redis có primary và replica, bật failover, sau đó kiểm tra kết nối từ EC2. | 30/10/2025 | 30/10/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | **Tích hợp DynamoDB – Redis** <br> Kiểm tra redis-cli với GET/SET/TTL, thử snapshot, thiết lập Cache-Aside (cache hit/miss) và đo độ trễ giữa Redis và DynamoDB. | 31/10/2025 | 31/10/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 7 | **Dọn tài nguyên và đánh giá** <br> Xóa Redis Cluster và các group liên quan; gỡ bảng DynamoDB thử nghiệm. Kiểm tra billing để xác định chi phí phát sinh và ghi nhận sự khác biệt tốc độ giữa cache và database. | 1/11/2025 | 1/11/2025 | <https://cloudjourney.awsstudygroup.com/> |

---

### Kết quả trong tuần 8

#### 1. DynamoDB

**Thiết kế & mô hình hóa dữ liệu**

* Hiểu rõ cách DynamoDB phân tán dữ liệu và mở rộng theo chiều ngang.
* Thực hành xây dựng khóa phân vùng/sắp xếp phù hợp để giảm va chạm partition.
* Trải nghiệm vai trò của chỉ mục phụ GSI/LSI trong việc định hình access pattern.

**Truy vấn & cập nhật**

* Hoàn chỉnh toàn bộ CRUD qua giao diện console và CLI.
* Sử dụng thành thạo KeyConditionExpression cho truy vấn có điều kiện.
* Biết kết hợp FilterExpression, UpdateExpression trong tình huống lọc phức tạp.
* Khảo sát Scan và giới hạn của phương pháp này khi dữ liệu lớn.

**Tính năng nâng cao**

* Kích hoạt TTL và quan sát hành vi tự loại bỏ bản ghi.
* Thử DynamoDB Streams để xem cách log sự thay đổi.
* Đánh giá chi phí dựa trên nhu cầu đọc/ghi và mức tiêu thụ thực tế.

---

#### 2. ElastiCache for Redis

**Triển khai cụm Redis**

* Xây dựng cụm Redis trong VPC với cấu hình mạng đầy đủ.
* Kiểm tra hoạt động replication và failover.
* Thử kết nối từ EC2 để xác nhận môi trường hoạt động ổn định.

**Thao tác và quan sát**

* Thực hiện SET, GET, DEL, TTL, EXPIRE trong nhiều tình huống.
* Đo ảnh hưởng của snapshot RDB lên trạng thái dữ liệu.
* Đánh giá hành vi cache khi dung lượng bị giới hạn.

---

#### 3. Kết hợp DynamoDB – Redis (Cache-Aside)

* Xây dựng luồng xử lý: kiểm tra cache → truy vấn DynamoDB nếu thiếu → đưa dữ liệu trở lại Redis.
* So sánh kết quả cache hit và miss, đo độ trễ thật để rút ra đặc tính hiệu năng.
* Nhận ra lý do các hệ thống đọc nhiều thường dùng Redis như lớp đệm.
* Nhận diện các trường hợp áp dụng điển hình: session, user profile, dữ liệu tra cứu tần suất cao.

---

### Tổng hợp kiến thức

**DynamoDB**

* Mô hình NoSQL phân tán.
* Cách chọn Partition Key và Sort Key hợp lý.
* Các dạng truy vấn phổ biến và các biểu thức liên quan.
* Cơ chế throughput theo RCU/WCU hoặc On-Demand.
* TTL và Streams cho quản lý vòng đời dữ liệu.

**ElastiCache Redis**

* Mô hình cache tốc độ cao dựa trên RAM.
* Cấu hình cluster, replica và failover.
* TTL, snapshot và xử lý dữ liệu tạm thời.

**Tích hợp DynamoDB – Redis**

* Áp dụng Cache-Aside để giảm tải đọc.
* Phân tích cache hit/miss.
* Tối ưu hóa hiệu năng trong dịch vụ lớn.

---
