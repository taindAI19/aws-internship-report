---
title: "Worklog Tuần 12"
weight: 2
chapter: false
pre: " <b> 1.12 </b> "
---

### Mục tiêu trong tuần

**Phần 1 – Giới thiệu Amazon Bedrock & Foundation Models**

* Nắm được cách Amazon Bedrock được thiết kế và các thành phần vận hành chính.
* Tìm hiểu phương thức truy cập và sử dụng các foundation models thông qua Bedrock.
* Khảo sát các mô hình phổ biến như Claude, Llama, Mistral, Amazon Titan…
* Hiểu rõ sự khác nhau giữa mô hình sinh văn bản, mô hình embeddings và mô hình đa phương thức.

**Phần 2 – Xây dựng AI Agent với Bedrock Agent**

* Hiểu khái niệm AI Agent và cơ chế hoạt động của nó.
* Nắm được các thành phần:

  * Action groups  
  * Knowledge bases  
  * Orchestration  
  * Tích hợp Lambda functions  

* Thiết lập một AI Agent có khả năng gọi và sử dụng công cụ thông qua Lambda.

**Phần 3 – Sử dụng Knowledge Base cho Enterprise Search**

* Tạo một Knowledge Base bằng vector embeddings.
* Liên kết Bedrock KB với dữ liệu lưu trong S3.
* Kiểm thử khả năng tìm kiếm ngữ nghĩa và cơ chế RAG (Retrieval Augmented Generation).
* Hoàn tất tích hợp KB vào Bedrock Agent.

**Phần 4 – Tích hợp Front-end với Bedrock Agent**

* Xây dựng giao diện chat để tương tác trực tiếp với Agent.
* Thực hiện truyền dữ liệu dạng streaming để hiển thị phản hồi theo thời gian thực.
* Mô tả luồng xử lý: Người dùng nhập → Agent → (KB, Lambda) → Kết quả trả về.
* Đưa front-end lên môi trường Amplify Hosting.

---

### Các công việc triển khai trong tuần

| Thứ | Công việc chi tiết | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | ------------------- | ------------ | ---------------- | --------------- |
| 2 | **Tìm hiểu nền tảng Bedrock**<br>• Khám phá danh sách mô hình.<br>• Thử Claude / Llama 3 trong Playground.<br>• Đối chiếu chi phí và năng lực xử lý.<br>• Nắm API Bedrock cơ bản. | 24/11/2025 | 24/11/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | **Phát triển ứng dụng Text Generation đơn giản**<br>• Viết Lambda gọi InvokeModel API.<br>• Thử nghiệm temperature và max tokens.<br>• Tạo CLI nhỏ bằng SDK. | 25/11/2025 | 25/11/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | **Thiết lập Bedrock Agent**<br>• Cấu hình agent.<br>• Tạo hướng dẫn và guardrails.<br>• Tạo Action Group dùng Lambda.<br>• Kết nối agent với DynamoDB mẫu. | 26/11/2025 | 26/11/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | **Xây dựng hệ thống Knowledge Base (RAG)**<br>• Tạo bucket S3 chứa tài liệu.<br>• Thiết lập embeddings (Titan Embeddings G1).<br>• Kiểm thử Q&A với PDF/CSV.<br>• Tích hợp KB vào Agent. | 27/11/2025 | 27/11/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | **Kiểm thử toàn bộ Agent**<br>• Thử chuỗi hoạt động: Agent → KB → Lambda.<br>• Khắc phục lỗi IAM, KMS.<br>• Test nhiều lượt hội thoại.<br>• Bổ sung xử lý lỗi và fallback. | 28/11/2025 | 28/11/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 7 | **Phát triển giao diện Chat bằng Amplify**<br>• Tạo UI React Chat.<br>• Kết nối với Agent qua API Gateway.<br>• Thử streaming output.<br>• Triển khai bằng Amplify Hosting. | 29/11/2025 | 29/11/2025 | <https://cloudjourney.awsstudygroup.com/> |

---

### Kết quả đạt được trong tuần 12

**1. Kiến thức về Amazon Bedrock & Foundation Models**

* Biết cách gọi mô hình thông qua SDK Bedrock.
* Thực hành với nhiều nhóm mô hình khác nhau.
* Hiểu các tình huống ứng dụng: tạo văn bản, tóm tắt, sinh mã, embeddings.

---

**2. Hoàn thiện một AI Agent có khả năng chạy thực tế**

* Agent nhận diện được mục đích người dùng.
* Sử dụng Action Groups để kích hoạt Lambda.
* Hỗ trợ suy luận theo nhiều bước.
* Truy vấn DynamoDB thông qua Lambda.

---

**3. Xây dựng Knowledge Base phục vụ RAG**

* Tạo kho vector từ dữ liệu trong S3.
* Thực hiện tìm kiếm ngữ nghĩa thành công.
* Agent cải thiện chất lượng trả lời khi tích hợp KB.

---

**4. Tạo giao diện chat hoạt động với Bedrock**

* Xây dựng UI chat bằng React.
* Kết nối qua API Gateway để đảm bảo an toàn.
* Hoạt động tốt với phản hồi dạng streaming.
* Quy trình đầy đủ: UI → Agent → KB/Lambda → Phản hồi.

---

### Tóm tắt kiến thức đã học

**Amazon Bedrock**

* Cung cấp truy cập tới nhiều mô hình mạnh mẽ.
* Hệ thống được quản lý hoàn toàn và đạt chuẩn bảo mật doanh nghiệp.
* Hỗ trợ mô hình sinh văn bản, embeddings và đa phương thức.

**Bedrock Agents**

* Có khả năng duy trì hội thoại, xử lý logic và gọi công cụ.
* Action Groups cho phép kết nối backend thực tế.
* Guardrails giúp kiểm soát an toàn nội dung.

**Knowledge Bases**

* Embeddings nâng cao khả năng tìm kiếm ngữ nghĩa.
* Kết hợp KB và Agent tạo thành một hệ thống RAG hoàn chỉnh.
* Hỗ trợ tự động cập nhật tài liệu từ S3.

**Tích hợp & Triển khai**

* Lambda thực thi logic phía backend.
* API Gateway đảm bảo kết nối an toàn cho front-end.
* Amplify hỗ trợ triển khai giao diện nhanh chóng.

---