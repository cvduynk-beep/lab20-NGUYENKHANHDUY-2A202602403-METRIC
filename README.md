# BÀI LAB DAY 20: PRODUCT METRICS — RETENTION & ENGAGEMENT
**Khóa học:** VinUni AI20K — Build Phase Cohort 4 (Track 1)  
**Ngày thực hiện:** 06/10/2026

---

## 1. THÔNG TIN HỌC VIÊN & ĐỀ ÁN

* **Họ và tên:** Nguyễn Khánh Duy
* **Mã học viên (MHV):** `2A202602403`
* **Dự án thực hiện:** **VinStay AI** (Đề án Nhóm P-010) — Hệ điều hành cho thuê & vận hành căn hộ nội khu Vinhomes Ocean Park (Gia Lâm, Hà Nội).
* **Use case phân tích chuyên sâu:** Khách thuê tìm kiếm, thẩm định chi phí All-in và khóa căn giữ chỗ trực tuyến (`Tenant All-in Cost Discovery & Instant Unit Holding`).
* **Kho lưu trữ GitHub:** [lab20-NGUYENKHANHDUY-2A202602403-METRIC](https://github.com/cvduynk-beep/lab20-NGUYENKHANHDUY-2A202602403-METRIC)
* **Liên kết tệp Metrics Pack chính thức:** [METRICS_PACK.md](./METRICS_PACK.md) (Xem trực tiếp trong repo)
* **Nhật ký sử dụng AI:** [ai-support-log.md](./ai-support-log.md)

---

## 2. CẤU TRÚC HỒ SƠ NỘP BÀI (METRICS PACK)

Tệp bài làm chi tiết [`METRICS_PACK.md`](./METRICS_PACK.md) được xây dựng xuyên suốt theo chuỗi quyết định logic của Day 20:

$$\text{Core Action} \longrightarrow \text{Nhịp tự nhiên (Nature)} \longrightarrow \text{Bộ Metric + Retention} \longrightarrow \text{Product Loop (Giả thuyết)} \longrightarrow \text{Tracking (Phép thử)}$$

Hồ sơ bao gồm đầy đủ 7 hạng mục bắt buộc và vượt qua 5 Gates đánh giá:
* **Mục 00 — Chốt phạm vi:** Định vị dự án VinStay AI, chân dung Persona (Nguyễn Minh Anh - 24 tuổi) và Core job bằng ngôn từ của người dùng.
* **Mục 01 — Core Action Card:** Phân biệt 4 khái niệm, đặc tả Core Action (*Quét VietQR cọc 2.000.000đ khóa căn 24h*), vượt qua 5/5 tiêu chí tự kiểm (**GATE 1: ĐẠT**).
* **Mục 02 — Action Nature Card & Kết luận Cadence:** Phân tích bản chất hành vi, xác lập nhịp đo tự nhiên không ép Daily habit (**GATE 2: ĐẠT**).
* **Mục 03 — Metric System:** Hệ thống chỉ số Activation (Start, Event, Window 72h), Engagement (Frequency, Depth), North Star Metric (3 thành phần), 3 Leading indicators và 2 Counter-metrics rủi ro (**GATE 3: ĐẠT**).
* **Mục 04 — Retention Definition:** Định nghĩa chuẩn 6 thành phần của Retention, khớp hoàn toàn với nhịp tự nhiên của sản phẩm cho thuê bất động sản.
* **Mục 05 — Product Loop:** Thiết kế vòng lặp sản phẩm 2 chu kỳ (Tiến trình thuê & Giới thiệu cư dân), gắn Metric hypothesis đo lường độ tăng trưởng (**GATE 4: ĐẠT**).
* **Mục 06 — Tracking nhanh:** Bảng 6 Core Events chuẩn cú pháp `object_action`, 2 Tiêu chí nghiệm thu (Acceptance Criteria) chống bắn event sớm và chống trùng lặp.
* **Mục 07 — Tự soi lỗi kinh điển & Revision:** Vượt qua bảng 7 câu hỏi tự soi, giải trình lý do giữ vững nguyên tắc sản phẩm (**GATE 5: ĐẠT**).

---

## 3. ĐIỀU TÔI MANG VỀ ÁP DỤNG CHO DỰ ÁN THẬT (KEY TAKEAWAYS)

Qua bài Lab Day 20, ba đúc kết sâu sắc nhất tôi đem về áp dụng trực tiếp cho việc phát triển sản phẩm **VinStay AI** là:

1. **"Nature trước, Nurture sau" — Tôn trọng nhịp sống thật của người dùng:**  
   Bất động sản cho thuê là sản phẩm có quyết định tài chính lớn và chu kỳ dài hạn (6–12 tháng/hợp đồng). Việc cố ép các chỉ số như DAU hay spam Push Notification để bắt khách mở app hàng ngày chỉ tạo ra "vanity metrics" và làm phiền khách hàng. Nền tảng phải tập trung tối ưu hóa **tốc độ chuyển đổi trong đợt tìm nhà (Burst Cadence 7–14 ngày)** thay vì chạy theo tần suất ảo.

2. **Core Action phải gắn với khoảnh khắc xác nhận giá trị (Value Confirmation), không phải thao tác giao diện:**  
   Trước bài lab này, đội ngũ dễ nhầm lẫn việc khách "tìm kiếm", "bấm xem ảnh" hay "chat với VinStay AI" là thành công. Thực tế, giá trị cốt lõi của VinStay AI chỉ thành hiện thực khi khách hoàn toàn an tâm xuống tiền **Cọc giữ chỗ 2.000.000đ qua VietQR** để khóa căn hộ trong 24h. Đó là thời điểm căn bệnh "tin ảo", "lệch giá All-in" và "sợ bị lừa cọc" được giải quyết triệt để.

3. **Luôn luôn có Counter-metric đi kèm North Star Metric:**  
   Nếu chỉ tối ưu hóa số lượng căn hộ được cọc (NSM), đội ngũ bán hàng và thuật toán có thể đẩy mạnh FOMO hoặc thông tin chưa chuẩn xác để ép khách cọc nhanh. Việc thiết lập Counter-metric **Tỷ lệ yêu cầu hoàn cọc trong 24h (`deposit_refund_request_rate`)** và **Tỷ lệ khiếu nại bàn giao (`handover_dispute_rate`)** là chiếc phanh an toàn bảo vệ uy tín lâu dài của nền tảng.
