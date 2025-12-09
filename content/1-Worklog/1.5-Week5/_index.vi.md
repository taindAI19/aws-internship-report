---
title: "Worklog Tuần 5"
weight: 1
chapter: false
pre: " <b> 1.5. </b> "
---

### Mục tiêu tuần 5:

* Nắm vững cơ chế hoạt động của **Amazon S3**, hiểu cấu trúc lưu trữ dạng object, các tùy chọn lưu trữ và phạm vi áp dụng trong thực tế.  
* Triển khai **static website** trên S3: bật tính năng hosting, tinh chỉnh quyền truy cập và thử nghiệm tốc độ hoạt động.  
* Thành thạo các thiết lập **bảo mật cho bucket**, bao gồm chặn truy cập công khai, viết chính sách IAM và cấu hình Bucket Policy một cách an toàn.  
* Làm quen với các thao tác nâng cao: **Versioning**, **Transfer Acceleration**, **Replication sang vùng khác**, cùng các lệnh di chuyển object.  
* Thực hiện quy trình **giải phóng tài nguyên** đúng chuẩn để tránh phát sinh chi phí không mong muốn và tuân thủ best practice khi sử dụng S3.

---

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | ---------- | ------------- | ---------------- | --------------- |
| 2 | **Ôn tập nền tảng & chuẩn bị môi trường** <br>&emsp; + Giải thích khái niệm bucket, object, region, key và các phân lớp lưu trữ (STANDARD, IA, GLACIER) <br>&emsp; + Tìm hiểu mức độ bền (11-nines) và khả năng sẵn sàng <br>&emsp; + Tổng hợp bài toán phù hợp cho S3: website tĩnh, sao lưu, phân tích dữ liệu | 06/10/2025 | 06/10/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | **Khởi tạo bucket & bật hosting website** <br>&emsp; + Tạo bucket theo đúng quy tắc đặt tên và chọn region <br>&emsp; + Upload `index.html`, `error.html` <br>&emsp; + Kích hoạt chế độ Static Website Hosting và truy cập endpoint để test | 07/10/2025 | 07/10/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | **Thiết lập Public Access & cấu hình Bucket Policy** <br>&emsp; + Nắm rõ các chế độ Block Public Access ở cấp tài khoản và bucket <br>&emsp; + Viết Bucket Policy để chỉ cho phép public một object cụ thể (index.html) <br>&emsp; + Kiểm tra truy cập website qua trình duyệt <br>&emsp; + Thử thu hồi public access và kiểm tra lại hành vi bảo mật | 08/10/2025 | 08/10/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | **Nâng tốc độ & mở rộng khả năng hosting** <br>&emsp; + So sánh ưu điểm — hạn chế giữa: S3 + CloudFront, S3 Transfer Acceleration, AWS Amplify Hosting <br>&emsp; + Bật Transfer Acceleration và benchmark tốc độ bằng `curl` ở nhiều vị trí <br>&emsp; + (Tùy chọn) Tạo CloudFront để bật HTTPS/CDN <br>&emsp; + Thêm giám sát CloudWatch và đánh giá chi phí sử dụng | 09/10/2025 | 09/10/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | **Quản lý vòng đời, replication & dọn dẹp tài nguyên** <br>&emsp; + Bật Versioning để kiểm soát thay đổi object và thử phục hồi file cũ <br>&emsp; + Cài đặt Lifecycle chuyển sang IA/Glacier sau một số ngày nhất định <br>&emsp; + Thiết lập Cross-Region Replication với IAM Role tương ứng <br>&emsp; + Dùng cp/mv/sync để chuyển dữ liệu giữa bucket/region <br>&emsp; + Xóa tài nguyên thử nghiệm: disable acceleration, remove CloudFront, empty bucket, xóa bucket | 10/10/2025 | 10/10/2025 | <https://cloudjourney.awsstudygroup.com/> |

---

### Kết quả đạt được trong tuần 5:

**1. Thiết lập & vận hành cơ bản:**
- Hoàn chỉnh cấu hình AWS CLI (Access Key, Secret Key, Region).  
- Kiểm tra trạng thái CLI bằng:  
  - `aws configure list`  
  - `aws s3 ls` (liệt kê bucket)  
  - `aws s3api list-buckets` (xem chi tiết)  
- Tạo/xóa bucket bằng lệnh:  
  - `aws s3 mb s3://ten-bucket`  
  - `aws s3 rb s3://ten-bucket --force`

**2. Static Website Hosting:**
- Tạo bucket mới, đưa file HTML vào và bật hosting.  
- Xem website chạy qua endpoint được cung cấp.  
- Kiểm tra trang lỗi khi truy cập file không tồn tại để đảm bảo error.html hoạt động đúng.

**3. Quản lý quyền & bảo mật:**
- Thử bật/tắt Block Public Access để quan sát sự khác biệt.  
- Viết chính sách bucket chỉ công khai một file duy nhất.  
- Test quyền truy cập bằng cách public/private từng object.

**4. Quản lý dữ liệu & tăng tốc hiệu năng:**
- Bật versioning và thử upload nhiều phiên bản của cùng một file.  
- Khôi phục file từ version cũ để hiểu cơ chế.  
- Áp dụng lifecycle rules để tự động chuyển object sang IA hoặc Glacier.  
- Thử tốc độ Transfer Acceleration bằng curl từ nhiều region.

**5. Replication & di chuyển dữ liệu:**
- Thiết lập CRR và quan sát object được sao chép sang region khác.  
- Sử dụng các lệnh:  
  - `aws s3 cp`  
  - `aws s3 mv`  
  - `aws s3 sync`  
- Kiểm tra bucket đích để xác minh replication thành công.

**6. Dọn dẹp & tối ưu chi phí sử dụng:**
- Xóa object test, vô hiệu hóa Transfer Acceleration và CloudFront.  
- Xóa bucket thử nghiệm, tắt hosting.  
- Tổng hợp best practices giúp kiểm soát chi phí và đảm bảo an toàn dữ liệu.

---

### Ghi chú:

- Luôn tránh public toàn bộ bucket — chỉ public object thật sự cần thiết.  
- Block Public Access là lớp an toàn quan trọng, chỉ nên override nếu hiểu rõ quyền và rủi ro.  
- Versioning kết hợp Lifecycle giúp quản lý dữ liệu lâu dài mà vẫn tiết kiệm chi phí.  
- CloudFront phù hợp khi cần HTTPS, domain riêng và hiệu năng toàn cầu; Transfer Acceleration thích hợp khi client thường upload từ xa.  
- Amplify Hosting là lựa chọn đơn giản khi chỉ cần triển khai website tĩnh từ repo Git.  
- IAM phải được cấu hình chặt chẽ, không lưu Access Key trong mã nguồn.  
- CloudWatch + S3 Storage Lens hỗ trợ theo dõi dung lượng, traffic và chi phí.  
- Khi xóa bucket có Versioning, cần xóa tất cả version + delete marker, tránh bị tính phí lưu trữ không mong muốn.

---

### Tóm tắt kiến thức đạt được:

- Vận hành S3 ở mức đầy đủ: hosting, bảo mật, replication, versioning và tối ưu cost.  
- Biết chọn giải pháp triển khai static site phù hợp: S3 đơn thuần, S3 + CloudFront, hoặc Amplify.  
- Sử dụng hiệu quả các công cụ quản lý dữ liệu lớn: lifecycle, policy, replication, sync/copy.  
- Nắm kỹ quy trình dọn dẹp tài nguyên để tránh phát sinh chi phí.

---
