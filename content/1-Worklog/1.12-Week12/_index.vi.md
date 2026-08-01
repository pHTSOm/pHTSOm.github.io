---
title: "Worklog Tuần 12"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 1.12 </b> "
---

### Mục tiêu tuần 12:

Tuần cuối cùng: Thắt chặt bảo mật tài khoản AWS theo tiêu chuẩn CIS AWS Foundations Benchmark, load-test API bằng Locust, dọn dẹp các việc tồn đọng trong repo và hạ tầng, deploy frontend tĩnh lên S3 + CloudFront.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Bật AWS CloudTrail multi-region và AWS Config kèm conformance pack chuẩn CIS AWS Foundations Benchmark <br> - Sửa lỗi tích hợp CloudTrail → CloudWatch Logs bị fail do ARN của log group yêu cầu bắt buộc phải thêm hậu tố :*                                                                                             | 07/06/2026   | 07/06/2026      |  <https://docs.aws.amazon.com/config/latest/developerguide/operational-best-practices-for-cis_aws_benchmark_level_1.html> |
| 3   | - Chạy load test API bằng Locust với 50 concurrent users gửi request liên tục vào POST /summarize <br> - Điều tra lượng lớn response 429 trả về: do cơ chế throttle của API Gateway usage plan (2 req/s) chặn traffic đúng như thiết kế. Đã verify trên CloudWatch dashboard cho thấy backend vẫn hoạt động ổn định đằng sau lớp throttle                                            | 07/07/2026   | 07/07/2026      | <https://docs.locust.io/> |
| 4   | - Viết module Terraform cho frontend (S3 bucket + CloudFront distribution) và deploy static frontend <br> - Sửa lỗi nút login bị hỏng trên live site do Cognito vẫn redirect về localhost — đã thêm domain CloudFront vào danh sách Cognito callback URLs trong module auth của Terraform | 07/08/2026   | 07/08/2026      | <https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/> |
| 5   | - Dọn dẹp các file bị trót track nhầm vào Git (file .env, .DS_Store, các artifact __pycache__) <br> - Rút kinh nghiệm: file .gitignore không có tác dụng với các file đã được track — cần phải xóa khỏi index bằng lệnh git rm --cached trước                  | 07/09/2026   | 07/09/2026      |  |
| 6   | - Viết lại file README để phản ánh chính xác kiến trúc thực tế đã triển khai, loại bỏ các mô tả về những tính năng chưa từng được build                                                                                    | 07/10/2026   | 07/10/2026      | |


### Kết quả đạt được tuần 12:

* Triển khai dịch vụ CloudTrail đa vùng, AWS Config và gói đánh giá tuân thủ tiêu chuẩn CIS AWS Foundations Benchmark, đồng thời khắc phục sự cố tích hợp: vai trò CloudWatch Logs của CloudTrail yêu cầu cấu hình chính xác hậu tố :* trong ARN của nhóm nhật ký.
* Kiểm thử khả năng chịu tải của API bằng Locust với 50 người dùng đồng thời và đưa ra đánh giá chính xác: các phản hồi lỗi 429 xuất phát từ cơ chế giới hạn lưu lượng (throttle 2 yêu cầu/giây) của kế hoạch sử dụng nhằm bảo vệ hệ thống phía sau chứ không phải lỗi hệ thống — bảng điều khiển CloudWatch xác nhận không phát sinh lỗi 5XX hay sự cố Lambda. (Các phản hồi Bedrock được xử lý qua luồng dữ liệu giả lập do yêu cầu nâng hạn ngạch Bedrock theo yêu cầu vẫn đang đợi AWS Support phê duyệt.)
* Triển khai thành phần hạ tầng cuối cùng: phân hệ Terraform giao diện hosting trang web tĩnh trên S3 thông qua CloudFront, đồng thời khắc phục luồng đăng nhập thực tế bằng cách bổ sung tên miền CloudFront vào danh sách đường dẫn phản hồi của Cognito cùng với localhost.
* Loại bỏ các tệp tin chứa thông tin nhạy cảm và tệp tự động phát sinh khỏi kho mã nguồn (.env, .DS_Store, __pycache__), ghi nhận quy tắc .gitignore chỉ áp dụng cho tệp mới — các tệp đã được theo dõi cần sử dụng lệnh git rm --cached để loại bỏ.
* Cập nhật lại tệp README để tài liệu phản ánh chính xác trạng thái triển khai thực tế — loại bỏ các thông tin chưa được phát triển như caching hay rate limit — đồng thời chuẩn bị kịch bản trình diễn bao gồm: quy trình pipeline hoàn chỉnh, luồng xác thực toàn diện, các giao diện API summarize/history và bảng điều khiển chỉ số thời gian thực.
* Trạng thái hoàn thiện của nền tảng: khả năng khởi tạo hoàn toàn từ mã nguồn Terraform, tự động quét lỗ hổng bảo mật mỗi lượt push code, giám sát chủ động bằng bảng điều khiển và hệ thống cảnh báo, đáp ứng tiêu chuẩn bảo mật CIS, đã kiểm thử chịu tải và hoạt động chính thức trên CloudFront.