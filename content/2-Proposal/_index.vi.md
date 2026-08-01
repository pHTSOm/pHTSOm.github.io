---
title: "Bản đề xuất"
date: 2026-02-04
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# Nền tảng Tóm tắt Văn bản Serverless Tự động trên AWS

### 1. Tổng quan dự án

Đồ án tốt nghiệp này xây dựng một nền tảng tóm tắt văn bản hoàn toàn serverless, đạt chuẩn production trên AWS, do nhóm hai thành viên phát triển. Người dùng sau khi xác thực có thể gửi một đoạn văn bản qua REST API (hoặc qua trang web đơn giản) và nhận về bản tóm tắt do AI tạo ra thông qua Amazon Bedrock. Mỗi lần tóm tắt được lưu theo từng người dùng, có thể xem lại qua endpoint lịch sử, và được tổng hợp tự động thành báo cáo CSV hàng tuần theo lịch định sẵn.

Ngoài bản thân ứng dụng, mục đích cốt lõi của dự án là thực hành quy trình kỹ thuật cloud hiện đại từ đầu đến cuối: toàn bộ hạ tầng được định nghĩa bằng code với Terraform, triển khai qua pipeline CI/CD tự động có quét bảo mật, giám sát bằng dashboard và cảnh báo, và được củng cố theo chuẩn CIS AWS Foundations Benchmark — tất cả trong giới hạn ngân sách sinh viên.

**Phân chia công việc:** một thành viên phụ trách backend, tích hợp Bedrock và toàn bộ hạ tầng/CI-CD; thành viên còn lại phụ trách giao diện frontend, logic báo cáo hàng tuần và kiểm thử tải.

### 2. Mục tiêu

* **Serverless compute** — AWS Lambda (Python) gọi Amazon Bedrock (mô hình Amazon Nova Lite) để tóm tắt văn bản. Xử lý đồng bộ, đầu vào tối đa 5.000 ký tự.
* **Xác thực** — Amazon Cognito với OAuth 2.0 (trang đăng nhập Hosted UI, JWT token) bảo vệ mọi route của API.
* **Quản lý API** — Amazon API Gateway (REST) với Cognito authorizer, API key và usage plan giới hạn tốc độ request cùng hạn mức theo tháng.
* **Lưu trữ dữ liệu** — Amazon DynamoDB thiết kế single-table (partition key `user_id`, sort key `timestamp`) kèm GSI phục vụ truy vấn báo cáo theo ngày.
* **Báo cáo định kỳ** — Amazon EventBridge cron kích hoạt Lambda báo cáo hàng tuần, ghi file CSV thống kê theo người dùng vào S3 với lifecycle chuyển sang Glacier.
* **CI/CD** — AWS CodePipeline + CodeBuild: unit test bằng pytest, quét bảo mật bằng bandit và tfsec, `terraform plan`, phê duyệt thủ công, rồi `terraform apply`.
* **Infrastructure as Code** — Terraform dạng module (auth, api, compute, data, scheduling, frontend, monitoring, pipeline) với remote state trên S3 và khóa state bằng DynamoDB.
* **Giám sát** — Dashboard CloudWatch (thời gian chạy Lambda và độ trễ Bedrock ở mức p50/p95/p99, lỗi API, mức sử dụng DynamoDB) kèm cảnh báo qua email SNS.
* **Bảo mật & tuân thủ** — IAM đặc quyền tối thiểu, CloudTrail đa vùng, AWS Config với conformance pack chuẩn CIS AWS Foundations Benchmark.
* **Frontend demo** — trang tĩnh HTML/JS trên S3 phía sau CloudFront, đăng nhập qua Cognito Hosted UI và gọi API bằng JWT.

### 3. Vấn đề cần giải quyết

Triển khai ứng dụng AI theo cách thủ công rất mong manh: cấu hình bằng tay trên console gây ra sai lệch môi trường, phụ thuộc không được ghi lại, và hệ thống không thể tái tạo hay kiểm tra được. Việc gọi các API AI tạo sinh trong môi trường production còn đặt ra những vấn đề mà một script đơn giản bỏ qua — xác thực và định danh từng người dùng, chống lạm dụng và giới hạn tốc độ, lỗi tạm thời và giới hạn quota của mô hình, kiểm soát chi phí, và khả năng audit.

Dự án giải quyết các vấn đề đó bằng một kiến trúc serverless hoàn toàn tái tạo được: mọi tài nguyên đều là Terraform có quản lý phiên bản, mọi lần triển khai đều qua kiểm thử tự động và quét bảo mật, mọi request đều được xác thực và giới hạn tốc độ, và đường gọi AI được phòng thủ kỹ (retry với exponential backoff, trả lỗi nhanh khi hết quota). Với một nhóm sinh viên, dự án còn trả lời một câu hỏi thực tế: liệu có thể vận hành một backend GenAI đạt chuẩn production với ngân sách chỉ vài chục đô mỗi tháng?

### 4. Kiến trúc giải pháp

Luồng request: người dùng đăng nhập qua Cognito Hosted UI và được chuyển hướng về kèm JWT. Frontend gọi `POST /summarize` hoặc `GET /history` trên API Gateway kèm token; Cognito authorizer xác thực token và usage plan áp giới hạn tốc độ trước khi Lambda chạy. Lambda tóm tắt gọi Amazon Nova Lite trên Bedrock, lưu văn bản gốc và bản tóm tắt vào DynamoDB theo định danh người dùng, rồi trả kết quả về. Hàng tuần, EventBridge kích hoạt Lambda thứ hai tổng hợp hoạt động tuần trước từ DynamoDB thành báo cáo CSV trên S3.

**Các tầng kiến trúc:**

| Tầng | Dịch vụ |
|---|---|
| Người dùng / Edge | Trang tĩnh HTML/JS trên S3 + CloudFront (HTTPS) |
| API | API Gateway REST API, Cognito authorizer, usage plan + API key, CORS |
| Compute | Hai hàm Lambda (Python): tóm tắt đồng bộ, báo cáo hàng tuần theo lịch |
| AI | Amazon Bedrock — Amazon Nova Lite |
| Dữ liệu | DynamoDB (single table + GSI), S3 bucket báo cáo (AES-256, lifecycle Glacier) |
| Lập lịch | EventBridge cron rule hàng tuần |
| DevOps | CodePipeline + CodeBuild (pytest, bandit, tfsec, plan/approve/apply), Terraform remote state (S3 + khóa DynamoDB) |
| Bảo mật & Giám sát | CloudTrail (đa vùng), AWS Config + CIS conformance pack, dashboard + cảnh báo CloudWatch, SNS |

Region chính: `ap-southeast-1` (Singapore).

### 5. Timeline

Kỳ thực tập 12 tuần, tháng 4 – tháng 7/2026:

| Tuần | Giai đoạn |
|---|---|
| 1–5 | Học nền tảng AWS: networking, IAM, compute, storage, DNS, container |
| 6 | Khởi động dự án: đề xuất, thiết kế kiến trúc, chọn mô hình, phân chia công việc |
| 7 | Chuẩn bị môi trường: AWS CLI, Terraform, repository chung, nghiên cứu dịch vụ |
| 8 | Backend lõi: tích hợp Bedrock, parse kết quả, lưu DynamoDB, retry, unit test |
| 9 | Tầng xác thực & API: Cognito User Pool + Hosted UI, route API Gateway, authorizer, usage plan, CORS |
| 10 | Infrastructure as Code: Terraform dạng module, remote state có khóa |
| 11 | Pipeline CI/CD + giám sát: CodePipeline, buildspec tự động, metric tùy chỉnh, dashboard, cảnh báo |
| 12 | Củng cố & bàn giao: chuẩn CIS, kiểm thử tải, triển khai frontend lên CloudFront, dọn dẹp, tài liệu |

### 6. Ngân sách

Trần cứng: **50 USD/tháng** cho toàn bộ dịch vụ AWS. Các quyết định thiết kế đều xuất phát từ giới hạn này: DynamoDB on-demand thay vì provisioned, không dùng NAT gateway hay VPC endpoint, Lambda cấu hình bộ nhớ nhỏ nhất khả dụng, và chủ động bỏ qua response caching của API Gateway (cache cluster nhỏ nhất đã tốn ~14–19 USD/tháng).

Ước tính chi phí hàng tháng ở mức lưu lượng dự kiến (vài nghìn request):

| Hạng mục | Ước tính/tháng |
|---|---|
| Lambda (cả hai hàm) | ~0 USD (free tier) |
| DynamoDB on-demand + PITR | < 1 USD |
| API Gateway REST | < 1 USD |
| Bedrock — token Nova Lite | ~1 USD |
| S3 + CloudFront (trang tĩnh + báo cáo) | < 1 USD |
| CodePipeline + phút build CodeBuild | ~2 USD |
| CloudTrail (trail đầu tiên) + AWS Config | ~3–5 USD |
| Cảnh báo/metric CloudWatch, SNS | ~1 USD |
| **Tổng** | **≈ 8–12 USD/tháng** — thấp hơn nhiều so với trần 50 USD |

### 7. Rủi ro

| Rủi ro | Mức ảnh hưởng | Xác suất | Biện pháp giảm thiểu |
|---|---|---|---|
| Giới hạn quyền truy cập mô hình / quota on-demand của Bedrock trên tài khoản AWS mới | Cao | Trung bình | Xin tăng quota sớm qua AWS Support; duy trì đường mock cho chức năng tóm tắt để việc phát triển, kiểm thử và demo không bao giờ bị chặn bởi quota |
| Vượt ngân sách sinh viên | Trung bình | Trung bình | Ưu tiên free tier, billing on-demand, cảnh báo ngân sách, tránh tài nguyên chạy liên tục; đối chiếu mọi thay đổi với trần 50 USD |
| Hai người làm hỏng hạ tầng chung (xung đột state, cấu hình Cognito/CORS) | Trung bình | Trung bình | Terraform remote state có khóa DynamoDB, branch protection kèm review PR, trao đổi trước khi thay đổi tài nguyên dùng chung |
| Cấu hình bảo mật sai (IAM quá rộng, bucket public) | Cao | Thấp | Cổng chặn tfsec + bandit trong pipeline, IAM đặc quyền tối thiểu, CIS conformance pack, audit bằng CloudTrail |
| Mô hình không khả dụng tại region chính | Trung bình | Thấp | Dùng cross-region inference profile; giữ model ID cấu hình được qua biến môi trường |

