---
title: "Worklog Tuần 4"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.4. </b> "
---


### Mục tiêu tuần 4:

* Học cách triển khai và di chuyển các relational database được quản lý bằng dịch vụ RDS, đảm bảo tính sẵn sàng cao và khôi phục sau thảm hoạ thông qua cấu hình Multi-AZ và sao lưu tự động. 
* Tìm hiểu cách tối ưu hoá hiệu năng đọc bằng cách sử dụng Read Replicas đi kèm việc kiểm soát replication lag. 
* Nghiên cứu về kiến trúc cloud-native cùng các tính năng serverless của Amazon Aurora.
* Tìm hiểu về kiến thức liên quan đến quản lý khả năng mở rộng quy mô toàn cầu và tối ưu hoá connection pooling bằng Aurora Global Database và RDS Proxy
### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Biết về quy trình triển khai và di chuyển các cơ sở dữ liệu được quản lý                                                                                             |05/04/2026   | 05/04/2026      |  <https://learn.cantrill.io/p/aws-certified-solutions-architect-associate-saa-c03> <br> <https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_DMS_migration.html> |
| 3   | - Hiểu thế nào và cách đảm bảo tính lưu trữ dữ liệu an toàn và khả năng hoạt động liên tục 24/7 cho các ứng dụng quan trọng                                             | 05/05/2026   | 05/05/2026      | <https://learn.cantrill.io/p/aws-certified-solutions-architect-associate-saa-c03> <br> <https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Welcome.html> |
| 4   | - Xem các tài liệu liên quan đến mở rộng quy mô hiệu năng cơ sở dữ liệu cho các hệ thống có tải truy vấn đọc cao | 05/06/2026   | 05/06/2026      | <https://docs.aws.amazon.com/whitepapers/latest/best-practices-wordpress/reference-architecture.html>  <br>  <https://learn.cantrill.io/p/aws-certified-solutions-architect-associate-saa-c03> |
| 5   | Tìm hiểu về giải pháp cơ sở dữ liệu cloud-native hiệu năng cao                     | 05/07/2026   | 05/07/2026      | <https://learn.cantrill.io/p/aws-certified-solutions-architect-associate-saa-c03> |
| 6   | - xem cách quản lý quy mô truy cập dữ liệu trên phạm vi toàn cầu và tối ưu hoá connection pooling lưu lượng lớn                                                                                         | 05/08/2026   | 05/08/2026      | <https://learn.cantrill.io/p/aws-certified-solutions-architect-associate-saa-c03/> |


### Kết quả đạt được tuần 4:

* Xem về các dòng RDS instance class và các loại lưu trữ. Thực hành di chuyển cơ sở dữ liệu đang chạy trên EC2 sang RDS bằng AWS DMS
* Tìm hiểu về cơ chế synchronous replication và automatic failover. Thực hành quản lý automated backups và manual snapshots cho mục đích khôi phục dữ liệu dài hạn.
* Biết được là snapshot là các bản sao lưu immutable, giúp đảm bảo không bao giừo vô tình ghi đè lên dữ liệu hiện có trong quá trình khôi phục. Qua đó có thể thấy lý do việc restore từ snapshot luôn tạo ra một RDS instance hoàn toàn mới thay vì cập nhật instance cũ.
* Biết về cơ chế asynchronous replication cho phép mở rông lên đến 15 Read Replicas, giúp giảm tải các truy vấn đọc nặng cho primary writer instance 
* Học cách xử lý đữ liệu cũ/chưa cập nhật khi Read Replica chưa kịp đồng bộ từ primary, bằng cách định tuyến các thao tác ghi xong đọc ngay (write-then-read) trực tiếp vào primary instance.
* Tìm hiểu về giải pháp Amazon Aurora Serverless cho các ứng dụng có lưu lượng truy cập biến động bất thường và khó dự đoán.
* Tìm hiểu về Aurora Global Database để đạt độ trễ toàn cầu dưới 1 giây và RDS Proxy để quản lý hiệu quả hàng nghìn kết nối đồng thời từ ứng dụng