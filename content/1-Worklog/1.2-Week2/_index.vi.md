---
title: "Worklog tuần 2"
date: 2026-02-04
weight: 1
chapter: false
pre: " <b> 1.2. </b> "
---




### Mục tiêu tuần 2:

* Học cách thiết kế kiến trúc có thể tự động hoá phục hồi sự cố thất bại và có thể tự động mở rộng/thu hẹp dựa trên nhu cầu sử dụng.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 5   | - Học về vai trò của Application Load Balancers (ALB) nhằm giúp giải quyết vấn đề phân phối lưu lượng truy cập ứng dụng đến các máy ảo khác nhau (EC2 instances) tại những Availability Zones khác nhau                                                                                                      | 04/09/2026 | 04/09/2026      | <https://learn.cantrill.io/p/tech-fundamentals>|
| 6   |  - Tìm hiểu về No-Ops và kiến trúc hướng sự kiện.                                              | 04/10/2026 | 04/10/2026      | <https://master.d31mm2rc5713dr.amplifyapp.com/#/course/week-1:-introduction-to-aws> <br> <https://learn.cantrill.io/p/tech-fundamentals> |
| 2   | - Học về sự khác biệt giữa lưu trữ dữ liệu quan hệ và phi quan hệ, và biết cách chọn loại cơ sở dữ liệu phù hợp cho những trường hợp khác nhau. | 04/13/2026 | 04/13/2026      | <https://learn.cantrill.io/p/aws-certified-solutions-architect-associate-saa-c03> |
| 3   |  - Học cách dùng Cloudfront và cách đọc những số liệu trên CloudWatch.                            | 04/14/2026 | 04/14/2026      | <https://master.d31mm2rc5713dr.amplifyapp.com/#/course/week-5:-security-services-on-aws> <br> <https://learn.cantrill.io/p/aws-certified-solutions-architect-associate-saa-c03> |
| 4   | - Học cách lưu trữ những thông tin quan trọng bằng AWS Secrets Manager.                                                                                     | 04/15/2026 | 04/15/2026      |  <https://learn.cantrill.io/p/aws-certified-solutions-architect-associate-saa-c03>  |


### Kết quả đạt được tuần 1:

* Học cách Applicationn Load Balancers (ALB) trong việc phân phối lưu lượng truy cập đến nhiều máy ảo khác nhau (EC2 instances) tại các điểm Availability Zoné khác nhau.

* Học cách Auto Scaling Group giúp việc thêm hoặc bớt EC2 dựa trên health checks hay chỉ số sử dụng CPU

* Tìm hiểu về tính năng hướng sự kiện của AWS Lambda, nơi mà code được chạy khi các phản hồi được kích hoạt mà không cần phải làm thủ công việc thêm bớt hay quản lý những máy chủ ảo.

* Được biết cách dịch vụ Amazon RDS mang lại tính sẵn sàng cao bằng việc triển khai Multi-AZ và cách Read Replica hỗ trợ khả năng mở rộng đối với tác vụ nặng về đọc thông tin.

* Học về khái niệm của cơ sở dữ liệu Key Value, tìm hiểu về partition key, sort eys, và biết được NoSQL được ưu tiên sử dụng cho mục đích để đạt tốc độ cao và khả năng mở rộng vô hạn của nó so với cơ sở dữ liệu truyền thống.

* Biết cách sử dụng Amazon Cloudfront cho việc caching tài nguyên động và tài nguyên tĩnh tại những điểm biên nhằm giảm độ trễ cho nhưng người dùng ở xa so với nơi đặt server

* Học cách sử dụng Amazon Cloudwatch để quan sát tình trạng hoạt động bằng cách thiết lập Alarms cho mức sử dụng CPU và tạo các bảng điều khiển để trực quan hoá hiệu suất hệ thống

* Biết về Envelope Encryption và cách quản lý các khoá mật mã để mã hoá dữ liệu lưu trữ trong S3 và RDS

* Học cách lưu trữ các thông tin quan trọng như thông tin xác thực cơ sở dữ liệu và API key bằng cách sử dụng AWS Secrets Manager