---
title: "Worklog Tuần 7"
weight: 1
chapter: false
pre: " <b> 1.7. </b> "
---

---

###  Mục tiêu tuần 7:

**Phần 1 – AWS CloudWatch**

* Hiểu được kiến trúc tổng thể của CloudWatch và chức năng từng thành phần: Metrics, Logs, Events, Dashboards, Alarms.
* Quan sát hoạt động của các metric từ EC2, RDS và Lambda trong môi trường vận hành thực tế.
* Thiết lập thu thập log và nắm được cách CloudWatch Logs lưu trữ – lập chỉ mục – tìm kiếm – phân tích dữ liệu.
* Cấu hình ngưỡng cảnh báo nhằm hỗ trợ giám sát liên tục.
* Xây dựng Dashboard để trực quan hóa tình trạng hệ thống theo thời gian thực.
* Kích hoạt Container Insights để theo dõi chi tiết hiệu năng container.
* Loại bỏ tài nguyên không còn sử dụng để tối ưu chi phí.

**Phần 2 – Hybrid DNS với Route 53 Resolver**

* Nắm được chiến lược kiến trúc khi tích hợp DNS on-premise với DNS trong AWS.
* Thiết lập các endpoint inbound và outbound của Route 53 Resolver.
* Xây dựng các bộ quy tắc Resolver Rules để điều hướng truy vấn DNS theo yêu cầu.
* Tích hợp DNS của Active Directory nội bộ với Private Hosted Zone của Route 53.
* Kiểm thử phân giải tên miền hai chiều giữa hệ thống nội bộ và AWS.
* Thu hồi toàn bộ tài nguyên (AD server, endpoint, cấu hình VPC) sau khi hoàn tất.

---

### Các công việc triển khai trong tuần

| Thứ | Công việc chi tiết | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | ------------------ | ------------ | --------------- | -------------- |
| 2 | **CloudWatch – Tổng quan & Kiến trúc** <br> • Ôn lại mục tiêu thiết kế của CloudWatch và cách nó tích hợp với dịch vụ AWS. <br> • Tìm hiểu cơ chế của Metrics, Logs, Alarms, Events, Dashboards và Container Insights. <br> • So sánh giữa giám sát cơ bản và giám sát chi tiết. <br> • Phân tích luồng hoạt động từ ứng dụng → agent → log group → metric → alarm → SNS → xử lý. <br> • Tạo biểu đồ đầu tiên dựa trên dữ liệu từ EC2. | 20/10/2025 | 20/10/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | **CloudWatch Metrics & Logs – Thực hành** <br> • Tạo Log Group và tìm hiểu luồng vận hành của Log Stream. <br> • Cài đặt CloudWatch Agent để thu dữ liệu CPU, RAM, network từ hệ điều hành. <br> • Chỉnh sửa file `cloudwatch-agent.json` để gửi log hệ thống và log ứng dụng. <br> • Tạo metric filter để phát hiện lỗi phổ biến (“ERROR”, “Failed”, “CRITICAL”). <br> • Gửi dữ liệu metric thủ công bằng AWS CLI. <br> • Thử đổi chế độ retention và theo dõi thay đổi. | 21/10/2025 | 21/10/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | **CloudWatch Alarm & Dashboard – Tự động hóa giám sát** <br> • Tạo cảnh báo CPU vượt 70% trong 5 phút. <br> • Tạo alarm theo dõi EC2 Status Check. <br> • Tích hợp SNS để gửi email thông báo. <br> • Dùng alarm để thực hiện hành động tự động như reboot EC2. <br> • Thiết kế Dashboard với nhiều widget hiển thị logs, metrics và trạng thái. <br> • Tạo Dashboard tổng hợp dữ liệu của EC2, RDS, network... <br> • Kích hoạt Container Insights để theo dõi CPU/memory và số lần restart. | 22/10/2025 | 22/10/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | **Route 53 Resolver – Kiến trúc DNS Hybrid** <br> • Tìm hiểu Private Hosted Zone và cơ chế phân giải DNS trong VPC. <br> • Thiết lập Outbound Endpoint để chuyển truy vấn DNS từ AWS về hệ thống nội bộ. <br> • Tạo Inbound Endpoint để nhận truy vấn từ on-premise. <br> • Tạo rule forward domain “corp.local” về DNS AD. <br> • Gán rule cho VPC và kiểm tra hoạt động của endpoint. | 23/10/2025 | 23/10/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | **Microsoft AD + DNS Integration – Mô phỏng on-premise** <br> • Khởi tạo Windows Server và cài Active Directory Domain Services. <br> • Thiết lập domain “corp.local” và DNS zone. <br> • Thêm Conditional Forwarder trỏ đến Inbound Endpoint. <br> • Tạo các bản ghi A và CNAME. <br> • Kiểm thử phân giải hai chiều: <br> – Từ AWS: `nslookup dc1.corp.local` <br> – Từ AD: `nslookup api.internal.aws` <br> • Giả lập lỗi endpoint và quan sát hành vi failover. | 24/10/2025 | 24/10/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 7 | **Dọn dẹp tài nguyên & Tối ưu chi phí** <br> • Xóa Log Group, Log Stream, Dashboard, Alarm không dùng. <br> • Tắt Container Insights để giảm chi phí. <br> • Gỡ Resolver Endpoint (tính phí theo giờ). <br> • Xóa toàn bộ Resolver Rules. <br> • Tắt domain controller. <br> • Xóa các EC2 thử nghiệm. <br> • Kiểm tra chi phí CloudWatch Logs, metrics và endpoint. | 25/10/2025 | 25/10/2025 | <https://cloudjourney.awsstudygroup.com/> |

---

### Kết quả đạt được trong tuần 7:

#### 1. AWS CloudWatch

**CloudWatch Metrics – Thu thập & phân tích**  
* Nắm danh sách metric mặc định của EC2, EBS, VPC và Load Balancer.  
* Tạo metric tùy chỉnh bằng AWS CLI để kiểm thử khả năng ghi dữ liệu.  
* Quan sát retention và độ phân giải dữ liệu từng giây.  
* Phân tích các dấu hiệu bất thường như CPU tăng đột biến, network spike, lượng DiskOps cao.

---

**CloudWatch Logs – Thu thập log ứng dụng**  
* Cài agent để gửi log ứng dụng và log hệ điều hành.  
* Tạo log group – stream phục vụ debugging.  
* Thiết lập retention và thử export sang S3 để lưu lâu dài.  
* Nhận diện các lỗi phổ biến: unauthorized request, throttling, CPU credit cạn.

---

**CloudWatch Alarms – Cảnh báo & phản hồi**  
* Tạo cảnh báo CPU vượt mức trong thời gian xác định.  
* Theo dõi EC2 system check để đảm bảo instance ổn định.  
* Tích hợp SNS gửi email khi có sự cố.  
* Kích hoạt auto-recovery để khắc phục lỗi phần cứng.

---

**CloudWatch Dashboards**  
* Xây dashboard theo dõi realtime.  
* Tổng hợp dữ liệu từ EC2, NAT Gateway, RDS, ELB.  
* Dùng nhiều kiểu widget để trực quan dữ liệu.

---

**Container Insights**  
* Kích hoạt theo dõi container trên ECS và Fargate.  
* Phân tích CPU/memory từng task.  
* Theo dõi số lần restart container để phát hiện lỗi.  
* Đánh giá cách Container Insights rút ngắn thời gian tìm lỗi.

---

**Dọn dẹp tài nguyên**  
* Xóa dashboard, alarm, custom metrics.  
* Gỡ agent và xóa log group không cần thiết.  
* Tắt Container Insights để giảm chi phí.

---

**Kết luận CloudWatch**  
* Hiểu trọn vẹn quy trình: thu thập → phân tích → cảnh báo → hiển thị.  
* Vận hành đầy đủ pipeline logs/metrics.  
* Cải thiện kỹ năng phân tích sự cố.  
* Tối ưu vận hành và chi phí hơn.  
* Tự xây dựng cơ chế cảnh báo realtime.

---

#### 2. Hybrid DNS với Route 53 Resolver

**Nắm kiến trúc DNS lai**  
* Hiểu các vấn đề khi doanh nghiệp dùng DNS nội bộ.  
* Biết chức năng của Inbound/Outbound Endpoint và Resolver Rules.

---

**Chuẩn bị môi trường**  
* Tạo VPC, subnet và security group cho endpoint.  
* Tạo Windows Server mô phỏng AD.  

---

**Kết nối RDGW**  
* Dùng RDGW để truy cập server trong private subnet.  
* Kiểm tra phân giải DNS nội bộ trước khi tích hợp.

---

**Triển khai Active Directory**  
* Tạo domain controller và DNS zone nội bộ.  
* Kiểm tra bản ghi SRV, A, NS.

---

**Thiết lập DNS Hybrid**

**Outbound Endpoint**  
* Cho phép AWS gửi truy vấn DNS về AD.  
* Forward domain nội bộ về DNS on-premise.  

**Inbound Endpoint**  
* Cho phép on-premise truy vấn bản ghi AWS.  
* Kiểm tra phân giải Private Hosted Zone.  

**Resolver Rules**  
* Tạo rule chuyển tiếp domain nội bộ.  
* Dùng system rule để kế thừa DNS mặc định VPC.

---

**Kiểm thử hệ thống**  
* Thực hiện phân giải hai chiều AD ↔ AWS.  
* Đánh giá độ ổn định và độ trễ.  
* Đảm bảo bản ghi phân giải chính xác.

---

**Dọn dẹp tài nguyên**  
* Xóa endpoint.  
* Xóa Private Hosted Zone và record test.  
* Tắt AD server và EC2 thử nghiệm.

---

**Kết luận DNS**  
* Hiểu rõ mô hình DNS hybrid.  
* Thiết lập hoàn thiện endpoint và rule.  
* Tích hợp DNS nội bộ với AWS thành công.  
* Phân giải hai chiều hoạt động ổn định.

---

### Tóm tắt kiến thức đạt được

**CloudWatch:**  
* Giám sát logs và metrics toàn diện.  
* Tự động hóa cảnh báo.  
* Xây dashboard trực quan.  
* Giám sát container hiệu quả.

**Route 53 Hybrid DNS:**  
* Hiểu cơ chế DNS trong môi trường lai.  
* Tích hợp DNS nội bộ và DNS AWS.  
* Thực hiện phân giải hai chiều.  
* Sẵn sàng áp dụng vào môi trường doanh nghiệp.
