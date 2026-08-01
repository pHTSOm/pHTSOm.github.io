---
title: "Tự đánh giá"
date: 2026-02-04
weight: 6
chapter: false
pre: " <b> 6. </b> "
---

Trong thời gian thực tập với chương trình **First Cloud Journey (FCJ)** từ **tháng 4/2026** đến **tháng 7/2026**, mình đã có cơ hội đi từ kiến thức trên lớp đến việc xây dựng và vận hành một hệ thống cloud thực tế. Sau năm tuần học nền tảng AWS có lộ trình, mình dành bảy tuần xây dựng đồ án tốt nghiệp, nền tảng tóm tắt văn bản serverless ứng dụng AI, trong đó mình phụ trách backend, tích hợp Amazon Bedrock và toàn bộ hạ tầng: Terraform, pipeline CI/CD, giám sát và củng cố bảo mật.

Để nhìn nhận khách quan về quá trình thực tập, mình tự đánh giá theo các tiêu chí sau:

| STT | Tiêu chí | Xếp loại | Nhận xét |
| --- | --- | --- | --- |
| 1 | **Kiến thức** | Khá | Bắt đầu với kiến thức chủ yếu là lý thuyết, kết thúc với khả năng thiết kế và vận hành một stack serverless hoàn chỉnh (Lambda, API Gateway, Cognito, DynamoDB, Bedrock, Terraform). Vẫn còn khoảng trống: một số phát hiện theo chuẩn CIS trên tài khoản chưa được xử lý triệt để, và nhiều dịch vụ mình mới dùng lần đầu trong dự án này. |
| 2 | **Khả năng học hỏi** | Tốt | Tiếp thu lượng kiến thức mới lớn trong thời gian ngắn: năm tuần học nền tảng, sau đó áp dụng khoảng mười dịch vụ AWS mới vào thực tế. mình học chủ yếu từ tài liệu chính thức và từ chính các lỗi gặp phải: debug payload request của Bedrock, các phát hiện của tfsec, và lỗi môi trường CodeBuild bằng cách đối chiếu với tài liệu. |
| 3 | **Tính chủ động** | Tốt | Khi quota on-demand của Bedrock trên tài khoản mới chặn việc gọi mô hình thật, mình tự mở support case với AWS và, thay vì ngồi chờ kết quả, xây dựng đường mock cho chức năng tóm tắt để việc phát triển, kiểm thử và demo không bao giờ bị gián đoạn. Support case cuối cùng bị từ chối (do giới hạn về điều kiện của tài khoản mới, không phải lỗi cấu hình), điều này càng cho thấy quyết định tự gỡ vướng cho mình là đúng đắn. Mình cũng chủ động làm vượt phạm vi tối thiểu với CI/CD, metric tùy chỉnh, dashboard và tuân thủ CIS. |
| 4 | **Kỷ luật** | Khá | Duy trì giờ làm việc ổn định, tuân thủ quy trình branch protection/PR của nhóm, không bao giờ đẩy thay đổi chưa review lên main. Tuy nhiên, mình đã chậm trễ trong việc ghi worklog theo thời gian thực và phải bổ sung dồn vào giai đoạn cuối, điểm cần khắc phục ở các dự án sau. |
| 5 | **Giao tiếp** | Khá | Trao đổi thường xuyên với đồng đội về các tài nguyên dùng chung (Cognito callback URL, CORS, state) nên hai bên không bao giờ vô tình làm hỏng phần việc của nhau. Kỹ năng thuyết trình vẫn là điểm yếu: việc cô đọng bảy tuần làm hạ tầng thành một bản demo năm phút rõ ràng khiến mình phải thử nhiều lần. |
| 6 | **Teamwork** | Tốt | Cách phân chia hai người (backend/hạ tầng và frontend/báo cáo/kiểm thử tải) có ranh giới sở hữu rõ ràng, tích hợp qua PR trên nhánh main được bảo vệ. Các lần bàn giao, như kết nối frontend hoàn thiện với API thật, diễn ra suôn sẻ. |
| 7 | **Giải quyết vấn đề** | Tốt | Giải quyết vấn đề một cách có hệ thống thay vì thử-sai: in chính xác payload gửi đi để đối chiếu tài liệu, truy ra lỗi CloudTrail do thiếu hậu tố `:*` trong ARN, nhận định đúng các lỗi 429 khi kiểm thử tải là usage plan hoạt động đúng thiết kế, và dùng `git rm --cached` để dọn các file bị track nhầm. |
| 8 | **Đóng góp cho dự án** | Tốt | Phụ trách và hoàn thành phần lớn nền tảng: backend tóm tắt, tích hợp Bedrock, toàn bộ tám module Terraform, pipeline CI/CD với các cổng bảo mật, giám sát/cảnh báo và củng cố bảo mật theo CIS, tất cả trong trần ngân sách 50 USD/tháng. |

### Điểm cần cải thiện

* Cập nhật tài liệu và worklog **ngay khi làm việc**, thay vì tái dựng lại sau đó.
* Đào sâu kiến thức bảo mật: một số phát hiện CIS (ví dụ IAM role của pipeline còn quá rộng) đã được chấp nhận tạm hoãn có chủ đích; lần sau mình muốn xử lý triệt để thay vì chấp nhận.
* Ước lượng thời gian thực tế hơn: việc debug hạ tầng (pipeline, quota, IAM) luôn tốn nhiều thời gian hơn dự kiến.
