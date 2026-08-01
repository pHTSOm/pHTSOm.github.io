---
title: "Worklog Tuần 9"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.9. </b> "
---

### Mục tiêu tuần 9:

Bổ sung cơ chế xác thực và một lớp API hoàn chỉnh phía trước AWS Lambda: khởi tạo Cognito User Pool kết hợp Hosted UI phục vụ tính năng đăng ký/đăng nhập, xây dựng API Gateway REST API để cung cấp các route /summarize và /history, tích hợp Cognito Authorizer nhằm bảo vệ cả hai phương thức, đồng thời cấu hình Usage Plan kết hợp CORS để ngăn chặn hành vi lạm dụng và cho phép kết nối từ phía Frontend.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Cấu hình Cognito User Pool để quản lý luồng đăng ký và đăng nhập của người dùng.                                                                                             | 11/08/2025   | 11/08/2025      |
| 3   | - Cấu hình thiết lập OAuth cùng trang đăng nhập Hosted <br> - Debug và xử lý triệt để lỗi redirect_mismatch do sai lệch giữa Callback URL đăng ký trên Cognito và địa chỉ thực tế của local server. UI.                                            | 06/16/2026   | 06/16/2026      | <https://docs.aws.amazon.com/cognito/latest/developerguide/cognito-user-pools-app-integration.html> |
| 4   | - Tạo API Gateway REST API và ánh xạ (map) các route /summarize cùng /history sử dụng cơ chế Lambda Proxy Integration. | 06/17/2026   | 06/17/2026      | <https://docs.aws.amazon.com/apigateway/latest/developerguide/> |
| 5   | - Tạo một Cognito Authorizer trong API Gateway và đính kèm vào cả hai HTTP method.                     | 06/18/2026   | 06/18/2026      | <https://docs.aws.amazon.com/apigateway/latest/developerguide/apigateway-integrate-with-cognito.html> |
| 6   | - Thiết lập Usage Plan đi kèm giới hạn truy cập (rate limit) và API Key để kiểm soát lưu lượng. <br> - Cấu hình CORS cho các method để mở quyền kết nối an toàn từ phía ứng dụng Frontend.                                                                                         | 06/19/2026   | 06/19/2026      | <https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-request-throttling.html> |


### Kết quả đạt được tuần 9:

* Thiết lập Cognito User Pool hỗ trợ luồng đăng ký và đăng nhập dựa trên email.
* Thiết lập OAuth và Hosted UI, đồng thời sửa triệt để lỗi redirect_mismatch sau khi đăng nhập bằng cách đồng bộ Callback URL đăng ký trên Cognito tương thích hoàn toàn với cấu trúc giao thức (scheme http/https) và địa chỉ thực tế của local dev server.
* Khởi tạo API Gateway REST API cung cấp hai tuyến endpoint /summarize và /history được kết nối trực tiếp với AWS Lambda qua cơ chế Lambda Proxy Integration.
* Đính kèm Cognito JWT Authorizer vào cả hai phương thức để bắt buộc mọi request phải mang theo token hợp lệ — từ đó Lambda trích xuất và định danh chính xác người dùng thông qua subject claim của Cognito.
* Bảo vệ API khỏi các hành vi lạm dụng bằng Usage Plan (giới hạn tần suất - rate limit + hạn ngạch hàng tháng - monthly quota) cùng API Key, đồng thời cấu hình CORS cho phép ứng dụng web trên trình duyệt truy cập API an toàn.
* Nắm vững toàn bộ chu trình xác thực: Đăng nhập qua Hosted UI → Phát hành JWT Token → Trình Authorizer của API Gateway xác thực Token → Lambda nhận diện danh tính người dùng.