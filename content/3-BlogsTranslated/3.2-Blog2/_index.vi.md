---
title: "Blog 2 - Cognito M2M Authorization"
date: 2026-02-04
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---

# AWS Security Blog | How to monitor, optimize, and secure Amazon Cognito machine-to-machine authorization – Vài điều mình học được khi mới bắt đầu tìm hiểu AWS

Xin chào mọi người,

Mình đang tìm hiểu thêm về Cognito nên hôm trước có đọc bài "How to monitor, optimize, and secure Amazon Cognito machine-to-machine authorization" trên AWS Security Blog. Bài này nói về việc theo dõi, tối ưu chi phí và bảo mật cho luồng xác thực machine-to-machine (M2M) trên Cognito. Đọc xong mình thấy hiểu thêm được một luồng authorization khác với cái mình đang dùng, xin chia sẻ lại, có gì hiểu sai mong mọi người góp ý ạ.

Ban đầu mình tưởng M2M chỉ là một biến thể nhỏ của việc user đăng nhập bình thường. Nhưng đọc kỹ thì mình mới biết đây là một luồng khác hẳn: không có user nào đăng nhập cả, mà là hai hệ thống/service tự "xác thực" với nhau bằng client ID và client secret, gọi là OAuth 2.0 client credentials grant.

### Mình hiểu luồng hoạt động như thế nào

Theo bài viết thì luồng M2M có 6 bước: app client gửi request kèm client ID/secret tới endpoint `/oauth2/token` của Cognito, Cognito trả về access token, app client dùng token đó gọi tới resource server, resource server lấy JSON Web Key Set (JWKS) từ Cognito để verify chữ ký token, sau đó mới trả resource về. Mình thấy hay ở chỗ toàn bộ quá trình này diễn ra ở phía server, không có giao diện đăng nhập nào cả — đúng nghĩa "máy nói chuyện với máy".

### Vấn đề mà bài viết nhắc tới: chi phí và việc theo dõi

Điều làm mình bất ngờ là Cognito tính phí riêng cho M2M app client và số lượng token request, nên nếu không theo dõi kỹ thì chi phí có thể tăng khá nhanh. Bài viết có cho xem biểu đồ chi phí thực tế theo ngày và theo từng account, có ngày lên tới hơn 24 đô chỉ riêng cho việc issue token — mình nhìn con số đó mới hiểu vì sao cần theo dõi sát.

### Cách tối ưu và bảo mật mà bài viết đề xuất

Vài điểm mình thấy dễ hiểu và nhớ được:

- Client nên tự cache access token, dùng lại cho tới khi hết hạn, để đỡ phải xin token liên tục
- Nếu client không tự cache được, có thể dùng API Gateway làm proxy phía trước endpoint `/oauth2/token` của Cognito và bật caching ở đó — giảm số request thật tới Cognito
- Nên dùng AWS Secrets Manager để giữ client ID/secret, không hardcode vào code
- Dùng AWS WAF để bảo vệ endpoint, kể cả chỉ cho phép request đi qua API Gateway proxy chứ không cho gọi thẳng vào Cognito
- Luôn định nghĩa scope ở mức app client theo nguyên tắc least privilege, tránh cấp quyền dư thừa

### Điều mình học được sau bài viết này

Vì mình mới học nên đọc đoạn về caching qua API Gateway và WAF allow-list mình phải đọc lại vài lần mới hình dung được luồng, nhất là đoạn dùng custom header để chỉ cho phép request đi qua proxy. Nhưng điều mình rút ra được là: xác thực không chỉ có một kiểu "user đăng nhập" như mình vẫn nghĩ, mà M2M là một bài toán hoàn toàn khác, với các mối lo về chi phí và bảo mật cũng khác theo.

Project của mình hiện đang dùng Cognito hosted UI với JWT authorizer cho user đăng nhập qua giao diện, chưa có luồng M2M nào, nên đọc bài này giúp mình biết thêm một pattern khác của Cognito mà biết đâu sau này project khác sẽ cần tới.

### Lời kết

Bài "How to monitor, optimize, and secure Amazon Cognito machine-to-machine authorization" theo mình khá chi tiết và còn khá mới (được cập nhật tới tháng 11/2025), nên thông tin về giá và luồng hoạt động chắc vẫn còn sát với hiện tại. Nếu ai đang tìm hiểu về Cognito như mình thì mình nghĩ bài này đáng đọc, dù cần đọc chậm ở phần caching và WAF.

Cảm ơn mọi người đã đọc bài chia sẻ của mình, mình còn đang học nên có gì sai sót mong mọi người chỉ giáo thêm ạ 🙏

Link bài viết tham khảo: <https://aws.amazon.com/blogs/security/how-to-monitor-optimize-and-secure-amazon-cognito-machine-to-machine-authorization/>
