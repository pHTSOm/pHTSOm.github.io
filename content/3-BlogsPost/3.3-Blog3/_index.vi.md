---
title: "Blog 3 - RDS Blue/Green Deployments"
date: 2026-02-04
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---

# AWS Blog | How CRED uses Amazon RDS Blue/Green Deployments at scale – Vài điều mình học được khi mới bắt đầu tìm hiểu AWS

Xin chào mọi người,

Mình đang tập tìm hiểu về blue/green deployment cho database nên hôm trước có đọc bài "How CRED uses Amazon RDS Blue/Green Deployments at scale" trên AWS Blog. Bài này viết về CRED, một nền tảng fintech ở Ấn Độ, và cách họ tự động hóa việc upgrade database trên hơn 120 cluster RDS/Aurora. Đọc xong mình thấy hiểu thêm được khá nhiều thứ, xin chia sẻ lại, có gì hiểu sai mong mọi người góp ý ạ.

Ban đầu mình tưởng blue/green deployment chỉ đơn giản là có 2 bản database, chuyển qua chuyển lại là xong. Nhưng đọc kỹ thì mình mới thấy phần khó nhất không nằm ở lúc chuyển đổi, mà nằm ở khâu chuẩn bị trước đó.

### Mình hiểu vấn đề như thế nào

Theo bài viết thì trước đây mỗi lần CRED muốn upgrade version database hay đổi instance, họ phải lên kế hoạch bảo trì mất khoảng 3 tiếng, tốn nhiều công sức phối hợp và rủi ro downtime. Với hơn 120 cluster thì cách làm thủ công này không còn ổn nữa. Mình thấy con số này khá dễ hình dung: cứ tưởng tượng làm thủ công cho vài chục database thì mệt cỡ nào.

Blue/green deployment giải quyết việc này bằng cách tạo ra một bản sao (green) chạy song song với bản chính (blue), đồng bộ dữ liệu qua replication. Mọi thay đổi được làm trên green trước, xong mới "switchover", tức chuyển traffic từ blue sang green, mà theo bài viết thì bước này chỉ mất trung bình 2 phút.

### Điều mình thấy hay nhất là phần chuẩn bị

CRED nói rằng qua 200 lần migrate, 90% khả năng thành công là do chuẩn bị kỹ chứ không phải do lúc switchover. Vài điều họ làm trước khi switchover:

- Test kỹ trên staging giống hệt production, nếu test staging fail thì không được làm trên production (không có ngoại lệ)
- Cho các team ứng dụng biết endpoint của green sớm để họ test trước, và phải có sign-off mới được switchover
- Với major version upgrade thì chạy lại các query production trên cả 2 bản để so sánh kết quả
- Chuyển dần traffic đọc (read) sang green theo tỷ lệ 10% → 50% → 100% qua vài ngày trước khi chuyển hẳn


### Điều mình học được sau bài viết này

Bài viết có kể một tình huống là sau khi switchover 20 phút thì phát hiện lỗi, nhờ họ đã test sẵn quy trình rollback nên quay lại bản cũ chỉ trong 2.5 phút, không mất dữ liệu. Nếu không chuẩn bị rollback từ đầu thì chắc tình huống đó sẽ căng hơn nhiều.

Project của mình hiện tại dùng DynamoDB nên chưa đụng tới RDS/Aurora, nhưng đọc bài này giúp mình hiểu thêm về khái niệm blue/green ở tầng database, biết đâu sau này có dịp áp dụng.

### Lời kết

Cảm ơn mọi người đã đọc bài chia sẻ của mình, mình còn đang học nên có gì sai sót mong mọi người chỉ giáo thêm ạ

Link bài viết tham khảo: <https://aws.amazon.com/blogs/database/how-cred-uses-amazon-rds-blue-green-deployments-at-scale/>
