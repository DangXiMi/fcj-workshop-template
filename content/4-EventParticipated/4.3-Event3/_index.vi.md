---
title: "Sự kiện 3"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 4.3. </b> "
---

### Mục tiêu sự kiện

- Trình diễn các ứng dụng AI agent thực tế trong nhiều lĩnh vực
- Cung cấp hiểu biết kỹ thuật thực tế từ các chuyên gia trong ngành
- Thúc đẩy học tập cộng đồng và kết nối
- Trình diễn các dịch vụ AWS trong production (Amazon Q, Bedrock, DevOps Agent, Voice AI)
- Nhấn mạnh sự giao thoa giữa AI, kinh doanh và nhu cầu doanh nghiệp

### Diễn giả

- **Steve Trần** – Nhà sáng lập, Cloud Thinker
- **Hiếu Nghị** – Renova Cloud (Phiên Voice AI)
- **Kiệt** – Student Builder (Trình diễn Voice AI)
- **Trung** – Nhà sáng lập & CEO, R AI
- **Bảo** – Kỹ sư Đám mây, Cloud Kinetics (DevOps Agent)
- **Nguyên** – Kỹ sư Đám mây, Cloud Kinetics (DevOps Agent)
- **Trường** – Kiến trúc sư Giải pháp AI, Noventis (Amazon Q & HR)
- **Minh Anh** – Kiến trúc sư Giải pháp, Noventis (Amazon Q & HR)
- **Toàn Nguyễn** – AWS Security Builder (Amazon Q Bảo mật)
- **Nghị** – Renova Cloud (Amazon Q Bảo mật)

### Điểm nổi bật

#### Phiên 1: Vận hành Đám mây & AI (Steve Trần – Cloud Thinker)

**Hành trình Nghề nghiệp & Góc nhìn Thị trường:**
- Bắt đầu trong lĩnh vực IT trong thời kỳ COVID; nhu cầu đám mây bùng nổ
- Nhận ra đám mây là thị trường tăng trưởng cao và chuyển hướng sớm
- AI đang chuyển dịch nhu cầu từ lập trình viên junior sang kỹ sư senior có thể sử dụng hiệu quả các công cụ AI
- Thách thức doanh nghiệp hiện tại: **độ phức tạp** – hệ thống cũ, đa đám mây và thiếu nhân tài DevOps

**Nền tảng Cloud Thinker:**
- Giải quyết các điểm đau vận hành bằng **agentic AI**:
  - **Quản lý Sự cố**: AI điều tra nguyên nhân gốc rễ trong vài phút thay vì hàng giờ
  - **Kiểm soát Chất lượng**: AI xem xét các thay đổi hạ tầng trước production để giảm lỗi
  - **Tối ưu Chi phí**: AI liên tục giám sát và đề xuất tối ưu – nhiều khách hàng đã chuyển tác vụ FinOps cho AI
  - **Bảo mật**: Kiểm tra thâm nhập và đánh giá tuân thủ tích hợp sẵn

**Quyết định Kiến trúc Quan trọng:**
- **Đa-agent so với Single Agent**: Tranh luận giữa agent chuyên biệt và một siêu agent
  - Đa-agent cho phép ngữ cảnh tập trung hơn, kiểm soát chi phí tốt hơn và phân quyền theo vai trò
  - Single agent có thể làm 95% tác vụ, nhưng với chi phí cao hơn và rủi ro hallucination
  - Cloud Thinker sử dụng **kiến trúc đa-agent** để xử lý độ phức tạp doanh nghiệp tốt hơn

**Thách thức cho Startups:**
- Bán hàng cho doanh nghiệp đòi hỏi thay đổi 50% quy trình của họ
- Cần **khách hàng tiên phong** (ví dụ: F88, FPT) để xác nhận phù hợp sản phẩm-thị trường
- Xây dựng **dịch vụ quản lý đầy đủ** để giáo dục và hỗ trợ chuyển đổi doanh nghiệp
- Dự kiến nỗ lực onboarding doanh nghiệp gấp 10 lần so với phân phối SaaS

**Bài học:** Tập trung vào vấn đề thực tế; làm việc nhanh, lặp lại và tìm khách hàng sớm.

#### Phiên 2: Voice AI – Kích hoạt Agent Giọng nói Tiếng Việt (Hiếu Nghị, Kiệt, Trung)

**Bối cảnh Voice AI:**
- Các mô hình speech-to-speech chủ yếu chỉ hỗ trợ tiếng Anh – tiếng Việt là **ngôn ngữ ít tài nguyên**
- Cách tiếp cận hiện tại tại Việt Nam: pipeline **STT → LLM → TTS** (các thành phần riêng biệt)
- Điều này cho phép kiểm soát, gọi công cụ và hỗ trợ ngôn ngữ Việt

**Thành phần:**
- **STT (Speech-to-Text)**: Chuyển giọng nói thành văn bản – được huấn luyện tùy chỉnh cho giọng Việt
- **LLM**: Xử lý suy luận, ngữ cảnh, gọi công cụ – hoạt động tốt với tiếng Việt
- **TTS (Text-to-Speech)**: Chuyển phản hồi thành giọng nói – có thể tùy chỉnh cho giọng/kịch bản khác nhau

**Thách thức cho Voice AI Tiếng Việt:**
- **Xử lý giọng vùng**: Dữ liệu huấn luyện bao gồm 10-20% giọng vùng miền (Bắc, Trung, Nam)
- **Phát hiện giới tính**: Tiếng Việt yêu cầu sử dụng đại từ xưng hô đúng (anh/chị) – mô hình phải phát hiện giới tính người nói
- **Xử lý ngắt lời**: Mô hình phải quyết định khi nào nên nói và khi nào lắng nghe – đòi hỏi huấn luyện bổ sung
- **Độ trễ**: Streaming đầu-cuối là quan trọng cho hội thoại tự nhiên

**Tính năng Doanh nghiệp:**
- **Quản lý prompt tự phục vụ** cho người dùng kinh doanh (phi kỹ thuật)
- **Phiên bản và nhật ký kiểm toán** để tuân thủ (giống GitHub)
- Tích hợp **Cơ sở tri thức** cho câu trả lời theo lĩnh vực
- **Chuyển giao cho con người**: Chuyển đổi liền mạch từ AI sang người khi AI không xử lý được truy vấn
- **Cá nhân hóa giọng nói**: Giọng theo trường hợp sử dụng cụ thể (ví dụ: thu hồi nợ có thể sử dụng giọng vùng miền để tương tác tốt hơn)

**Trình diễn trực tiếp:**
- Quick Agent xây dựng trên **AWS Bedrock** với **Knowledge Base** hỗ trợ sản phẩm Apple
- Trả lời câu hỏi về MacBook Pro – speech-to-speech bằng tiếng Anh (sau đó làm rõ hỗ trợ tiếng Việt đang phát triển)

**Bài học:** Voice AI tiếng Việt là một lĩnh vực đang phát triển; tập trung vào cách tiếp cận pipeline để kiểm soát và độ tin cậy.

#### Phiên 3: DevOps Agent – Quản lý Sự cố Thông minh (Bảo & Nguyên – Cloud Kinetics)

**Vấn đề:**
- Khắc phục sự cố thủ công bị phân mảnh: logs ở nhiều nơi, khoảng cách tri thức, gián đoạn liên tục
- MTTR (Thời gian trung bình để khắc phục) quá cao do thiếu ngữ cảnh

**Giải pháp – AWS DevOps Agent:**

**Sáu Năng lực Cốt lõi:**
1. **Học ngữ cảnh**: Agent xây dựng topology của toàn bộ hạ tầng (AWS, on-prem, Azure) – học các mối quan hệ và phụ thuộc
2. **Kiểm soát**: Phân quyền đầy đủ – agent có thể bị giới hạn đối với tài nguyên cụ thể qua tags và chính sách IAM
3. **Tích hợp**: Có thể mở rộng qua MCP (Model Context Protocol) – kết nối với bất kỳ nguồn dữ liệu nào (logs, cơ sở dữ liệu, công cụ tùy chỉnh)
4. **Hợp tác**: Người dùng có thể trò chuyện, nhận đề xuất và chuyển đến hệ thống ticketing (ServiceNow, Slack)
5. **Thuận tiện**: Thiết lập một cú nhấp chuột qua AWS Console; giao diện chat dựa trên web
6. **Hiệu quả chi phí**: Định giá theo giây ($0.083/giây), không theo token – thanh toán dễ dự đoán

**Cách hoạt động (4 Bước):**
1. **Kích hoạt**: Cảnh báo (CloudWatch) hoặc điều tra do người dùng khởi tạo
2. **Điều tra**: Agent phân tích logs, metrics, traces và topology để tạo giả thuyết
3. **Giảm thiểu**: Đề xuất các bước khắc phục (không tự động thực thi – ưu tiên an toàn)
4. **Cải thiện**: Đề xuất sửa chữa dài hạn (ví dụ: thêm cache, mở rộng tài nguyên)

**Trình diễn trực tiếp:**
- Mô phỏng tấn công DDoS trên ứng dụng thương mại điện tử (ECS + ALB)
- Agent phát hiện độ trễ cao, điều tra, xác định 10 tác vụ ECS tạo 1000 request/giây và cung cấp kế hoạch giảm thiểu (dừng tác vụ, thu nhỏ)
- Agent cũng tạo phân tích nguyên nhân gốc rễ với các lệnh có thể hành động (copy-paste vào terminal)
- Sau khi áp dụng sửa chữa, ứng dụng trở lại bình thường

**Chỉ số thành công (từ các trường hợp khách hàng):**
- Đại học (200k sinh viên): Giảm MTTR từ 2 giờ xuống 28 phút (-77%)
- Zenchef (nền tảng nhà hàng): Tìm cấu hình sai trong 20 phút (-75% so với thủ công)
- KDDI (viễn thông Nhật Bản): Giảm thời gian điều tra từ tuần xuống ngày

**Điều kiện tiên quyết cho Thành công:**
- Khả năng quan sát tốt: logs, metrics và alarms toàn diện
- Hệ thống quy mô lớn: giá trị nhiều hơn trong môi trường phức tạp
- Human-in-the-loop: agent đề xuất, con người thực thi

**Bài học:** DevOps Agent là hệ số nhân lực cho đội SRE/DevOps; nó không thay thế kỹ năng mà khuếch đại chúng.

#### Phiên 4: Amazon Q – AI cho HR và Quản lý Nhân tài (Trường & Minh Anh – Noventis)

**Điểm đau của HR trong Kỷ nguyên AI:**
- Sàng lọc CV thủ công tốn thời gian và dễ sai sót – thường bỏ lỡ nhân tài chủ chốt
- Không có khuôn khổ chuẩn hóa để đánh giá ứng viên qua các vai trò
- Lo ngại về quyền riêng tư dữ liệu khi sử dụng công cụ AI công khai (lộ dữ liệu nhân sự nhạy cảm)
- Chi phí cao của tuyển dụng sai: trì hoãn, hiệu suất nhóm thấp, tỷ lệ nghỉ việc cao

**Amazon Q – Trợ lý AI Agentic:**
- **Agent tùy chỉnh**: Xây dựng kỹ năng cho các tác vụ cụ thể (ví dụ: Trợ lý Đánh giá Nhân tài)
- **Nghiên cứu đa nguồn**: Truy vấn tài liệu nội bộ, trang web và dữ liệu có cấu trúc
- **Thông minh kinh doanh tự động**: Truy vấn ngôn ngữ tự nhiên trên tập dữ liệu – không cần SQL
- **Tự động hóa luồng**: Tự động hóa các luồng công việc lặp lại (email, lên lịch, phê duyệt)

**Tích hợp Dữ liệu:**
- Kết nối với Microsoft (SharePoint, Outlook, OneDrive) và Google Workspace (Gmail, Drive)
- Có thể kết nối với bất kỳ hệ thống nào qua custom MCP connectors
- Dữ liệu nằm trong AWS – an toàn, tuân thủ (đã có local zone tại Việt Nam)

**Trình diễn Trường hợp sử dụng HR:**
1. **Tạo Skill**: Upload file MD mô tả quy trình đánh giá nhân tài – Q tự động xây dựng skill
2. **Tạo Mô tả Công việc**: Yêu cầu Q tạo JD cho "Kỹ sư Đám mây Junior" – nó tạo JD hoàn chỉnh
3. **Sàng lọc CV**: Upload thư mục CV; Q xếp hạng ứng viên theo JD với điểm số (Xuất sắc, Tốt, Trung bình, Rất thấp)
4. **Tạo Báo cáo**: Q tạo bảng điều khiển trực quan hiển thị điểm số, điểm mạnh và đề xuất của ứng viên
5. **Hành động**: Q có thể gửi email, lên lịch phỏng vấn và cập nhật hệ thống theo dõi qua tự động hóa

**Kết quả:**
- Giảm thời gian sàng lọc từ ngày xuống phút
- Đánh giá chuẩn hóa qua tất cả ứng viên
- Cho phép HR tập trung vào quyết định chiến lược

**Tích hợp Bảo mật (Phiên Toàn & Nghị):**
- **Kết nối riêng tư**: Sử dụng **VPC Interface Endpoint** để Amazon Q kết nối với MCP server mà không lộ ra internet
- **Lợi ích**: Không IP công khai, không rủi ro tấn công MITM, dữ liệu nằm trong VPC, đáp ứng tuân thủ (ví dụ: lưu trữ dữ liệu)
- **Dự toán chi phí**: ~$250–350/tháng cho thiết lập riêng tư (bao gồm Route53 Resolver, ALB, EC2, truyền dữ liệu)

**Bài học:** Amazon Q dân chủ hóa AI cho đội ngũ phi kỹ thuật – HR, Tài chính và Vận hành giờ đây có thể sử dụng AI một cách an toàn và hiệu quả.

### Bài học chính

#### Góc độ kinh doanh

- AI không thay thế phán đoán con người mà khuếch đại nó – đặc biệt trong các lĩnh vực quan trọng (HR, bảo mật, vận hành)
- Doanh nghiệp ưu tiên **bảo mật**, **tuân thủ** và **kiểm soát** – kết nối riêng tư và lưu trữ dữ liệu là điều bắt buộc
- Trợ lý AI **Low-code/No-code** (như Amazon Q) trao quyền cho người dùng kinh doanh sử dụng AI mà không cần kỹ năng kỹ thuật sâu
- **Thời gian đến giá trị** là quan trọng – các công cụ giảm nỗ lực thủ công (sàng lọc CV, điều tra sự cố) mang lại ROI ngay lập tức

#### Góc độ kỹ thuật

- **Kiến trúc đa-agent** được ưa chuộng cho độ phức tạp doanh nghiệp nhờ kiểm soát, chi phí và chuyên môn hóa lĩnh vực
- **Voice AI tiếng Việt** yêu cầu cách tiếp cận pipeline (STT → LLM → TTS) vì các mô hình end-to-end không hỗ trợ ngôn ngữ ít tài nguyên
- **MCP (Model Context Protocol)** là yếu tố then chốt để tích hợp AI với hệ thống bên ngoài – thiết yếu cho áp dụng doanh nghiệp
- **Kết nối riêng tư** là bắt buộc cho dịch vụ AI cấp production – tránh lộ API nội bộ ra internet công khai
- **Streaming** là quan trọng cho tương tác thời gian thực – cả cho voice và chat

#### Thực hành tốt nhất

- **Bắt đầu nhỏ** – xây dựng MVP giải quyết điểm đau thực tế, sau đó lặp lại dựa trên phản hồi
- **Thiết kế với human-in-the-loop** – đặc biệt trong hệ thống quan trọng (AML, bảo mật, hạ tầng)
- **Đầu tư vào khả năng quan sát** – AI agent chỉ tốt như dữ liệu chúng có thể truy cập
- **Chọn kiến trúc phù hợp** – single vs. multi-agent phụ thuộc vào trường hợp sử dụng và ràng buộc chi phí
- **Ưu tiên bảo mật từ ngày đầu** – quản trị dữ liệu và kiểm soát truy cập nên được tích hợp, không thêm sau

### Áp dụng vào công việc

- **Đánh giá kiến trúc đa-agent** cho dự án hiện tại – so sánh chi phí, độ phức tạp và tính linh hoạt với single agent
- **Nguyên mẫu voice agent** sử dụng pipeline STT → LLM → TTS – bắt đầu với tiếng Anh hoặc mô hình tiếng Việt hiện có
- **Thử nghiệm Amazon Q** – sử dụng tầng miễn phí để tự động hóa một luồng công việc nhỏ (ví dụ: tóm tắt email, tạo báo cáo)
- **Cải thiện khả năng quan sát** trong hệ thống của bạn – đảm bảo logs, metrics và traces có sẵn cho AI agent
- **Thực hiện kết nối riêng tư** nếu phát triển dịch vụ AI sử dụng nội bộ – tránh lộ API ra internet
- **Áp dụng MCP** để kết nối AI agent với hệ thống hiện có (cơ sở dữ liệu, ticketing, HR)

### Trải nghiệm sự kiện

Tham dự **FCAJ Community Day - June 2026** là một chuyến tham quan sâu rộng về cách AI agent đang chuyển đổi vận hành doanh nghiệp. Những trải nghiệm chính bao gồm:

#### Học hỏi từ diễn giả đa dạng
- Steve Trần chia sẻ hành trình từ lập trình viên đến nhà sáng lập, nhấn mạnh tầm quan trọng của việc giải quyết vấn đề thực tế và tìm khách hàng tiên phong
- Phiên Voice AI nhấn mạnh những thách thức đặc biệt của ngôn ngữ Việt và cách tiếp cận pipeline thực tế
- Trình diễn DevOps Agent cho thấy AI có thể giảm đáng kể thời gian xử lý sự cố – một lợi ích kinh doanh hữu hình
- Phiên Amazon Q chứng minh AI không chỉ dành cho kỹ sư; HR và đội ngũ kinh doanh cũng có thể sử dụng nó

#### Trải nghiệm kỹ thuật thực tế
- Hiểu sự đánh đổi giữa kiến trúc đa-agent và single-agent
- Học về MCP và cách tích hợp AI với API bên ngoài
- Xem trình diễn trực tiếp AI agent trong hành động – từ điều tra sự cố đến sàng lọc CV
- Khám phá tầm quan trọng của kết nối riêng tư cho bảo mật doanh nghiệp

#### Công nghệ mới được khám phá
- **AWS Bedrock** (mô hình nền tảng, guardrails)
- **Amazon Q** (trợ lý AI agentic cho người dùng kinh doanh)
- **DevOps Agent** (quản lý sự cố)
- **MCP (Model Context Protocol)** cho tích hợp AI
- **Voice AI** (STT, LLM, TTS) cho tiếng Việt

#### Kết nối và thảo luận
- Tương tác với diễn giả và người tham dự trong các phiên hỏi đáp
- Học về thách thức và giải pháp thực tế từ các ngành khác nhau (ngân hàng, bán lẻ, viễn thông)
- Hiểu rằng áp dụng AI khác nhau theo ngành – một số tiên tiến hơn, số khác mới bắt đầu

#### Bài học rút ra
- **AI là hệ số nhân lực**, không phải thay thế – nó khuếch đại kỹ năng của những người sử dụng tốt
- **Bảo mật và tuân thủ** là quan trọng cho áp dụng doanh nghiệp – kết nối riêng tư và lưu trữ dữ liệu là điều bắt buộc
- **Kiến trúc đa-agent** cung cấp kiểm soát và tối ưu chi phí tốt hơn hệ thống single-agent
- **Xây dựng sản phẩm AI** cho doanh nghiệp đòi hỏi kiên nhẫn và cộng tác chặt chẽ với khách hàng

#### Hình ảnh sự kiện
![Speaker presentation](/images/3-Event/Event3/event3.png)
