---
title: "Chia sẻ, đóng góp ý kiến"
date: 2026-02-04
weight: 7
chapter: false
pre: " <b> 7. </b> "
---

> Những cảm nhận cá nhân về trải nghiệm tham gia chương trình First Cloud Journey, chia sẻ với mong muốn giúp team FCJ tiếp tục hoàn thiện chương trình.

### 1. Cảm nhận về chương trình

Điều làm FCJ khác biệt so với một khóa học thông thường nằm ở cấu trúc: năm tuần tự học có định hướng về nền tảng AWS, tiếp theo là bảy tuần áp dụng kiến thức đó vào một dự án thật trên tài khoản AWS thật — với hệ quả thật. Đọc về IAM least privilege là một chuyện; để tfsec chặn chính pipeline của mình cho đến khi thu hẹp policy lại là chuyện hoàn toàn khác. Tài liệu tự học (các khóa học và workshop được chọn lọc) rất chất lượng, và việc được tự chọn đề tài đồ án tốt nghiệp khiến chúng tôi thực sự đầu tư vào kết quả.

Chương trình còn âm thầm dạy những điều không tutorial nào đề cập: làm việc trong trần ngân sách hàng tháng, mở support case thật với AWS khi bị quota dịch vụ chặn, phối hợp hạ tầng dùng chung với đồng đội qua branch protection và pull request, và dọn dẹp tài khoản trước khi bàn giao. Những bài học "vận hành" này hóa ra lại là những bài học giá trị nhất.

### 2. Mức độ hài lòng

**Rất hài lòng — 9/10.** Kết thúc chương trình, tôi đã đi từ chỗ chỉ có kiến thức trên lớp đến việc tự thiết kế, xây dựng, bảo mật và vận hành một nền tảng serverless hoàn chỉnh có CI/CD và giám sát — thứ tôi có thể demo trực tiếp và trao đổi sâu trong các buổi phỏng vấn xin việc. Một điểm trừ phản ánh các góp ý bên dưới chứ không phải vấn đề cốt lõi nào của chương trình.

### 3. Điểm cần cải thiện

* **Một buổi review kiến trúc trước khi bắt tay xây dựng.** Thiết kế của chúng tôi chỉ được xem xét sau khi đã bắt đầu triển khai. Một buổi review ngắn với mentor về kiến trúc đề xuất vào cuối tuần thiết kế sẽ giúp phát hiện sớm các quyết định tốn kém hoặc thiếu thực tế.
* **Cảnh báo trước về giới hạn của tài khoản mới.** Chúng tôi mất thời gian kiểm thử thật vì quota on-demand của các mô hình Bedrock trên tài khoản AWS mới bằng không — điều chương trình có thể cảnh báo trước cho các nhóm (kèm hướng dẫn nộp yêu cầu tăng quota ngay từ tuần đầu).
* **Một buổi đánh giá giữa kỳ.** Một buổi check-in ngắn khoảng tuần 9 sẽ giúp các nhóm phát hiện lệch phạm vi và tiến độ khi vẫn còn thời gian điều chỉnh.
* **Tăng tương tác giữa các nhóm.** Phần lớn trao đổi của chúng tôi chỉ diễn ra trong nhóm hai người; một buổi định kỳ để các nhóm demo tiến độ cho nhau sẽ giúp lan tỏa bài học kinh nghiệm (và phát hiện các vấn đề chung như quota nhanh hơn).

### 4. Có giới thiệu chương trình cho bạn bè không? Vì sao?

**Có, không do dự** — kèm một lưu ý. Tôi sẽ giới thiệu chương trình cho bất kỳ người bạn nào muốn làm việc trong mảng cloud hoặc backend, vì đây là trải nghiệm gần nhất với môi trường làm việc chuyên nghiệp mà một sinh viên có thể có: tài khoản cloud thật, ngân sách thật, công cụ quét bảo mật thật đánh trượt build của chính mình, và một sản phẩm mình sở hữu trọn vẹn từ kiến trúc đến vận hành. Một dự án FCJ hoàn chỉnh là một sản phẩm trong portfolio, không chỉ là một chứng chỉ.

Lưu ý: chương trình đòi hỏi tính tự định hướng cao. Chương trình cung cấp lộ trình và sự hỗ trợ, nhưng không ai kèm cặp hàng ngày — một người bạn kỳ vọng trải nghiệm kiểu nghe giảng và được giao sẵn bài tập sẽ gặp khó khăn. Còn với ai sẵn sàng tự dẫn dắt dự án của mình, tôi nghĩ không có sự chuẩn bị nào tốt hơn.
