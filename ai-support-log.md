# AI SUPPORT LOG
**Học viên:** Nguyễn Khánh Duy — **Mã học viên (MHV):** `2A202602403`  
**Dự án:** VinStay AI (Team P-010) — Build Phase Cohort 4 (Track 1 — Day 20)  
**Ngày thực hiện:** 06/10/2026

---

### 1. AI đã giúp tôi ở đâu?
* **Brainstorm ứng viên Core Action và đặt câu hỏi phản biện:** AI đã giúp liệt kê và so sánh giữa các hành vi trong phễu thuê nhà (Xem catalog All-in, Đặt lịch hẹn có OTP, Tham gia xem thực tế với Field Host, Cọc giữ chỗ 2.000.000đ qua VietQR).
* **Đóng vai "Khách thuê khó tính" (Challenger):** AI phản biện góc nhìn của Persona Nguyễn Minh Anh về những rào cản tâm lý khi xuống tiền cọc online, giúp tôi định nghĩa rõ ràng điều kiện tiên quyết (`Preconditions`) và tiêu chuẩn hoàn cọc 100% nếu phát hiện thông tin sai lệch.
* **Chuẩn hóa cú pháp Event Tracking và Acceptance Criteria:** Hỗ trợ quy chuẩn hóa danh mục 6 Core Events theo đúng định dạng `object_action` (snake_case) và gợi ý 2 tiêu chí nghiệm thu về tính toàn vẹn dữ liệu (chống bắn event sớm và chống trùng lặp Idempotency).

---

### 2. AI sai, hời hợt hoặc đề xuất metric sai nature ở đâu?
* **Đề xuất ép Daily / Weekly Active Users (DAU/WAU):** Ban đầu, AI có xu hướng máy móc đề xuất đo lường DAU và WAU cho VinStay AI dựa trên các template dashboard thông thường của sản phẩm phần mềm. Đây là sai lầm nghiêm trọng về mặt bản chất ngành (Nature vs Nurture), vì không có người thuê nhà nào cần hoặc muốn cọc nhà hay mở app tìm phòng mỗi ngày.
* **Nhầm lẫn tính năng "Chat tư vấn AI" thành Core Action:** AI từng gợi ý lấy việc "User gửi câu hỏi cho VinStay AI Chatbot" làm Core Action. Tôi nhận thấy đây chỉ là một thao tác giao diện (`UI interaction`) và output của mô hình ngôn ngữ lớn, hoàn toàn chưa chứng minh được người dùng đã nhận được giá trị cốt lõi hay chưa.
* **Gợi ý North Star Metric thuần doanh thu hoặc lượt tìm kiếm:** AI ban đầu đề xuất NSM là "Tổng doanh thu tiền hoa hồng" hoặc "Số lượt tìm kiếm căn hộ", vốn là vanity metrics dễ bị thao túng và không phản ánh chất lượng trải nghiệm của khách thuê.

---

### 3. Tôi đã tự sửa hoặc quyết định lại điều gì?
* **Quyết định chọn "Cọc giữ chỗ 2.000.000đ qua VietQR" làm Core Action:** Tôi đã bác bỏ các gợi ý về thao tác giao diện để chọn hành vi cọc giữ chỗ làm Core Action, vì đây là thời điểm xác nhận giá trị then chốt giải quyết trọn vẹn nỗi đau phòng trống của chủ nhà và nỗi đau bị hớt tay trên của khách thuê.
* **Xác lập lại Cadence theo nhịp tự nhiên của thị trường bất động sản:** Tôi đã tự điều chỉnh nhịp đo sang Monthly và phân chia 2 khung Bracket rõ ràng: **14 ngày** (cho chiến dịch tìm kiếm tập trung) và **12 tháng** (cho chu kỳ hợp đồng cư trú).
* **Bổ sung Counter-metrics bắt buộc:** Tôi chủ động bổ sung thêm 2 Counter-metrics (`deposit_refund_request_rate` và `handover_dispute_rate`) để làm chiếc phanh an toàn, ngăn chặn việc thuật toán hoặc sale đẩy nhanh số lượng cọc bất chấp sự hài lòng của khách hàng.
