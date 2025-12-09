---
title: "Worklog Tuần 3"
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---

### Mục tiêu tuần 3:

* Nắm bắt khái niệm và mục đích sử dụng của **Amazon EC2 (Elastic Compute Cloud)**.  
* Làm quen với quy trình **khởi tạo, truy cập, cấu hình và quản lý các máy ảo EC2** trên môi trường Windows và Linux.  
* Tiến hành triển khai thử nghiệm một **ứng dụng web cơ bản (AWS User Management)** lên các EC2 instance.  
* Rèn luyện kỹ năng **giám sát, bảo mật và tối ưu tài nguyên EC2** trong suốt quá trình sử dụng.  

---

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | ---------- | ------------- | ---------------- | --------------- |
| 2 | - Tìm hiểu tổng quan về **Amazon EC2** cùng các thuật ngữ quan trọng: <br>&emsp; + Instance, AMI, Key Pair, Elastic IP, Security Group, Volume <br>&emsp; + Các mô hình chi phí: On-Demand, Spot, Reserved Instance, Savings Plan | 22/09/2025 | 22/09/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | - **Thực hành:** Khởi tạo và thiết lập **Windows EC2 instance** <br>&emsp; + Lựa chọn AMI và loại instance phù hợp <br>&emsp; + Tạo key pair, điều chỉnh security group <br>&emsp; + Kết nối qua Remote Desktop (RDP) <br>&emsp; + Khám phá giao diện Windows Server 2022 | 23/09/2025 | 23/09/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - **Thực hành:** Khởi tạo và thiết lập **Linux EC2 instance** <br>&emsp; + Tạo máy ảo Amazon Linux 2 <br>&emsp; + Đăng nhập bằng SSH với key pair <br>&emsp; + Làm quen terminal và lệnh căn bản <br>&emsp; + Cập nhật gói và hệ thống | 24/09/2025 | 24/09/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - **Triển khai ứng dụng “AWS User Management”** <br>&emsp; + Cài Node.js, npm và phụ thuộc cần thiết trên Windows & Linux <br>&emsp; + Triển khai ứng dụng CRUD quản lý người dùng <br>&emsp; + Kiểm thử các chức năng thêm, chỉnh sửa, xoá, tìm kiếm <br>&emsp; + Cho phép người khác truy cập ứng dụng thông qua Security Group | 25/09/2025 | 25/09/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - Tìm hiểu các công cụ theo dõi và quản lý EC2: <br>&emsp; + Amazon CloudWatch (theo dõi metric & log) <br>&emsp; + AWS Systems Manager <br>&emsp; + EC2 Instance Connect <br> - Thu gom và giải phóng tài nguyên: xoá instance, Elastic IP, Security Group không dùng | 26/09/2025 | 26/09/2025 | <https://cloudjourney.awsstudygroup.com/> |

---

### Kết quả đạt được trong tuần 3:

* Nắm rõ **những thành phần quan trọng của Amazon EC2**, bao gồm:  
  * **AMI:** Mẫu hệ điều hành và phần mềm để tạo instance.  
  * **Instance Type:** Quy định hiệu năng (CPU, RAM, lưu trữ).  
  * **Key Pair:** Công cụ xác thực đăng nhập an toàn.  
  * **Elastic IP:** Địa chỉ IP tĩnh để truy cập công khai.  
  * **Security Group:** Lớp bảo vệ kiểm soát luồng truy cập.  

* Tạo và cấu hình thành công **cả Windows và Linux EC2 instance**:  
  * Kết nối bằng **RDP (Windows)** và **SSH (Linux)**.  
  * Điều khiển instance qua **AWS Console và CLI**.  
  * Điều chỉnh **các luật mạng (ports 80, 443, 22, 3389)** để phục vụ ứng dụng web.  

* Hoàn tất triển khai ứng dụng **AWS User Management** trên hai hệ điều hành:  
  * Cài đặt các môi trường chạy như **Node.js** và **npm**.  
  * Vận hành đầy đủ chức năng CRUD.  
  * Cho phép người khác truy cập qua **Public IP hoặc Elastic IP**.  

* Áp dụng thành công các phương pháp **giám sát instance**:  
  * Sử dụng **CloudWatch** để theo dõi tài nguyên (CPU, RAM, network).  
  * Dùng **Systems Manager** để tự động hóa và quản lý phiên làm việc.  
  * Tận dụng **EC2 Instance Connect** để truy cập nhanh qua trình duyệt.  

* Nâng cao khả năng **quản lý chi phí và tài nguyên EC2**:  
  * Tắt hoặc xoá các instance không còn nhu cầu sử dụng.  
  * Thu hồi Elastic IP còn thừa.  
  * Dọn dẹp Security Group và Key Pair không cần thiết.  

---

### Tóm tắt kiến thức đạt được:

- **Amazon EC2:** Hiểu rõ cơ chế vận hành và cách triển khai máy chủ ảo trong môi trường cloud.  
- **Quản trị Windows & Linux:** Nắm được cách truy cập, cấu hình và bảo mật trên hai hệ điều hành.  
- **Triển khai ứng dụng:** Hoàn thiện triển khai ứng dụng Node.js CRUD trên EC2.  
- **Giám sát hệ thống:** Biết cách sử dụng CloudWatch & Systems Manager để theo dõi hiệu suất hoạt động.  
- **Tối ưu chi phí:** Có khả năng phân tích và dọn dẹp tài nguyên nhằm giảm chi phí vận hành.  

---
