---
title: "Các bài blogs đã nghiên cứu"
date: 2026-02-04
weight: 3
chapter: false
pre: " <b> 3. </b> "
---

Trong thời gian thực tập, nhóm chúng mình đã nghiên cứu ba bài viết từ các blog chính thức của AWS và viết lại những gì học được từ mỗi bài. Ba bài được chọn để gắn với các tầng khác nhau trong đồ án tốt nghiệp — infrastructure as code, xác thực, và chiến lược triển khai:

### [Blog 1 – How CloudFormation express mode accelerates your development cycle](3.1-blog1/)

Bài viết trên AWS DevOps Blog về Express mode của CloudFormation — chế độ báo "hoàn thành" ngay khi resource được cấu hình xong, trong khi quá trình ổn định hóa (stabilize) tiếp tục chạy ngầm phía sau. Khái niệm đắt giá nhất mình rút ra: "cấu hình xong" và "sẵn sàng phục vụ" là hai trạng thái khác nhau — điều liên quan trực tiếp tới các vòng deploy-test lặp đi lặp lại khi mình xây pipeline CI/CD cho đồ án bằng Terraform.

### [Blog 2 – How to monitor, optimize, and secure Amazon Cognito machine-to-machine authorization](3.2-blog2/)

Bài viết trên AWS Security Blog về OAuth 2.0 client credentials grant trong Cognito — cách các service tự xác thực với nhau mà không cần user đăng nhập, vì sao các request token M2M có chi phí riêng cần theo dõi, và cách tối ưu bằng token caching, API Gateway proxy, Secrets Manager và WAF. Một sự đối chiếu hữu ích với luồng Hosted UI + JWT authorizer mà đồ án của nhóm đang dùng cho người dùng thật.

### [Blog 3 – How CRED uses Amazon RDS Blue/Green Deployments at scale](3.3-blog3/)

Bài case study trên AWS Database Blog về cách công ty fintech CRED tự động hóa việc nâng cấp database trên hơn 120 cluster RDS/Aurora, rút cửa sổ bảo trì 3 tiếng xuống chỉ còn ~2 phút switchover. Bài học lớn nhất: thành công đến từ khâu chuẩn bị — staging giống hệt production, chuyển traffic từ từ, và quy trình rollback đã được diễn tập — chứ không phải từ bản thân lúc switchover.
