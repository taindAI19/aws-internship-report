---
title: "Blog 2"
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---

# Tự động hóa xử lý dữ liệu với Amazon EMR: Điều phối bằng Step Functions & EventBridge

Khi các pipeline dữ liệu ngày càng mở rộng, nhu cầu **tự động hóa quy trình**, **giảm thao tác thủ công**, và **tối ưu chi phí compute** trở nên quan trọng hơn bao giờ hết. **Amazon EMR** cung cấp môi trường mạnh mẽ để chạy các workload như **Apache Spark**, ETL, batch analytics và data enrichment. Tuy nhiên, trong nhiều trường hợp – đặc biệt trong các ngành đòi hỏi kiểm soát hạ tầng chặt chẽ như tài chính, y tế, chính phủ – việc vận hành các cụm EMR tạm thời (transient clusters) nếu không tự động hóa sẽ gây tốn kém và rủi ro vận hành.

Trong blog này, tôi chia sẻ cách xây dựng **pipeline Spark hoàn toàn tự động** sử dụng **EMR on EC2**, được điều phối bởi **AWS Step Functions** và kích hoạt bởi **Amazon EventBridge**. Kiến trúc này minh họa cách chạy các job xử lý dữ liệu theo lịch, tối ưu chi phí và dễ quản trị.

---

## Hướng dẫn kiến trúc

Giải pháp sử dụng dataset COVID-19 public để mô phỏng pipeline xử lý dữ liệu định kỳ. Toàn bộ workflow được tách thành các thành phần độc lập, dễ thay thế, và dễ mở rộng.

Luồng xử lý dữ liệu gồm 7 bước chính:

1. Dữ liệu CSV được lưu trong S3 (raw input).  
2. EventBridge trigger theo lịch, kích hoạt state machine.  
3. Step Functions tạo cụm EMR tạm thời trên EC2.  
4. PySpark job được submit để tính toán các chỉ số COVID-19 theo bang.  
5. Kết quả được ghi vào output S3.  
6. Cụm EMR tự động xóa sau khi job hoàn thành.  
7. Toàn bộ log được lưu vào S3 để theo dõi & troubleshooting.

> Kiến trúc này đặc biệt phù hợp với các workload Spark theo batch, yêu cầu kiểm soát chi tiết hạ tầng nhưng vẫn muốn tối ưu chi phí.

---

## Đặc điểm kiến trúc tự động hóa

Khi làm việc với transient EMR clusters, ba yếu tố quan trọng được xem xét:

- **Nội tại**: hiệu năng cụm Spark, kiểm soát tài nguyên, tối ưu chi phí EC2  
- **Bên ngoài**: trigger theo lịch, điều phối nhiều job pipeline  
- **Con người**: giảm gánh nặng vận hành, hạn chế lỗi thủ công, audit rõ ràng  

Mô hình orchestration sử dụng Step Functions giúp theo dõi lifecycle rõ ràng – từ provisioning → spark submit → cleanup.

---

## Lựa chọn công nghệ và phạm vi giao tiếp

| Thành phần                          | Công nghệ sử dụng                                                                 |
| ---------------------------------- | --------------------------------------------------------------------------------- |
| Provision & teardown cluster       | AWS Step Functions, Amazon EC2, Amazon EMR                                        |
| Scheduling                         | Amazon EventBridge Scheduler                                                      |
| Data storage & logs               | Amazon S3                                                                          |
| Observability                      | Amazon CloudWatch, S3 logs, EMR Application UIs                                   |
| IaC (triển khai hạ tầng)           | AWS CloudFormation                                                                 |

---

## The orchestration pipeline

Mô hình kết nối các micro-components được xây dựng theo hướng **event-driven**:  
- EventBridge: kích hoạt workflow.  
- Step Functions: quản lý tuần tự các bước.  
- EMR: thực thi workload Spark.  
- S3: lưu input, output và log.  

Ưu điểm mô hình này:  
- Tách biệt compute (EMR) và logic điều phối (Step Functions)  
- Chỉ trả tiền compute khi cluster đang chạy  
- Quá trình xử lý minh bạch theo từng state  

Nhược điểm: cần quan sát chặt chẽ state machine & error handling.

---

## Core workflow components

### 1. Provisioning EMR cluster  
Step Functions khởi tạo cụm EMR on EC2 với cấu hình tối ưu cho workload. IAM roles được set theo nguyên tắc **least privilege**.

### 2. Spark job execution  
Job PySpark được upload lên S3, và Step Functions gửi step submit đến EMR cluster.

Khi chạy, script thực hiện:  
- Chuẩn hóa format dữ liệu  
- Loại bỏ bản ghi lỗi  
- Tính trung bình hàng tháng của:
  - giường nội trú  
  - giường ICU  
  - tỷ lệ bệnh nhân COVID-19  
- Xuất file CSV theo timestamp vào S3 output

### 3. Automated teardown  
Sau khi job hoàn thành, cluster được tự động xóa để tiết kiệm chi phí.  
Không còn lo chi phí EC2 phát sinh khi quên tắt cluster.

---

## Thiết lập & vận hành pipeline

### CloudFormation
Một template duy nhất triển khai toàn bộ hạ tầng:  
- EMR roles  
- S3 buckets  
- Log bucket  
- Step Functions state machine  
- EventBridge schedule  

Triển khai thường hoàn tất trong 5 phút.

### Tải và chuẩn bị dữ liệu
Dataset từ healthdata.gov được đổi tên và upload vào `raw/`.

### PySpark script
Script được upload vào thư mục `scripts/` trên S3 và sử dụng khi submit job.

---

## Scheduling với EventBridge

Workflow có thể chạy:  
- Một lần  
- Theo chu kỳ (cron hoặc rate-based)  
- Theo trigger nghiệp vụ

Điều này biến pipeline Spark thành một phần của hệ thống ETL định kỳ, ví dụ:  
- xử lý báo cáo cuối ngày  
- tổng hợp dữ liệu theo tuần  
- tính toán chỉ số y tế định kỳ

---

## Monitoring & observability

### Giám sát Step Functions  
- Theo dõi từng state  
- Bắt lỗi nhanh, xem input/output  
- Thao tác trực quan

### Giám sát EMR  
- Theo dõi step Spark  
- Xem chi tiết job qua Spark UI, YARN Timeline  
- Quan sát cluster-level metrics

### CloudWatch logs  
Nếu bật logging:  
- driver logs  
- executor logs  
- system metrics  

Đều được stream realtime.

> Quan sát đa lớp giúp rút ngắn thời gian troubleshooting, đặc biệt với workload Spark phức tạp.

---

## Kết quả xử lý & kiểm tra

Output file CSV được lưu vào thư mục  
s3://<output-bucket>/processed/<timestamp>/

Kết quả có thể dùng cho:  
- dashboard analytics  
- báo cáo tuân thủ  
- data enrichment downstream

---

## Dọn dẹp tài nguyên

Để tránh phát sinh chi phí:  
- Xóa S3 buckets (input/output/log)  
- Xóa CloudFormation stack  
- Kiểm tra lại EventBridge schedule để tránh trigger không mong muốn  

---

## Kết luận

Giải pháp sử dụng **Amazon EMR + Step Functions + EventBridge** cung cấp một cách tiếp cận **hoàn toàn tự động**, **tối ưu chi phí**, và **giàu tính quan sát** cho việc xử lý Spark on-demand.  

Đây là lựa chọn lý tưởng cho các doanh nghiệp muốn:  
- Tự động hóa pipeline ETL/batch analytics  
- Giảm chi phí compute bằng mô hình cluster tạm thời  
- Duy trì kiểm soát chi tiết về bảo mật và hạ tầng  
- Đảm bảo audit, logging, và scheduling theo chuẩn enterprise

Bạn có thể mở rộng giải pháp này bằng:  
- thêm nhiều Spark jobs  
- thêm workflow phức tạp hơn trong Step Functions  
- tích hợp partitioned output với Glue Data Catalog  
- kết hợp với Lake Formation để kiểm soát dữ liệu

---
