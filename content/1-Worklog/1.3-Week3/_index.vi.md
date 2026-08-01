---
title: "Worklog Tuần 3"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---

### Mục tiêu tuần 3:

Học từ việc thiết lập máy chủ cơ bản đến kiến thức về triển khai tự động hoá. Thực hiện quản lý an toàn các EC2 bằng sSM và thiết kế chuyển đổi kiến trúc máy chủ từ monolithic sang mô hình tách biệt giữa tầng ứng dụng và tầng cơ sở dữ liệu

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 5   | - Hiểu rõ cấu hình tự động của các máy chủ ảo nhằm đảm bảo tính nhất quán với cơ sở hạ tầng dưới dạng mã                                                                                              | 04/16/2026   | 16/04/2026      |
| 6   | - Học, biết về cách triển khai nguyên tắc đặc quyền tối thiểu cho các dịch vụ và quản lý tập trung secret của ứng dụng.   <br>                                            | 04/17/2026   | 04/17/2026      | <https://learn.cantrill.io/p/aws-certified-solutions-architect-associate-saa-c03> <br>  <https://docs.aws.amazon.com/systems-manager/latest/userguide/sysman-paramstore-versions.html> |
| 2   | - Triển khai system-level logging và giám sát hiệu năng hệ thống | 04/21/2026  | 04/21/2026      | <https://learn.cantrill.io/p/aws-certified-solutions-architect-associate-saa-c03/> |
| 3   | - Tối ưu hoá vị trí vật lý và logic của các server để nâng cao hiệu năng và độ tin cậy                 | 14/08/2025   | 15/08/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Hiểu được thế nào là chuyển đổi từ việc tự vận hành database trên server sang sử dụng AWS RDS                                                                                         | 04/22/2026   | 04/22/2026      | <https://aws.amazon.com/compare/the-difference-between-acid-and-base-database/> <br>  <https://learn.cantrill.io/p/aws-certified-solutions-architect-associate-saa-c03/> |


### Kết quả đạt được tuần 3:

* Nắm rõ cách lệnh cfn-signal hoạt động để thông báo cho Cloudformation stack biết phiên bản EC2 đã hoàn tất khởi tạo. Đồng thời, cfn-init giúp quản lý trạng thái và cập nhật dễ dàng hơn mà không cần phải thay thế toàn bộ EC2 instance: 
* Học cách các advanced parameters cho phép lưu trữ giá trị lớn hơn và đạt băng thôngn cao hơn, tuy nhiên việc này phát sinh chi phí.
* Hiểu cách sử dụng SSM Parameter Store để lưu trữ an toàn các dữ liệu nhạy cảm
* Tìm hiểu về Placement Group bao gồm Cluster, Spread và Partition. Ngoài ra, biết về việc kích hoạt ENA (Elastic Network Adapter) để duy trì băng thông mạng ổn định.
* Partition placement group mang lại sự cân bằng tốt nhất giữa khả năng cô lập lỗi và hiệu năng
* Tìm hiểu về tính nhất quán của dữ liệu qua các bài blog về ACID và BASE, học hỏi kiến thức liên quan đến quy trình tách rời kiến trúc cho Wordpress monolithic bằng cách chuyển cơ sở dữ liệu từ EC2 sang một phiên bản RDS chuyên dụng.