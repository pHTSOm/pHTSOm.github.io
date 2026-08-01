---
title: "Event 2"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.2. </b> "
---


# Bài thu hoạch “Agent Forge Deep Dive Day 1”

### Mục Đích Của Sự Kiện

- Giới thiệu về Amazon Bedrock AgentCore
- Triển khai một agent cơ bản trên AgentCore
- Kết nối các công cụ (tools) bên ngoài và Knowledge Base
- Xây dựng Web UI và tích hợp xác thực bằng Amazon Cognito

### Danh Sách Diễn Giả

- **Nghia Tran** – Agentic SA
- **Anh Pham** – Cloud Consultant, G-AsiaPacific Vietnam


### Nội Dung Nổi Bật

#### Agentic AI là gì
- Các hệ thống phần mềm tự vận hành (một phần hoặc hoàn toàn), tận dụng AI để suy luận, lập kế hoạch và hoàn thành các tác vụ thay cho con người hoặc hệ thống.

#### Strands Agents
- Strands Agents là một SDK mã nguồn mở giúp xây dựng agent chỉ với vài dòng code.
- Dễ sử dụng: phát triển agent một cách trực quan, giúp bắt đầu trong vài phút thay vì vài giờ.
- Khả năng mở rộng: hỗ trợ custom model provider, custom tools và MCP.
- Phát triển nhanh: tạo prototype và lặp (iteration) nhanh chóng.

#### Amazon Bedrock AgentCore
- Nền tảng để xây dựng, kết nối và tối ưu agent — với bất kỳ framework nào, bất kỳ model nào.

- **Triển khai agent nhanh chóng**: xây dựng và triển khai agent mà không cần hàng tháng trời làm hạ tầng.
- **Kết nối tới mọi thứ**: cấp cho agent quyền truy cập an toàn tới các MCP server, API và knowledge base.
- **Tối ưu liên tục**: truy vết (trace) mọi quyết định của agent, đánh giá hiệu năng và kiểm thử các cải tiến một cách an toàn trên môi trường production.
- **AgentCore Runtime**: một môi trường runtime serverless bảo mật, được thiết kế chuyên biệt để triển khai và mở rộng (scale) các AI agent và tool động (ví dụ MCP server), bất kể lựa chọn framework, protocol hay model nào.
- **Xác định model AI phù hợp cho agent**: để chọn đúng model cho đúng tác vụ, cần đọc kỹ tài liệu.
- **Chi phí (Pricing)**: AgentCore chạy theo mô hình serverless, giúp tiết kiệm chi phí.

#### Amazon Bedrock AgentCore Identity

- Quản lý xác thực chiều vào (inbound) và chiều ra (outbound) trực tiếp từ AgentCore.
- **Workload Identities**: tấm "thẻ nhân viên" của agent; phát hành các Workload Access Token (WAT) có thời hạn ngắn.
- **Credential Providers**: lưu cách xác thực tới một dịch vụ — API key, hoặc OAuth client_id + secret.
- **Token Vault**: kho lưu trữ được mã hóa (Secrets Manager + KMS); cache token theo từng người dùng.
- **Broker Logic**: thực hiện OAuth ở phía server — M2M, 3LO, OBO — và trả về token hoàn chỉnh.

#### Amazon Bedrock AgentCore Gateway

- **Làm thế nào để scale?**: tạo một gateway đóng vai trò middleware, giúp quản lý kết nối giữa agent với các API/tool/tài nguyên.
- **Truy cập an toàn**: AgentCore Gateway có thể lưu log vào Amazon CloudWatch.
- **So sánh sync vs async**: hiểu rõ các đánh đổi (trade-offs).
- **AgentCore Semantic Search**: AgentCore Gateway tự động lập chỉ mục (index) các tool và cung cấp tính năng semantic search serverless. Nó giảm lượng ngữ cảnh (context) truyền vào LLM của agent, cải thiện độ chính xác, tốc độ và chi phí, đồng thời giúp agent tập trung vào các tool liên quan tới một tác vụ cụ thể. Tên của search tool là x-amz-bedrock-agentcore-search.



### Trải nghiệm trong event

Tham gia workshop **“Agent Forge Deep Dive Day 1”** là một trải nghiệm rất bổ ích, mang lại cho tôi cái nhìn toàn diện về cách xây dựng và vận hành AI agent bằng các phương pháp và công cụ hiện đại. Một số trải nghiệm nổi bật:


#### Trải nghiệm kỹ thuật thực tế
- Tìm hiểu các kiến thức nền tảng về **Amazon Bedrock AgentCore** và các thành phần của nó — **Runtime, Gateway, Identity** — để hiểu rõ dịch vụ được sử dụng xuyên suốt workshop.
- Tham gia các phiên **hands-on workshop** giúp tôi xây dựng một web app chạy local và tự tạo AI agent của riêng mình với Kiro.


#### Ứng dụng công cụ hiện đại
- Trực tiếp tìm hiểu về **Amazon Bedrock AgentCore**, một nền tảng agentic để xây dựng, triển khai và vận hành các agent hiệu quả cao, an toàn và ở quy mô lớn, với bất kỳ framework và foundation model nào.


#### Một số hình ảnh khi tham gia sự kiện
![Định nghĩa tổng quan về một Agent](/images/4-Event/aws_event_agentcore_1.jpg)

![Thang mức độ tự vận hành (a gradient of autonomy)](/images/4-Event/aws_event_agentcore_2.jpg)

> Tổng thể, workshop hands-on mang tính tương tác cao của sự kiện đã giúp tôi có thêm nhiều kiến thức kỹ thuật mới, đồng thời khơi gợi những ý tưởng mới cho các dự án cá nhân trong tương lai.
