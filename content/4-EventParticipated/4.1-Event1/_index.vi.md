---
title: "Event 1"
date: 2026-05-23
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---


# Bài thu hoạch “FCAJ Community Day – 23/05”

### Mục Đích Của Sự Kiện

- Chia sẻ kiến thức thực tế về AI, cloud và kỹ thuật thực chiến thông qua chuỗi các bài chia sẻ cộng đồng
- Cho thấy cách ngữ cảnh (context) và các công cụ AI hiện đại giúp AI thực sự hữu ích trong công việc hằng ngày
- Khám phá các khối xây dựng (building block) của AWS — từ Amazon CloudFront đến hệ thống multi-agent — qua kinh nghiệm của diễn giả
- Học hỏi từ hành trình hackathon của một nhóm sinh viên và kết nối cộng đồng những người xây dựng sản phẩm, người đi làm và sinh viên

### Danh Sách Diễn Giả & Các Phiên

- **Tinh Truong** – Platform Engineer, GotymeX — *Context Is Everything: Making AI Actually Work for You*
- **Anh Pham** – Cloud Consultant, G-AsiaPacific Vietnam — *Friendly AI Assistant with Amazon Quick*
- **Thinh Nguyen** – DevOps Engineer, FCAJ — *From Edge To Origin: CloudFront as Your Foundation*
- **Team VIB** (Thao Nguyen, Mai Nguyen, Uyen Le) — *36 hrs with LotusHacks – Building UTMorpho from Idea to Reality*
- **Duc Dao** – Solution Architect, Cloud Kinetics — *Non-Determinism of “Deterministic” LLM Settings*
- **Vy Lam** – Senior Business System Analyst — *Enterprise-Grade Multi-Agent System: The Case of Startup Credit Scoring*


### Nội Dung Nổi Bật

#### Context Is Everything: Making AI Actually Work for You — Tinh Truong
- Vì sao AI thất bại khi thiếu ngữ cảnh, và "context" thực sự có nghĩa là gì trong thực tế.
- Sự chuyển dịch từ các prompt rời rạc sang bộ nhớ (memory) — ý tưởng về một **"Second AI Brain"** lưu giữ ngữ cảnh theo thời gian.
- Ngữ cảnh tốt hơn dẫn tới kết quả tốt hơn như thế nào: tư duy thực tế và các mẹo áp dụng hằng ngày.
- Góc nhìn về nghề nghiệp và cách sinh viên có thể bắt đầu xây dựng sản phẩm với AI, kèm phần hỏi đáp (Q&A).

#### Friendly AI Assistant with Amazon Quick — Anh Pham
- **Quick Chat Agent**: trợ lý AI để khám phá dữ liệu và phân tích insight.
- **Quick Flows**: xây dựng các workflow thông minh bằng ngôn ngữ tự nhiên — không cần code.
- **Quick Spaces**: không gian cộng tác chung, biến insight cá nhân thành tri thức của cả team.
- **Quick Sight**: tạo dashboard và báo cáo từ dữ liệu thô bằng ngôn ngữ tự nhiên.

#### From Edge To Origin: CloudFront as Your Foundation — Thinh Nguyen
- Amazon CloudFront như một nền tảng cho mọi loại workload, không chỉ để phân phối nội dung tĩnh.
- **Tối ưu chi phí** với CloudFront.
- **Khả năng bảo mật** ngay tại edge.
- **Tăng độ tin cậy (reliability)** với CloudFront.
- **Tăng hiệu năng (performance)** cho người dùng nhờ ở gần edge hơn.

#### 36 hrs with LotusHacks – Building UTMorpho from Idea to Reality — Team VIB
- Lý do nhóm tham gia **LotusHacks** và điều gì đã thôi thúc họ.
- Từ con số 0 đến ý tưởng — hành trình brainstorming.
- Xác định bài toán và định hình sản phẩm **UTMorpho**.
- Xây dựng dưới áp lực — chặng sprint phát triển 36 giờ.
- Những thử thách, thất bại và các bước ngoặt trên đường đi.
- Tổng quan sản phẩm UTMorpho và phần demo trực tiếp.
- Các bài học rút ra và định hướng tiếp theo cho dự án.

#### Non-Determinism of “Deterministic” LLM Settings — Duc Dao
- Cách các LLM lựa chọn token tiếp theo.
- Giả định phổ biến rằng **Temperature = 0** đảm bảo kết quả mang tính tất định (deterministic).
- Thực tế: các tối ưu hóa ở khâu inference khiến cùng một input vẫn có thể tạo ra output khác nhau.
- Những ảnh hưởng thực tế của tính bất định này lên các ứng dụng thật.
- Các chiến lược giảm thiểu (mitigation) để kết quả có thể tái lập hơn.

#### Enterprise-Grade Multi-Agent System: The Case of Startup Credit Scoring — Vy Lam
- Sự lệch pha về cấu trúc giữa hệ thống ngân hàng truyền thống và dữ liệu của startup.
- Thiết kế single-agent: khi nào nên và khi nào không nên dùng.
- Mô hình multi-agent như một hướng thay thế.
- Bản thiết kế (blueprint) cho một **"hội đồng tín dụng ảo" (virtual credit committee).**
- Guardrails và tuân thủ (compliance) trong một lĩnh vực chịu nhiều quy định.
- ROI vận hành và lộ trình triển khai.


### Những Gì Học Được

- **Context là yếu tố tạo khác biệt thực sự cho AI.** Bộ nhớ và ngữ cảnh tốt hơn — chứ không chỉ là prompt khéo hơn — mới là thứ biến AI từ một thứ mới lạ thành công cụ đáng tin cậy hằng ngày.
- **Công cụ dùng ngôn ngữ tự nhiên giúp hạ thấp rào cản.** Các công cụ như Amazon Quick cho phép mọi người xây workflow, dashboard và tri thức chung mà không cần code nhiều.
- **CloudFront là nền tảng, không phải thứ nghĩ đến sau cùng.** Nếu dùng đúng cách, nó cải thiện chi phí, bảo mật, độ tin cậy và hiệu năng cho nhiều workload.
- **Xây dựng trong ràng buộc giúp học rất nhanh.** Câu chuyện LotusHacks/UTMorpho cho thấy một bài toán rõ ràng và thời hạn gấp rút buộc ta phải tập trung và lặp nhanh.
- **Cấu hình LLM "tất định" không hoàn toàn tất định.** Temperature = 0 không phải một sự đảm bảo; hệ thống production cần các chiến lược giảm thiểu để đảm bảo tính tái lập.
- **Hệ thống multi-agent phù hợp với các bài toán phức tạp, nhiều quy định.** Chia trách nhiệm cho nhiều agent — kèm guardrails và compliance — có thể phù hợp với những lĩnh vực mà một agent đơn lẻ không kham nổi.


### Trải nghiệm trong event

Tham gia **FCAJ Community Day** là một trải nghiệm bổ ích, gói gọn nhiều chủ đề rất khác nhau — từ nền tảng về ngữ cảnh trong AI đến hệ thống multi-agent cấp doanh nghiệp — chỉ trong một buổi sáng chia sẻ. Một số điều để lại ấn tượng với mình:

#### Học hỏi từ những người làm thực tế
- Các diễn giả đến từ nhiều nền tảng khác nhau — platform engineering, cloud consulting, DevOps, solution architecture và business analysis — nên mỗi bài chia sẻ mang một góc nhìn riêng về việc xây dựng với AWS và AI.
- Nghe hành trình hackathon thực tế từ **Team VIB** giúp các bài học trở nên cụ thể: một ý tưởng đã trở thành sản phẩm chạy được như thế nào trong 36 giờ.

#### Mở rộng góc nhìn kỹ thuật
- Các phiên chia sẻ kết nối những ý tưởng ở tầm cao (context, tính tất định, thiết kế multi-agent) với các khối xây dựng AWS thực tế như **Amazon CloudFront** và **Amazon Quick**.
- Bài của Đức là một lời nhắc hữu ích rằng ngay cả cấu hình LLM "tất định" cũng cần được xử lý cẩn thận trong hệ thống thật.

#### Cộng đồng và cảm hứng
- Buổi chia sẻ cho thấy một cộng đồng gồm người xây dựng sản phẩm, người đi làm và sinh viên có thể học được rất nhiều từ việc chia sẻ kinh nghiệm một cách cởi mở.
- Nhiều phiên đã cho mình những ý tưởng mới để thử nghiệm trong các dự án của mình, đặc biệt là việc bổ sung ngữ cảnh tốt hơn cho các workflow AI.


> Tổng thể, FCAJ Community Day mang lại cho mình một cái nhìn rộng và thực tế về hướng đi của AI và cloud, đồng thời để lại những ý tưởng cụ thể để áp dụng vào công việc của mình.
