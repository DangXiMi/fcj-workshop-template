---
title: "Sự kiện 4"
date: 2024-01-01
weight: 4
chapter: false
pre: " <b> 4.4. </b> "
---

### Mục tiêu sự kiện

- Cung cấp trải nghiệm thực hành xây dựng ứng dụng AI agent
- Thúc đẩy hợp tác và kết nối giữa những người tham dự
- Cho phép các đội trình bày dự án trước ban giám khảo
- Khuyến khích học tập và ứng dụng thực tế các công nghệ AWS và AI
- Trình diễn giải quyết vấn đề kinh doanh thực tế bằng AI agent

### Diễn giả

- **Nguyễn Gia Hưng** – Trưởng phòng Kiến trúc sư Giải pháp, AWS Vietnam
- **Joseph Marazota** – Trưởng phòng Công nghệ, Châu Á
- **Nguyễn Ngọc Hưng** – Kiến trúc sư Giải pháp
- **Đội chiến thắng: One Team** – Agent Đặt hàng Hội thoại KFC
- **Đội Sign Signal C** – Nền tảng Thông minh Cạnh tranh
- **Đội 3K** – Quản lý Hàng đợi Thông minh (Shepher)
- **Đội Six Pillars** – Hệ thống Chống Rửa tiền (AML)
- **Đội BL** – Trợ lý Kiến trúc & Ước tính Chi phí

### Điểm nổi bật

#### Phát biểu Khai mạc (Joseph Marazota)

- AWS đang đầu tư mạnh vào nhân tài trẻ tại Việt Nam
- Ngành công nghiệp đang chuyển đổi nhanh chóng; AI agent sẽ xử lý phát hành có thể mỗi phút
- Chuyên gia trẻ mang đến mô hình tư duy mới mẻ và không bị ràng buộc bởi tư duy cũ
- Robot không có hướng dẫn con người chỉ là phần cứng; agent tinh chỉnh và phân tích dữ liệu để cải thiện
- 2-3 năm tới sẽ chứng kiến sự chuyển đổi lớn trong các ngành
- **Công thức Thành công:** Năng lực × Tầm nhìn × Kiên trì = Kết quả

#### One Team: Đặt hàng Hội thoại Được hỗ trợ AI cho KFC

**Vấn đề Kinh doanh:**
- Đặt hàng bằng giọng nói của McDonald's thất bại do hallucination và không thể hiểu sắc thái hội thoại con người
- Đặt hàng qua ứng dụng truyền thống tạo ra sự ma sát: người dùng phải rời hội thoại, tải ứng dụng, tạo tài khoản, điều hướng menu phức tạp
- Sự quan tâm của khách hàng giảm sút trong quá trình chuyển đổi ứng dụng

**Giải pháp:**
- **Agent đặt hàng hội thoại đa kênh** trên Zalo (chính) và WhatsApp
- Không cần chuyển đổi ứng dụng; đặt hàng trực tiếp trong nền tảng chat
- Không cần tạo tài khoản mới
- Sử dụng AI để trích xuất ý định và truy vấn của khách hàng
- **Tiny Fish** để thu thập dữ liệu từ trang web chính thức của KFC
- **Cơ sở dữ liệu AWS** để lưu trữ và truy xuất dữ liệu
- Bộ nhớ agent ghi nhớ đơn hàng trước và ngữ cảnh phiên
- Bước xác nhận đơn hàng ngăn hallucination (tránh sự cố 100 miếng gà của McDonald's)

**Kiến trúc:**
- **Đầu vào đa kênh** → Bộ chuyển đổi Kênh → Chuẩn hóa Tin nhắn → Lõi Agent
- **Bộ nhớ Agent** bảo tồn ngữ cảnh phiên qua các cuộc hội thoại
- Tối ưu chi phí: ~$0.006/đơn hàng; chi phí hạ tầng ~$88/tháng
- Độ trễ đầu-cuối: 3-4 giây
- **Giảm 60%** chi phí hạ tầng sử dụng Agent Core

**Bài học từ Đội:**
- Đội có nền tảng và thách thức giao tiếp đa dạng (Indian English, American English, Vietnamese)
- Mặc dù có thách thức, hợp tác hiệu quả
- 70% yếu tố chiến thắng: giải quyết vấn đề kinh doanh thực tế, không chỉ xuất sắc kỹ thuật

#### Đội Sign Signal C: Dream AI – Nền tảng Thông minh Cạnh tranh

**Vấn đề Kinh doanh:**
- Các ý tưởng hackathon truyền thống (To-Do list, bảng điều khiển tiếp thị) không hấp dẫn nhà đầu tư
- **Hiểu biết chính:** Sự tinh vi của công nghệ không thể bù đắp cho thiếu giá trị kinh doanh

**Giải pháp:**
- Nền tảng thu thập tín hiệu phân mảnh từ các công ty đối thủ
- Sử dụng **AWS Bedrock** cho mô hình nền tảng
- **Kiến trúc đa-agent** với giao tiếp A2A (Agent-to-Agent)
- **Subagent Thu thập**: sử dụng Tiny Fish (cho nội dung động) và thu thập API tùy chỉnh
- **Subagent Phân tích**: đánh giá chất lượng dữ liệu sử dụng Langfield để chấm điểm
- Dữ liệu được lưu trong **S3** và **DynamoDB**
- Giao diện ngôn ngữ tự nhiên cho người dùng phi kỹ thuật
- Dự báo ROI, tăng trưởng doanh thu và rủi ro khi áp dụng chiến lược đối thủ

**Thách thức:**
- Phụ thuộc vào dịch vụ bên thứ ba (Tiny Fish, Langfield) làm tăng chi phí đáng kể ($35 → $94/tháng)
- Đội giải quyết lo ngại chi phí bằng cách chuyển sang dịch vụ AWS gốc (WebSocket tools, browser tools)

**Bài học rút ra:**
- Định hướng rõ ràng là quan trọng—quá nhiều ý tưởng không tập trung là phản tác dụng
- Thực thi quan trọng hơn ý tưởng
- Làm việc nhóm đòi hỏi quản lý cái tôi và tin tưởng
- Bắt đầu từ vấn đề kinh doanh, không phải công nghệ

#### Đội 3K: Shepher – Quản lý Hàng đợi Thông minh

**Vấn đề Kinh doanh:**
- Tắc nghẽn tại sân bay, siêu thị và địa điểm tổ chức sự kiện
- Hàng đợi dài gây khó chịu cho khách hàng và kém hiệu quả vận hành

**Giải pháp:**
- Hệ thống giám sát camera hỗ trợ AI sử dụng **YOLO V26** (mô hình nhỏ để tối ưu hiệu quả)
- **ByteTrack** để theo dõi đối tượng và gán ID
- **AWS Kinesis Video Streams** để nhập video
- **Cụm Fargate** để xử lý container
- **Theo dõi theo vùng thời gian thực** với các vùng có thể cấu hình
- **Agent AI** với bộ nhớ để phân tích mẫu tắc nghẽn và đưa ra đề xuất
- Thiết kế human-in-the-loop

**Ngăn xếp Kỹ thuật:**
- YOLO V26 small (tối ưu chi phí: SageMaker ban đầu với mô hình lớn có chi phí $48 cho 3 giờ)
- WebSocket cho giao tiếp thời gian thực
- Hạ tầng AWS để triển khai an toàn, có thể mở rộng

**Trải nghiệm Đội:**
- Hackathon đầu tiên cho hầu hết thành viên
- Bắt đầu với dự án "DREAM AI", thất bại, chuyển hướng sang Shepher
- Nhấn mạnh: **"Code có thể học bất cứ lúc nào; trải nghiệm như hackathon là độc nhất"**
- Quan trọng: Giữ phạm vi quản lý, đừng làm quá kỹ thuật

#### Đội Six Pillars: Adaptive Workflow Engine – Chống Rửa tiền (AML)

**Vấn đề Kinh doanh:**
- Hệ thống AML truyền thống có tỷ lệ dương tính giả 90-95%
- $1.58 nghìn tỷ giao dịch đáng ngờ hàng năm
- Quy trình xem xét thủ công tốn $20-25 mỗi trường hợp và mất hàng giờ
- Chuyên viên phân tích dữ liệu bị kiệt sức vì xử lý thủ công

**Giải pháp:**
- Nền tảng điều tra hỗ trợ AI giảm quy trình 3 giờ xuống phút
- **Nhiều agent chuyên biệt**: KYC Agent, Transaction Agent, Evidence Builder
- **XGBoost** để chấm điểm giao dịch
- **Kiến trúc ba tầng**:
  1. Tầng phát hiện nhanh (phân loại XGBoost trên AWS Bedrock)
  2. Tầng điều tra sâu (điều phối đa-agent với Step Functions)
  3. Tầng xem xét con người (bảng điều khiển quản lý trường hợp)
- **Kinesis Data Streams** để xử lý giao dịch khối lượng lớn
- **DynamoDB** để lưu trữ cảnh báo
- **OpenSearch** để truy xuất vector dựa trên kiến thức pháp lý/topology
- **Bedrock Guardrails** để xác minh đầu ra và ngăn hallucination

**Tính năng chính:**
- Khả năng giải thích: Tất cả suy luận của agent được ghi log để kiểm toán
- Khả năng mở rộng: Một chuyên viên phân tích có thể xử lý nhiều trường hợp cùng lúc
- Human-in-the-loop: Chuyển giao cho các trường hợp không chắc chắn
- Tự phục hồi: Agent có thể học từ kết quả

**Cân nhắc Tin cậy Doanh nghiệp:**
- **Bảo mật**: AWS KMS, IAM, Secret Manager để kiểm soát truy cập
- **Giám sát**: CloudWatch, X-Ray để quan sát
- **Con người**: Quyền quyết định cuối cùng vẫn thuộc về chuyên viên phân tích

**Bài học rút ra:**
- Xác định phạm vi rõ ràng và ngoài phạm vi
- Khung thời gian 24 giờ đòi hỏi phân chia công việc chặt chẽ
- Giữ tâm lý bình tĩnh—tập trung vào học hỏi, không chỉ chiến thắng

#### Đội BL: Trợ lý Kiến trúc & Ước tính Chi phí

**Vấn đề Kinh doanh:**
- SA/Kiến trúc sư nhận yêu cầu khẩn cấp từ khách hàng (2-3 ngày hoặc thậm chí giao hàng trong đêm)
- Tạo sơ đồ kiến trúc thủ công và ước tính chi phí tốn thời gian

**Giải pháp:**
- Giao diện ngôn ngữ tự nhiên để tạo kiến trúc
- **Tải tài liệu** lên cho các chính sách và yêu cầu tùy chỉnh
- Tự động tạo sơ đồ kiến trúc (Draw.io)
- Máy tính chi phí tích hợp cho dịch vụ AWS
- Tạo **Infrastructure-as-Code (IaC)** (CloudFormation, Terraform)
- Triển khai một cú nhấp chuột
- Hỗ trợ người dùng phi kỹ thuật và kiến trúc sư giàu kinh nghiệm

**Lợi ích chính:**
- Giảm nỗ lực SA từ ngày xuống phút
- Loại bỏ vẽ sơ đồ thủ công và ước tính chi phí
- Tự phục vụ cho các bên liên quan phi kỹ thuật
- Tạo và triển khai IaC tự động

### Bài học chính

#### Góc độ kinh doanh

- **Bắt đầu từ vấn đề kinh doanh**, không phải công nghệ—70% yếu tố chiến thắng là giải quyết nhu cầu kinh doanh thực tế
- **Hợp tác mạnh hơn nỗ lực cá nhân**—đội có kỹ năng và nền tảng đa dạng vượt trội hơn cá nhân đơn lẻ
- **Giải quyết vấn đề thực tế** có giá trị hơn thực thi kỹ thuật hoàn hảo
- **Kết nối là quan trọng**—90% công việc đến qua giới thiệu, không phải đăng tuyển công khai
- **Tập trung vào trải nghiệm người dùng**—loại bỏ ma sát, giảm chuyển đổi ứng dụng, duy trì hội thoại tự nhiên

#### Góc độ kỹ thuật

- **Kiến trúc đa-agent** mạnh mẽ nhưng đòi hỏi thiết kế cẩn thận và tối ưu chi phí
- **Tối ưu chi phí** là quan trọng—cân bằng kích thước mô hình, phụ thuộc bên thứ ba và hạ tầng
- **Human-in-the-loop** là thiết yếu cho hệ thống quan trọng (AML, bảo mật, hạ tầng)
- **Bộ nhớ và ngữ cảnh** bảo tồn cải thiện hiệu quả agent
- **Khả năng quan sát** (ghi log, theo dõi, kiểm toán) là quan trọng cho hệ thống production
- **Công cụ mã nguồn mở và bên thứ ba** mang lại chiến thắng nhanh nhưng có thể trở thành nút thắt chi phí/bảo mật

#### Thực hành tốt nhất

- **Quản lý phạm vi**: Giữ dự án tập trung; đừng làm quá kỹ thuật
- **Hình thành đội**: Tìm kỹ năng bổ sung, không giống nhau
- **Nguyên mẫu nhanh**: Xây dựng nhanh, học từ thất bại, lặp lại
- **Tài liệu**: Sơ đồ và kiến trúc quan trọng như code
- **Tư duy bảo mật trước**: Đặc biệt cho hạ tầng tài chính và quan trọng

### Áp dụng vào công việc

- **Áp dụng kiến trúc đa-agent** cho dự án hiện tại, bắt đầu với một trường hợp sử dụng đơn giản
- **Đánh giá chiến lược tối ưu chi phí**—so sánh kích thước mô hình, phụ thuộc bên thứ ba và dịch vụ đám mây gốc
- **Nguyên mẫu giao diện hội thoại** cho ứng dụng hiện có để giảm ma sát người dùng
- **Cải thiện khả năng quan sát** trong hệ thống hiện tại—thực hiện ghi log, theo dõi và kiểm toán
- **Áp dụng guardrails AI** (như Bedrock Guardrails) để ngăn hallucination trong hệ thống production
- **Xây dựng dự án phụ** giải quyết vấn đề kinh doanh thực tế, không chỉ bài tập kỹ thuật
- **Tham gia hackathon và sự kiện cộng đồng** để xây dựng mạng lưới và có trải nghiệm thực tế

### Trải nghiệm sự kiện

Tham dự hackathon **FCAJ x Agentic AI Build Week** là một trải nghiệm vô cùng giá trị, mang lại cái nhìn toàn diện về xây dựng AI agent để giải quyết vấn đề kinh doanh thực tế. Những trải nghiệm chính bao gồm:

#### Học hỏi từ diễn giả
- Chuyên gia từ AWS chia sẻ thực hành tốt nhất trong thiết kế AI agent, kiến trúc đám mây và phát triển nghề nghiệp
- Phát biểu khai mạc của Joseph Marazota nhấn mạnh rằng các chuyên gia trẻ có lợi thế đặc biệt—họ mang góc nhìn mới mẻ và không bị ràng buộc bởi tư duy cũ
- Khuôn khổ **Năng lực × Tầm nhìn × Kiên trì = Kết quả** là một bài học then chốt

#### Dự án nhóm thực tế
- Tham gia hình thành đội, brainstorming và xây dựng AI agent trong khung thời gian chặt chẽ
- Học cách các đội khác nhau tiếp cận cùng vấn đề từ nhiều góc độ khác nhau:
  - One Team tập trung vào đặt hàng hội thoại (KFC)
  - Sign Signal C xây dựng thông minh cạnh tranh
  - Team 3K phát triển quản lý hàng đợi thông minh
  - Six Pillars giải quyết AML
  - Team BL tạo công cụ ước tính kiến trúc

#### Công nghệ mới được khám phá
- AWS Bedrock cho mô hình nền tảng và guardrails
- Tiny Fish cho thu thập dữ liệu web và trích xuất
- YOLO V26 cho thị giác máy tính thời gian thực
- Step Functions để điều phối luồng công việc đa-agent
- OpenSearch cho truy xuất vector
- AWS Kinesis cho xử lý dữ liệu streaming

#### Kết nối và thảo luận
- Hackathon cung cấp cơ hội kết nối với builder, kỹ sư và chuyên gia kinh doanh
- Các ví dụ thực tế củng cố rằng **70% thành công** đến từ giải quyết vấn đề kinh doanh thực tế, không chỉ xuất sắc kỹ thuật
- Các đội có nền tảng đa dạng (Ấn Độ, Việt Nam, Mỹ) cho thấy sức mạnh của hợp tác toàn cầu

#### Bài học rút ra
- Bắt đầu từ vấn đề kinh doanh, không phải công nghệ, dẫn đến giải pháp có tác động hơn
- Làm việc nhóm đòi hỏi quản lý cái tôi và tin tưởng—định hướng rõ ràng là quan trọng
- Tối ưu chi phí quan trọng như năng lực kỹ thuật
- Human-in-the-loop là thiết yếu cho hệ thống quan trọng
- Tốc độ quan trọng: xây dựng nhanh, kiểm tra, học hỏi và lặp lại

#### Hình ảnh sự kiện
![Speaker presentation](/fcj-workshop-template/images/3-Event/Event4/AI_Agent_Build.png)
