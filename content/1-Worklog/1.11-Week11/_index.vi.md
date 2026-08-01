---
title: "Worklog Tuần 11"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 1.11. </b> "
---

### Mục tiêu tuần 11:

Dựng pipeline CI/CD và bổ sung observability cho backend. Kết nối GitHub repo với AWS CodePipeline, viết file buildspec tự động hóa các bước (test, security scan, terraform plan), tích hợp custom latency metrics vào Lambda và dựng CloudWatch dashboard đi kèm cảnh báo qua SNS. Sau đó push một thay đổi thực tế chạy end-to-end qua pipeline và fix xong các lỗi do công cụ security scan phát hiện.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Tạo AWS CodePipeline và kết nối CodeStar tới GitHub repository <br> - Xử lý sự cố kết nối bị treo ở trạng thái "Pending" bằng cách xác thực kết nối GitHub thủ công trên AWS console                                                                                             | 06/29/2026   | 06/29/2026     | <https://docs.aws.amazon.com/codepipeline/latest/userguide/connections-github.html>  |
| 3   | - Viết file buildspec-test.yml để tự động chạy pytest, bandit, tfsec và terraform plan cho mỗi lần push code <br> - Sửa lỗi build fail do bản Terraform cài sẵn trên CodeBuild image bị lệch phiên bản — đã gỡ bản cũ và pin cố định (pin) chính xác phiên bản Terraform trong phase install                                            | 06/30/2026   | 06/30/2026      | <https://docs.aws.amazon.com/codebuild/latest/userguide/build-spec-ref.html> |
| 4   | - Tích hợp code đo đạc (instrument) độ trễ khi gọi Bedrock trong Lambda và đẩy thành custom CloudWatch metric (namespace Custom/Bedrock) <br> - Thêm quyền cloudwatch:PutMetricData vào IAM policy của Lambda trong module compute (Terraform) để cho phép đẩy metric | 07/01/2026   | 01/07/2026      | <https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/publishingMetrics.html> |
| 5   | - Dựng CloudWatch dashboard hiển thị thời gian thực thi (duration) của Lambda và các phân vị độ trễ (percentiles p50/p95/p99) của Bedrock <br>Tạo alarm cảnh báo lỗi liên kết với SNS email topic, giới hạn chỉ bắt các lỗi phía server (5XX) trong khung thời gian 5 phút liên tục để tránh báo động giả từ các test request lỗi 4XX phía client                  | 02/07/2026   | 02/07/2026      | <https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/CloudWatch_Dashboards.html> |
| 6   | - Push thay đổi thực tế chạy end-to-end xuyên suốt qua pipeline <br> - Xử lý các cảnh báo từ tfsec gây chặn stage security: giới hạn quyền IAM log về đúng log group cụ thể, bật mã hóa server-side và tính năng khôi phục theo thời điểm (PITR) cho DynamoDB, đồng thời thêm comment ignore inline kèm giải trình cho các trường hợp chấp nhận rủi ro                                                                                         | 03/07/2026   | 03/07/2026      | <https://aquasecurity.github.io/tfsec/> |


### Kết quả đạt được tuần 11:

* Dựng hoàn chỉnh pipeline CI/CD: GitHub push → CodeBuild test stage (pytest, bandit, tfsec, terraform plan) → manual approval → terraform apply.
* Rút kinh nghiệm: kết nối CodeStar với GitHub luôn ở trạng thái "Pending" cho đến khi được duyệt thủ công một lần trên console — IaC có thể khởi tạo tài nguyên nhưng bước bắt tay OAuth bắt buộc phải thao tác bằng tay.
* Fix lỗi môi trường CodeBuild bằng cách tự quản lý toolchain: buildspec giờ đây sẽ gỡ bản Terraform cài sẵn trên image và cài chính xác phiên bản được pin cố định, giúp quá trình build luôn nhất quán (reproducible).
* Tích hợp custom metrics đo độ trễ và tỷ lệ thành công/lỗi của Bedrock trong Lambda (namespace Custom/Bedrock), đồng thời nhận ra metric sẽ âm thầm không xuất hiện nếu execution role thiếu quyền cloudwatch:PutMetricData.
* Dựng CloudWatch dashboard theo dõi thời gian thực thi (duration) của Lambda, độ trễ Bedrock ở các mức phân vị p50/p95/p99, cùng các panel giám sát API Gateway và DynamoDB.
* Tối ưu hóa alarm để cảnh báo chuẩn xác: cảnh báo email qua SNS chỉ kích hoạt khi gặp lỗi phía server (5XX) kéo dài trong 5 phút liên tục, tránh báo động giả do các test request lỗi 4XX cố tình tạo ra khi test thủ công.
* Thấy rõ hiệu quả của security gate: tfsec đã chặn pipeline thành công cho đến khi thu hẹp phạm vi quyền IAM và bật mã hóa + PITR cho DynamoDB — đồng thời nắm được quy tắc comment ignore phải đặt ở cấp tài nguyên (resource level) mới có hiệu lực.