---
title: "Worklog Tuần 1"
date: 2026-02-04
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### Mục tiêu tuần 1:

* Học về kiến thức nền tảng thuộc mạng máy tính (OSI model, IP addressing/CIDR, NAT variations).
* Hiểu về cơ sở hạ tầng vật lý và logic của AWS.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 5   | - Học hiểu lý thuyết về truyền dữ liệu và địa chỉ hoá dữ liệu                                                                                                   | 04/02/2026 | 04/02/2026      | <https://master.d31mm2rc5713dr.amplifyapp.com/#/course/week-1:-introduction-to-aws> <br> <https://learn.cantrill.io/p/tech-fundamentals>|
| 6   |  - Tìm hiểu cách thức hoạt động của định tuyến lưu lượng truy cập và cơ sở hạ tầng vật lý của AWS.                                              | 04/03/2026 | 04/03/2026      | <https://master.d31mm2rc5713dr.amplifyapp.com/#/course/week-1:-introduction-to-aws> <br> <https://learn.cantrill.io/p/tech-fundamentals> |
| 2   | - Học cách sử dụng những dịch vụ đã học liên quan đến môi trường điện toán đám mây | 04/06/2026 | 04/06/2026      | <https://learn.cantrill.io/p/aws-certified-solutions-architect-associate-saa-c03> |
| 3   |  - Sử dụng hệ thống quản lý danh tính và quyền truy cập tập trung để bảo vệ môi trường đám mây.                            | 04/07/2026 | 04/07/2026      | <https://master.d31mm2rc5713dr.amplifyapp.com/#/course/week-5:-security-services-on-aws> <br> <https://learn.cantrill.io/p/aws-certified-solutions-architect-associate-saa-c03> |
| 4   | - Tìm hiểu cách tự động cấp phát dịch vụ AWS.                                                                                     | 04/08/2026 | 04/08/2026      |  <https://learn.cantrill.io/p/aws-certified-solutions-architect-associate-saa-c03>  |


### Kết quả đạt được tuần 1:

* Ôn lại OSI models:
  * Lớp Vật lý
  * Lớp Liên kết dữ liệu
  * Lớp Mạng
  * Lớp Vận Chuyển
  * Lớp Phiên
  * Lớp Trình Bày
  * Lớp Ứng Dụng

* Đã nghiên cứu không gian địa chỉ IP và biết cách tính toán mạng con (subnet) sử dụng ký pháp CIDR để xác định ranh giới mạng và miền quảng bá (broadcast domain)

* Học về Network Address Translation (NAT) bằng cách phân tích cách private IP giao tiếp với internet công cộng thông qua NAT

* Học về sự khác biệt giữa
  * Static NAT
  * Dynamic NAT
  * PAT (Port Address Translation)

* Tìm hiểu các nguyên tắc cơ bản của:
  * Virtual Private Cloud   
  * Elastic Compute Cloud   
  * Simple Storage Service

* Biết cách vận dụng IAM để tạo:
  * Users
  * Groups
  * Roles

* Thực hành viết JSON policies để thiết lập "Nguyên tắc đặc quyền tối thiểu" cho việc truy cập tài nguyên

* Đã tìm hiểu khái niệm về Tài khoản AWS (AWS Account) với vai trò là ranh giới bảo mật và thanh toán chính, cũng như cách nó cô lập các tài nguyên khỏi các môi trường khác

* Tìm hiểu khái niệm Cơ sở hạ tầng dưới dạng mã (Infrastructure as Code) với CloudFormation

* Học cách liên kết nhiều tài khoản AWS vào một Tổ chức (Organization) duy nhất, sử dụng các đơn vị tổ chức (Organizational Units - OUs) để phân nhóm theo logic

* Tìm hiểu về Service Control Policies (SCP) và phân tích cách áp dụng các rào chắn quản trị (administrative guardrails) trong toàn bộ tổ chức