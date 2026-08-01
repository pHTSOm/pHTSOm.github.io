---
title: "Worklog Tuần 10"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 1.10. </b> "
---


### Mục tiêu tuần 10:

Chuyển toàn bộ hạ tầng sang IaC. Rebuild lại các phần đã config trên console thành các module Terraform (auth, API, compute, data) và setup remote state backend trên S3 với DynamoDB locking để team làm việc chung an toàn, tránh xung đột state.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Thiết kế cấu trúc dự án Terraform thành các module tái sử dụng: auth/, api/, compute/, data/                                                                                             | 06/22/2026   | 06/22/2026      | <https://developer.hashicorp.com/terraform/language/modules> |
| 3   | - Viết module auth (Cognito User Pool, app client, Hosted UI domain) và module api (REST API, routes, Cognito authorizer, usage plan)                                            | 06/23/2026   | 23/06/2026      | <https://registry.terraform.io/providers/hashicorp/aws/latest/docs> |
| 4   | - Viết module compute (package Lambda function, cài đặt biến môi trường, phân quyền IAM role theo nguyên tắc least-privilege) và module data (bảng DynamoDB) | 06/24/2026   | 06/24/2026      | <https://registry.terraform.io/providers/hashicorp/aws/latest/docs> |
| 5   | - Cấu hình remote state backend: tạo S3 bucket lưu file state và bảng DynamoDB cho cơ chế state locking                     | 06/25/2026   | 06/25/2026      | <https://developer.hashicorp.com/terraform/language/backend/s3> |
| 6   | - Chạy terraform plan / apply để đảm bảo toàn bộ hạ tầng có thể tái tạo hoàn toàn từ code <br> - Dọn dẹp repo                                                                                         | 06/26/2026   | 06/26/2026      |  |


### Kết quả đạt được tuần 10:

* Tái cấu trúc toàn bộ hạ tầng sang dạng Terraform module thay vì cấu hình thủ công trên console, tách thành các module auth/, api/, compute/, và data/.
* Code hóa toàn bộ tích hợp giữa Cognito + API Gateway trong Terraform, bao gồm authorizer, Lambda proxy integration, usage plan và API key.
* Viết IAM role cho Lambda trong module compute theo nguyên tắc least-privilege, chỉ cấp đúng các quyền (action) DynamoDB và Bedrock thực sự cần thiết.
* Thiết lập Terraform remote state trên S3 kết hợp bảng lock DynamoDB, giúp 2 người có thể làm việc chung trên cùng hạ tầng mà không bị xung đột hay lỗi file state.
* Kiểm thử tính tái tạo hoàn toàn của stack: terraform plan không còn chênh lệch (clean diff) và apply có thể dựng lại trọn vẹn môi trường chỉ từ mã nguồn.