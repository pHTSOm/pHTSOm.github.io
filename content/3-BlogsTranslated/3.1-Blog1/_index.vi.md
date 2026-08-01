---
title: "Blog 1 - CloudFormation Express Mode"
date: 2026-02-04
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# AWS DevOps Blog | CloudFormation Express Mode – Vài điều mình học được khi mới bắt đầu tìm hiểu AWS

Xin chào mọi người,

Mình mới bắt đầu học AWS được một thời gian, đang tập làm quen với CloudFormation nên hay lên AWS Blog đọc để hiểu thêm. Hôm trước mình đọc được bài "How CloudFormation express mode accelerates your development cycle" mà thấy khá dễ hiểu (dù ban đầu cũng phải đọc đi đọc lại vài lần 😅), nên muốn chia sẻ lại những gì mình hiểu được, có gì sai sót mong mọi người góp ý thêm.

Đầu tiên mình tưởng đây chỉ đơn giản là một tùy chọn để deploy nhanh hơn thôi. Nhưng đọc kỹ thì mình mới vỡ ra là nó không chỉ nhanh hơn không, mà nó thay đổi cả cách CloudFormation báo cho mình biết "xong" nghĩa là gì.

### Mình hiểu vấn đề như thế này

Theo bài viết thì bình thường khi mình deploy một resource, CloudFormation không chỉ tạo ra resource đó xong là báo hoàn thành liền, mà nó còn chờ cho tới khi resource đó thật sự sẵn sàng hoạt động (gọi là "stabilize"). Ví dụ như CloudFront distribution thì phải mất 5-10 phút mới lan được ra hết các edge location trên thế giới. Cái này thì hợp lý nếu mình đang deploy cho production, nhưng nếu mình chỉ đang test đi test lại nhiều lần trong lúc học/code thì lại thấy hơi lâu, vì mình chưa cần traffic thật vào đâu, chỉ cần biết là mình cấu hình đúng chưa thôi.

### Vậy Express mode giúp gì?

Đọc xong thì mình hiểu đại khái là: Express mode cho phép CloudFormation báo "xong" ngay khi resource được cấu hình xong, còn việc nó "chín" hoàn toàn để chạy được thì để chạy ngầm phía sau. Mình thấy hay ở chỗ là nó vẫn cho mình biết resource nào đã cấu hình xong, resource nào còn đang chạy ngầm, chứ không phải giấu đi thông tin đó. Với lại thứ tự phụ thuộc giữa các resource (cái nào cần cái nào tạo trước) thì vẫn được giữ nguyên như bình thường, không bị đảo lộn.

Có một chỗ mình thấy khá thú vị là nó tắt sẵn tính năng rollback tự động. Lúc đầu mình hơi bất ngờ vì cứ nghĩ rollback tự động là tốt, nhưng đọc kỹ thì mới hiểu là khi đang test nhiều lần, nếu lỗi mà tự động rollback về trạng thái cũ thì mình mất luôn context để sửa lỗi, nên tắt đi để mình sửa tại chỗ lại hợp lý hơn.

### Điều mình rút ra được

Vì mình còn mới nên đọc bài này chủ yếu để hiểu thêm khái niệm, chưa dám nói là hiểu sâu 100%. Nhưng điều mình thấy hay nhất là mình học được một khái niệm mới: "cấu hình xong" và "sẵn sàng phục vụ" là hai chuyện khác nhau, không phải lúc nào cũng đi chung với nhau. Trước giờ mình cứ nghĩ đơn giản là deploy xong thì dùng được luôn.

Trong lúc làm phần backend và CI/CD cho đồ án tốt nghiệp, thỉnh thoảng mình cũng deploy đi deploy lại chỉ để lấy một cái ID hay endpoint nào đó cho bước sau, nên đọc bài này mình thấy đúng kiểu tình huống mình hay gặp, dù mình dùng Terraform là chính chứ chưa rành CloudFormation lắm.

### Lời kết

Bài "How CloudFormation express mode accelerates your development cycle" theo mình là một bài dễ tiếp cận cho người mới như mình, giúp hiểu thêm về cách CloudFormation vận hành phía sau. Nếu ai cũng đang mới học AWS như mình thì mình nghĩ bài này đáng đọc thử, đọc xong chắc mọi người sẽ hiểu rõ hơn khái niệm "stabilize" mà trước giờ mình cũng ít để ý tới.

Cảm ơn mọi người đã đọc bài chia sẻ của mình, mình còn đang học nên có gì sai sót thì mong mọi người chỉ giáo thêm ạ 🙏

Link bài viết tham khảo: <https://aws.amazon.com/blogs/devops/how-cloudformation-express-mode-accelerates-your-development-cycle/>
