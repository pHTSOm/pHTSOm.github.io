---
title: "Worklog Tuần 5"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.5. </b> "
---

### Mục tiêu tuần 5:

* Tìm hiểu về cách quản lý DNS toàn cầu với Amazon Route 53, bao gồm Hosted Zones, DNSSEC và các chính sách định tuyến lưu lượng thông minh(như Weighted và Failover Routing) nhằm đảm bảo hiệu năng cũng như tính sẵn sàng cao cho hệ thống.
* Tìm hiểu về cách tối ưu hoá trải nghiệm người dùng trển toàn cầu thông qua chiến lược định tuyến theo độ trễ, vị trí địa lý và khoảng cách địa lý.
* Chuyển đổi mô hình triển khai từ máy ảo sang ứng dụng đóng gói container bằng cách sử dụng Docker và đẩy các container image lên Amazon ECR
* Thực hành điều phối container với Amazon ECS và mô hình serverless AWS Fargate.
### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Tìm hiểu Global Entry Point                                                                                             | 05/11/2026   | 11/11/2026      |
| 3   | - Tìm hiểu về cách hệ thống mạng toàn cầu giúp điều hướng người dùng dựa trên hiệu năng và trạng thái hoạt động của ứng dụng                                            | 05/12/2026   | 05/12/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Tìm hiểu về định tuyến dựa trên độ trễ và vị trí địa lý để tối ưu hoá trải nghiệm truy cập | 05/13/2026   | 05/13/2026      | <https://learn.cantrill.io/p/aws-certified-solutions-architect-associate-saa-c03/> |
| 5   | - Thực hành tạo Docker image và push lên Amazon ECR để lưu trữ an toàn trên đám mây                  | 14/08/2026   | 15/08/2026      | <https://learn.cantrill.io/p/aws-certified-solutions-architect-associate-saa-c03/> |
| 6   | - Xem cách điều phối các container ở quy mô lớn với AWS Fargate mà không cần quản lý hạ tầng máy chủ bên dưới                                                                                         | 05/15/2026   | 05/15/2026      | <https://learn.cantrill.io/p/aws-certified-solutions-architect-associate-saa-c03/> |


### Kết quả đạt được tuần 5:

* Xem về Public / Private Hosted Zones và lý do bản ghi Alias tối ưu hơn về mặt kỹ thuật so với bản ghi CNAME trong hệ sinh thái AWS.
* Học cách sử dụng DNSSEC để thêm chữ ký số vào các bản ghi tên miền, giúp ngăn chặn các cuộc tấn công giả mạo DNS.
* Xem cách cập nhật Name Server tại các web đăng ký tên miền bên thứ ba(như GoDaddy, Namecheap) trỏ về AWS Hosted Zone, cho phép Route 53 điều hướng lưu lượng cho tên miền mua ở trang cung cấp khác.
* Thực hành cấu hình định tuyến theo tỷ lệ phần trăm và thiết lập cơ chế chuyển vùng tự động dựa trên kiểm tra sức khoẻ hệ thống cho mục đích khôi phục sau thảm hoạ.
* Học cách điều hướng người dùng dựa theo latency routing hoặc theo vị trí quốc gia thực tế của họ.
* Hiểu rằng Dockerfile đóng vai trò như mã nguồn cho môi trường thực thi, đảm bảo tính tái tạo và khả năng quản lý phiên bản. Do đó Dockerfile là bắt buộc ngay cả khi có thể commit/capture trực tiếp từ một container đang chạy.
* Tìm hiểu các khái niệm cốt lõi của Amazon ECS và các mô hình triển khai cluster.
* Thực hành cách triển khai với Fargate launch type, giúp thực thi các container theo mô hình không máy chủ (serverless) mà không cần quản lý hay bảo trì các cluster EC2.