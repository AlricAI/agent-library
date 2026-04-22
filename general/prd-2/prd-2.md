---
name: PRD
description: ## 1. Thông Tin Chung

- **Tên tính năng**: DevCoach.ai - Nền tảng AI Luyện Phỏng Vấn IT Thực Chiến
- **Người tạo/Chủ sở hữu**: Team 002
- **Các bên l
model: claude-sonnet-4-5
---
# PRD - DevCoach.ai: Nền tảng AI Luyện Phỏng Vấn IT Thực Chiến

## 1. Thông Tin Chung

- **Tên tính năng**: DevCoach.ai - Nền tảng AI Luyện Phỏng Vấn IT Thực Chiến
- **Người tạo/Chủ sở hữu**: Team 002
- **Các bên liên quan chính**: Team 002
- **Trạng thái**: Review
- **Ngày cập nhật cuối**: 07/04/2026

## 2. Tổng Quan, Mục Tiêu và Giải Pháp

### 2.1. Bối cảnh và vấn đề cần giải quyết (Pain points)
Các bạn sinh viên IT năm cuối hoặc lập trình viên Fresher mới ra trường thường có nền tảng chuyên môn tốt nhưng lại thiếu kỹ năng mềm. Hệ quả là họ mất tự tin, lúng túng khi đối mặt với nhà tuyển dụng, dẫn đến việc trượt phỏng vấn và đánh mất cơ hội việc làm. Tuy nhiên các giải pháp career coaching truyền thống lại quá đắt đỏ ($200-500/session).

### 2.2. Mục tiêu
- Khởi chạy thành công nền tảng Web App ứng dụng AI Multi-Agent đóng vai trò Interview Coach.
- Tạo ra luồng doanh thu tự động thông qua mô hình thu phí 50.000 VNĐ/tài khoản/tháng.
- Giúp người dùng nhận diện ngay lập tức các lỗ hổng kiến thức và cải thiện kỹ năng trả lời qua framework STAR.
- Cung cấp biểu đồ theo dõi sự tiến bộ (Progress Tracking), giúp ứng viên nhìn thấy điểm số kỹ năng mềm (STAR) và kỹ năng cứng (IT Rubric) tăng lên sau mỗi phiên mock interview, từ đó xây dựng sự tự tin thực sự trước ngày phỏng vấn.

### 2.3. Giải pháp
DevCoach.ai không phải là một chatbot thông thường, mà là một hệ thống đánh giá năng lực dựa trên dữ liệu thực tế:
- **Dữ liệu lõi thực chiến**: Hệ thống tích hợp một tập dữ liệu các câu hỏi phỏng vấn thực tế từ các doanh nghiệp IT. AI sẽ đối chiếu từ khóa trong CV và JD để trích xuất câu hỏi bám sát thực tế nhất.
- **Multi-Agent Roleplay (Phỏng vấn Đa vai)**:
    - **Technical Interview Agent**: Không hỏi định nghĩa học thuật. Ví dụ: Nếu hệ thống nhận diện ứng viên ứng tuyển vị trí AI Engineer và có ghi kinh nghiệm làm việc với LLM/RAG, thay vì hỏi định nghĩa 'RAG là gì?', Agent sẽ đưa ra tình huống: *"Hệ thống RAG của bạn thỉnh thoảng sinh ra câu trả lời sai (hallucination) do dữ liệu truy xuất từ vector database có quá nhiều thông tin nhiễu. Bạn sẽ tinh chỉnh bước chunking data, tối ưu thuật toán search hay thiết kế lại prompt như thế nào để khắc phục tình trạng này?”*.
    - **HR/Behavioral Agent**: Chuyên đặt các câu hỏi hành vi (behavioral questions) để kiểm tra mức độ phù hợp văn hóa.
- **Báo cáo Đánh giá Kép**: Đánh giá dựa trên 2 tiêu chuẩn: Kỹ năng diễn đạt theo chuẩn STAR (Situation - Task - Action - Result) và Độ chính xác kỹ thuật theo IT Rubric (Problem-solving, System Thinking).

## 3. Phạm vi và Giả định

### Trong phạm vi:
- **Thiết lập ngữ cảnh phỏng vấn**: Hỗ trợ người dùng tải lên CV cá nhân (giới hạn định dạng PDF) và dán nội dung văn bản Job Description (JD). Hệ thống AI tự động phân tích và trích xuất từ khóa chuyên môn từ CV và JD để cấu hình ngữ cảnh (Context) cá nhân hóa cho từng ứng viên.
- **Tương tác phỏng vấn**: Giao diện phòng phỏng vấn trực tiếp bằng văn bản. Người dùng gõ câu trả lời, AI phản hồi bằng văn bản. Tích hợp luồng AI Multi-Agent (Interviewer, Evaluator) để đặt câu hỏi linh hoạt, tự động nhận diện câu trả lời hời hợt để hỏi xoáy sâu.
- **Báo cáo & Đánh giá**: Màn hình Dashboard quản lý và lưu trữ lịch sử các phiên phỏng vấn. Hệ thống phân tích chi tiết từng đoạn chat theo framework STAR (Chỉ ra điểm mạnh, điểm yếu và gợi ý câu trả lời mẫu tối ưu).

### Ngoài phạm vi:
- **Tính năng giọng nói**: Hệ thống chưa tích hợp nhận diện giọng nói (Speech-to-Text) hay phát âm thanh (Text-to-Speech).
- **Đa ngôn ngữ**: Không hỗ trợ phỏng vấn bằng các ngôn ngữ khác (như tiếng Anh). Giai đoạn v1.0 tập trung 100% tối ưu Prompt để AI hiểu ngữ cảnh và giao tiếp tự nhiên bằng Tiếng Việt.
- **Định dạng tài liệu phức tạp**: Không hỗ trợ đọc/trích xuất thông tin CV từ file Word hoặc CV dạng hình ảnh, chỉ nhận PDF.
- **Khách hàng doanh nghiệp**: Không xây dựng hệ thống quản trị nội bộ cho phòng HR doanh nghiệp. Sản phẩm tập trung tối đa cho người dùng cá nhân.

### Giả định:
- Người dùng mục tiêu có thiết bị (Laptop/Mobile).
- Người dùng sẵn sàng chi trả 50.000 VNĐ cho một công cụ giúp họ tăng cơ hội có việc làm.

### Phụ thuộc:
- Phụ thuộc vào tính ổn định và giới hạn token của API OpenAI/Anthropic.

## 4. Yêu Cầu Nghiệp Vụ

### User Story:
- Với vai trò là một sinh viên IT năm cuối, tôi muốn hệ thống AI hỏi xoáy vào các kỹ năng công nghệ tôi ghi trong CV dựa trên JD, để tôi có thể luyện tập phản xạ và chuẩn bị tâm lý tốt nhất trước buổi phỏng vấn thực tế.
- Với vai trò là một ứng viên, tôi muốn nhận được báo cáo chỉ rõ điểm yếu trong cách trả lời của mình theo mô hình STAR, để tôi có thể sửa lỗi và cải thiện khả năng thuyết phục HR.

### Giá Trị Kinh Doanh:
- Tạo nguồn thu trực tiếp từ end-user thông qua gói dịch vụ 50.000 VNĐ/tài khoản.
- Thu thập dữ liệu hành vi trả lời phỏng vấn (có thông báo tới người dùng) để có thể fine-tune mô hình AI độc quyền trong tương lai.

## 5. Yêu Cầu Chức Năng
*(Bổ sung sau)*

## 6. Yêu Cầu Phi Chức Năng
*(Bổ sung sau)*

- **Hiệu năng (Performance)**:
- **Kiến trúc Hệ thống (Architecture)**:

## 7. Thiết Kế & Trải Nghiệm Người Dùng (UX/UI)
*(Bổ sung sau)*

- **Luồng người dùng (User Flow)**:
- **Thiết kế chi tiết (High-Fidelity)**:

## 8. Kế Hoạch Phát Hành & Đo Lường
*(Bổ sung sau)*

## 9. Phụ Lục
*(Bổ sung sau)*