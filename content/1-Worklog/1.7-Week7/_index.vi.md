---
title: "Worklog Tuần 7"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.7. </b> "
---

### Mục tiêu tuần 7:

Thiết lập toàn bộ môi trường phát triển cho dự án: công cụ AWS CLI và Terraform, khởi tạo shared Git repository với các quy tắc bảo vệ nhánh (branch rules), đồng thời tiến hành nghiên cứu nền tảng trước khi viết mã nguồn Backend, bao gồm chi phí & giới hạn của Amazon Bedrock, mô hình kích hoạt (invocation model) của AWS Lambda và thiết kế khóa (key design) cho DynamoDB.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Cài đặt AWS CLI và Terraform. <br> - Sửa lỗi aws sts get-caller-identity trả về thông báo "unable to locate credentials". <br> - Đọc tài liệu AWS về nguyên tắc phân quyền tối thiểu.                                                                                             | 06/01/2026   | 06/01/2026      | <https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html> |
| 3   | - Khởi tạo shared repository và thiết lập Branch Protection Rules trên nhánh main. <br> - Thống nhất với đồng đội về quy chuẩn phân nhánh và định dạng commit message.                                            | 06/02/2026   | 06/02/2026      |  |
| 4   | - Đọc bảng giá Amazon Bedrock và tài liệu mô hình Nova Lite để nắm rõ giới hạn token, chi phí trên mỗi request và xác định dung lượng đầu vào thực tế phù hợp. | 06/03/2026   | 06/03/2026      | <https://docs.aws.amazon.com/bedrock/> |
| 5   | - Đọc tài liệu Lambda về cấu trúc hàm handler và cơ chế kích hoạt. Nghiên cứu định dạng Lambda Proxy Integration và chỉnh sửa handler để parse đúng dữ liệu từ `event['body']` thay vì đọc raw event.<br> - Thực hành kiểm thử các mẫu event payload trên AWS Lambda Console.                  | 06/04/2026   | 06/04/2026      | <https://docs.aws.amazon.com/apigateway/latest/developerguide/set-up-lambda-proxy-integrations.html> |
| 6   | - Nghiên cứu thiết kế Partition Key và Sort Key trong DynamoDB. Chốt cấu trúc dữ liệu NoSQL cho bảng tóm tắt văn bản.                                                                                         | 06/05/2026   | 06/05/2025      | <https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/best-practices.html> |


### Kết quả đạt được tuần 7:

* Cài đặt, cấu hình thành công AWS CLI và Terraform; xử lý triệt để lỗi xác thực aws sts get-caller-identity không tìm thấy credentials bằng cách thiết lập lại AWS profile chính xác. Nghiên cứu và áp dụng nguyên tắc phân quyền tối thiểu ngay từ đầu dự án.
* Khởi tạo shared repository, thiết lập Branch Protection trên main, đồng thời thống nhất quy chuẩn phân nhánh và định dạng commit message với đồng đội để tránh xung đột mã nguồn.
* Nắm vững mô hình tính phí của Amazon Bedrock và giới hạn token của Nova Lite, từ đó xác định dung lượng đầu vào tối đa hợp lý cho bài toán tóm tắt văn bản.
* Hiểu rõ cơ chế gói dữ liệu của Lambda Proxy Integration trong API Gateway  
  * Hàm handler phải parse đúng dữ liệu từ event['body'] thay vì xử lý trực tiếp raw event  
  * Kiểm chứng thành công qua các sample event trên Lambda Console.