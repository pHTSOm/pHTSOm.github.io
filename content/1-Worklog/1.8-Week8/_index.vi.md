---
title: "Worklog Tuần 8"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.8. </b> "
---

### Mục tiêu tuần 8:

Xây dựng logic backend cốt lõi cho tính năng tóm tắt văn bản: gọi mô hình Amazon Nova Lite thông qua Amazon Bedrock, trích xuất kết quả tóm tắt từ phản hồi của mô hình, lưu trữ dữ liệu vào DynamoDB, tăng cường độ ổn định cho lời gọi Bedrock bằng cơ chế thử lại, đồng thời viết unit test bao phủ toàn bộ logic thao tác với cơ sở dữ liệu.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Viết hàm Python cơ bản sử dụng boto3.client('bedrock-runtime') để gọi mô hình Amazon Nova Lite. <br> - Debug các lỗi xác thực request body (validation errors) bằng cách in ra chính xác payload gửi đi và so sánh đối chiếu với tài liệu kỹ thuật của mô hình Nova.                                                                                             | 06/08/2026   | 06/08/2026      | <https://docs.aws.amazon.com/bedrock/latest/userguide/> |
| 3   | - Viết logic trích xuất đoạn văn bản tóm tắt ra khỏi đối tượng phản hồi của mô hình.                                             | 06/09/2026   | 06/09/2026      | <https://docs.aws.amazon.com/bedrock/latest/userguide/> |
| 4   | - Viết logic lưu trữ (persistence) vào DynamoDB để ghi văn bản đầu vào cùng bản tóm tắt do AI tạo ra vào bảng. | 06/10/2026   | 06/10/2026      | <https://boto3.amazonaws.com/v1/documentation/api/latest/guide/dynamodb.html> |
| 5   | - Thêm cơ chế tự động thử lại với thuật toán exponential backoff xung quanh việc gọi Bedrock để xử lý các lỗi tạm thời (transient errors / throttling).                  | 06/11/2026   | 06/11/2026      | |
| 6   | - Viết unit test cho logic thao tác cơ sở dữ liệu DynamoDB bằng bộ công cụ pytest và moto                                                                                         | 06/12/2026   | 06/12/2026      | <https://docs.getmoto.org/> |


### Kết quả đạt được tuần 8:

* Triển khai hàm tóm tắt cốt lõi gọi mô hình Amazon Nova Lite thông qua SDK boto3 client bedrock-runtime
* Debug các lỗi xác thực request (validation errors) của Bedrock bằng cách in ra chính xác payload gửi đi và đối chiếu từng trường với tài liệu kỹ thuật của mô hình Nova cho đến khi cấu trúc request body chuẩn xác và lời gọi API thành công.
* Viết logic trích xuất đoạn văn bản tóm tắt từ đối tượng phản hồi phân cấp do mô hình trả về.
* Triển khai luồng ghi dữ liệu vào DynamoDB, lưu trữ đầy đủ user_id, timestamp, văn bản gốc và bản tóm tắt do AI tạo ra.
* Nâng cao độ ổn định cho API dưới tải request liên tục bằng cách thêm cơ chế thử lại với thuật toán exponential backoff xung quanh việc gọi Bedrock để xử lý các lỗi tạm thời như nghẽn API (throttling) hoặc hết thời gian chờ (timeout).