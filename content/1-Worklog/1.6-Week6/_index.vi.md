---
title: "Worklog Tuần 6"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---


### Mục tiêu tuần 6:

Tuần này trọng tâm là công tác chuẩn bị trước khi phát triển hệ thống: hoàn thiện đề xuất đồ án, thiết kế kiến trúc serverless, lựa chọn các dịch vụ AWS phù hợp với ngân sách sinh viên, và thống nhất phân công công việc với đồng đội.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Soạn thảo và chốt đề xuất dự áncho nền tảng Tóm tắt Tài liệu                                                                                              | 05/25/2026   | 05/25/2026      |
| 3   | - Thiết kế kiến trúc serverless <br>&emsp; + Cognito <br>&emsp; + API Gateway <br>&emsp; + Lambda <br>&emsp; + DynamoDB <br>&emsp; + Amazon Bedrock <br> <br> - Hoàn tất vẽ sở đồ tổng quan hệ thống.                                            | 05/26/2026   | 05/26/2026      | <https://docs.aws.amazon.com/serverless/> |
| 4   | - So sánh các mô hình AI trên Amazon Bedrock dựa trên khả năng xử lý và chi phí <br> - Đã chọn Amazon Nova Lite làm mô hình chính cho tác vụ tóm tắt văn bản | 05/27/2026   | 05/27/2026      | <https://docs.aws.amazon.com/bedrock/> |
| 5   | - Thống nhất phân chia nhiệm vụ với đồng đội (phát triển backend và hạ tầng AWS với frontend và tính năng báo cáo hàng tuần của dự án)                  | 05/28/2026   | 05/28/2026      |  |
| 6   | - Chia dự án thành các giai đoạn và xây dựng danh mục công việc chi tiết                                                                                         | 05/29/2026   | 05/29/2026      |  |


### Kết quả đạt được tuần 6:
* Quyết định phát triển hệ thống backend cho ứng dụng tóm tắt tài liệu bằng AI trên hạ tầng AWS
* Sử dụng Cognito cho xác thực người dùng, API Gateway làm điểm truy cập tập trung, AWS Lambda để xử lý logic, DynamoDB làm cơ sở dữ liệu lưu trữ và Amazon Bedrock cho tác vụ tóm tắt bằng AI.
* So sánh các lựa chọn mô hình trên Amazon Bedrock và quyết định chọn Amazon Nova Lite vì đây là giải pháp tối ưu nhất giữa hiệu năng và chi phí cho một dự án với ngân sách sinh viên.
* Học cách đánh giá các dịch vụ AWS dưới góc độ chi phí trước. Ưu tiên chọn DynamoDB on-demand và các thành phần serverless để kiểm soát chi phí hàng tháng trong mức ngân sách cho phép.
* Hoàn thành phân chia công việc với đồng đội: quyết định thực hiện backend, tích hợp Bedrock và hạ tầng AWS.
* Xây dựng danh mục công việc triển khai theo từng giai đoạn làm định hướng cho các tuần phát triển tiếp theo.