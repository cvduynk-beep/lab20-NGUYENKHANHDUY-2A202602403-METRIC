# METRICS PACK: VINSTAY AI
### BẢN ĐẶC TẢ HỆ THỐNG CHỈ SỐ SẢN PHẨM — RETENTION & ENGAGEMENT
* **Đề án:** **VinStay AI** — Hệ Điều Hành Cho Thuê & Vận Hành Căn Hộ Vinhomes Ocean Park (Team P-010)
* **Học viên:** Nguyễn Khánh Duy — **Mã học viên (MHV):** `2A202602403`
* **Lớp:** AI20K Track 1 — Day 20 Lab

---

## 00 — DỰ ÁN, PERSONA, CORE JOB

### 1. Dự án
**VinStay AI** — Nền tảng PropTech hai đầu (Two-Sided Platform) tích hợp mạng lưới Field Host nội khu, số hóa quy trình tìm kiếm, thẩm định chi phí All-in, đặt lịch xem phòng thực tế và khóa căn tức thì cho thị trường căn hộ chung cư tại Vinhomes Ocean Park (Gia Lâm, Hà Nội).

### 2. Persona
* **Chân dung đại diện:** **Nguyễn Minh Anh**, 24 tuổi, chuyên viên phân tích dữ liệu mới chuyển nơi làm việc sang bờ Đông Hà Nội (Ocean Park), sống độc thân.
* **Đặc điểm hành vi & tâm lý:**
  * Thu nhập ổn định: 18 – 20 triệu VNĐ/tháng.
  * Ngân sách thuê tối đa (Trần cứng): **7.000.000 VNĐ/tháng**.
  * Rất dị ứng với tin đăng ảo trên Facebook/Môi giới tự do, sợ nhất việc xem phòng thì giá 6 triệu nhưng vào ở lại gánh thêm phí quản lý Vinhomes (8–11k/m²), phí gửi xe máy/ô tô, tiền điện nước giá kinh doanh đẩy tổng chi phí lên 8.5 – 9 triệu/tháng.
  * Rất bận rộn trong tuần, ngại việc phải đi lại nhiều chuyến sang Gia Lâm để xem phòng nếu không chắc chắn phòng đó còn trống và có thật.

### 3. Core Job
> *"Tôi muốn tìm và chốt được một căn hộ đúng thực tế, minh bạch toàn bộ chi phí All-in trong ngân sách 7 triệu mà không mất công đi lại nhiều lần và không lo bị lừa tiền cọc."*

*(Viết bằng ngôn từ người dùng, xuất phát từ nỗi đau thực tế: trần ngân sách All-in, ghét tin ảo, sợ mất tiền cọc).*

---

## 01 — CORE ACTION CARD & TỰ KIỂM 5 TIÊU CHÍ

### 1. Phân biệt 4 khái niệm cốt lõi (Bảng phân biệt)

| Khái niệm | Câu hỏi trọng tâm | Trả lời cho VinStay AI (Khách thuê) |
| :--- | :--- | :--- |
| **Core Job** | User đang cố hoàn thành việc gì? | Thuê được căn hộ phù hợp ngân sách All-in thật, an toàn, không lo tin ảo. |
| **Core Action** | User làm gì trong sản phẩm để tiến tới giá trị? | Quét mã VietQR chuyển cọc 2.000.000đ để khóa giữ chỗ căn hộ trong 24 giờ. |
| **Core Value** | User nhận được lợi ích gì? | Giữ chắc quyền ưu tiên thuê căn hộ ưng ý đúng giá niêm yết All-in, được đảm bảo quyền lợi pháp lý và hoàn cọc 100% nếu phát hiện sai lệch. |
| **Core Value Event** | Sự kiện nào chứng minh value đã xảy ra? | `holding_deposit_locked` (Hệ thống xác nhận tiền cọc vào tài khoản ký quỹ thành công, khóa trạng thái căn sang `HOLDING_DEPOSIT`). |

> **Phân tích chiều sâu:** Bấm "Tìm kiếm" hay "Hỏi AI tư vấn" chỉ là thao tác giao diện (`UI Interaction`). Danh sách căn hộ gợi ý chỉ là kết quả hệ thống (`System Output`). Thậm chí việc bấm nút "Đặt lịch xem" cũng chỉ là bước đệm. Giá trị cốt lõi giải quyết triệt để nỗi đau của khách thuê (sợ mất căn hời, sợ bị hớt tay trên) chỉ xảy ra khi khách **chuyển tiền cọc giữ chỗ 2.000.000đ qua VietQR**.

### 2. Điền Core Action Card

| Thành phần | Đặc tả của VinStay AI |
| :--- | :--- |
| **Target user** | Khách thuê tiềm năng (`Tenant`) đã xác thực số điện thoại bằng OTP và đã trải nghiệm xem phòng thực tế với Field Host (hoặc xem qua Virtual Tour 360). |
| **Core job** | Khóa quyền ưu tiên thuê căn hộ đã chọn trước các khách thuê khác trong vòng 24 giờ. |
| **Core action** | Quét mã VietQR động để chuyển 2.000.000 VNĐ cọc giữ chỗ cho căn hộ mục tiêu. |
| **Object** | Căn hộ cụ thể (`Unit ID`) đang ở trạng thái `AVAILABLE` trên hệ thống. |
| **Preconditions** | Căn hộ đã qua kiểm định 32 hạng mục (`VERIFIED`), khách đã xác thực OTP SĐT, và đã đồng ý với "Quy chế Ký quỹ Giữ chỗ & Nguyên tắc First-to-pay Wins". |
| **Completion rule** | Giao dịch ngân hàng thành công qua cổng VietQR, Webhook hệ thống nhận tín hiệu gạch nợ trong vòng 60 giây, căn hộ tự động chuyển trạng thái từ `AVAILABLE` sang `HOLDING_DEPOSIT` và bắt đầu đếm ngược 24h. |
| **Core value** | Bảo đảm 100% quyền giữ chỗ độc quyền trong 24h để hoàn tất hợp đồng thuê, không lo bị môi giới khác tranh cướp căn, không lo chi phí ẩn phát sinh. |
| **Evidence of value** | Khách thuê dừng tìm kiếm các căn hộ khác trong 24h tiếp theo; tiến hành upload ảnh CCCD để thực hiện eKYC ký hợp đồng. |
| **Candidate event** | `holding_deposit_locked` (hoặc `unit_deposit_locked`). |

### 3. Tự kiểm 5 tiêu chí (Evaluation Gate 1)
1. **Gần Core Value:** **ĐẠT** — Khi cọc giữ chỗ thành công, khách thuê đạt được 90% chặng đường sở hữu quyền thuê căn hộ, loại bỏ hoàn toàn rủi ro bị mất căn hộ giá tốt.
2. **Có thể lặp lại:** **ĐẠT** — Hành vi lặp lại khi khách hết hạn hợp đồng thuê (sau 6–12 tháng), hoặc khi có nhu cầu đổi phân khu (từ S1 sang S2), hoặc hỗ trợ bạn bè cùng cọc.
3. **Có thể quan sát:** **ĐẠT** — Quan sát chính xác 100% thông qua Webhook đối soát biến động số dư ngân hàng và chuyển đổi trạng thái bản ghi `Unit` trong Database.
4. **Có ý nghĩa:** **ĐẠT** — Số lượng cọc giữ chỗ tăng đồng nghĩa với việc khách hàng tìm thấy căn hộ vừa ý thực sự, và căn hộ trống của chủ nhà được thanh khoản.
5. **Có thể tác động:** **ĐẠT** — Đội ngũ sản phẩm có thể tối ưu giao diện All-in Cost, thuật toán Dynamic Pricing gợi ý căn hời, và thời gian điều phối Field Host để thúc đẩy tỷ lệ cọc.

> 🏁 **GATE 1 — Core action đứng vững: ĐẠT (5/5 tiêu chí).**  
> Core action có đầy đủ Actor (`Tenant`), Object (`Unit`), Completion Rule (`Webhook Bank xác nhận gạch nợ`); hoàn toàn tách biệt khỏi thao tác giao diện ("lướt xem", "chat AI").

---

## 02 — ACTION NATURE CARD & KẾT LUẬN CADENCE

### 1. Action Nature Card

| Thành phần | Phân tích bản chất hành vi |
| :--- | :--- |
| **Actor** | Khách thuê cá nhân (`Tenant Account`). |
| **Intent** | Quyết định xác lập quyền giữ chỗ sau khi đã so sánh All-in Cost và kiểm chứng chất lượng phòng thực tế qua buổi tiếp đón của Field Host. |
| **Trigger** | Sự kiện bên ngoài & Thực tế: Khách vừa kết thúc buổi xem thực tế, chứng kiến căn hộ đẹp đúng mô tả và phân khu có nhu cầu cao (sợ bị người khác cọc trước). |
| **Effort** | Rất cao về mặt tâm lý và tài chính (xuống tiền 2.000.000 VNĐ), nhưng cực thấp về mặt thao tác kỹ thuật (quét mã VietQR trên app ngân hàng mất 15 giây). |
| **Value timing** | Giá trị xuất hiện tức thì: ngay khi chuyển khoản thành công, căn hộ đổi trạng thái `HOLDING` trên toàn hệ thống, bảo vệ khách độc quyền trong 24 giờ. |
| **State** | Căn hộ chuyển sang `HOLDING_DEPOSIT`, sinh mã hợp đồng nháp, lưu vết mã giao dịch ngân hàng (`transaction_ref`). |
| **Dependency** | Phụ thuộc vào việc căn hộ còn đang mở (`AVAILABLE`), và buổi tiếp đón của Field Host diễn ra suôn sẻ, đúng giờ. |
| **Repeat condition** | Xuất hiện lại khi khách hết hợp đồng thuê 6–12 tháng hoặc khi bạn bè/người quen cần tìm phòng nhờ thuê hộ. |

### 2. Kết luận Cadence (Nhịp đo tự nhiên)
* **Dạng hành vi:** **Theo chu kỳ dài hạn (Cyclical)** trong vòng đời người thuê nhà, nhưng mang tính chất **Tập trung cao độ (Burst Activity)** trong vòng 7 – 14 ngày khi đang có nhu cầu chuyển nhà.
* **Kết luận theo template chuẩn:**
  > *"Đối với **khách thuê căn hộ (Tenant)**, core action **quét VietQR cọc 2.000.000đ giữ chỗ căn hộ** thường xuất hiện **6 đến 12 tháng một lần** (hoặc lặp lại 1–2 lần trong chiến dịch tìm nhà 14 ngày) vì **thuê nhà là nhu cầu cư trú trung và dài hạn có tính chu kỳ cố định theo hợp đồng**. Do đó, nhịp đo phù hợp là **Monthly / Cohort 30–60 ngày (đối với phễu chuyển đổi) và 12 tháng (đối với chu kỳ tái ký/gia hạn)** ở cấp **User (Tenant)**."*

* **Cân nhắc chuyên sâu:**
  * Tuyệt đối không ép dùng Daily hay Weekly Dashboard cho hành vi cọc nhà. Không người thuê bình thường nào cọc nhà mỗi tuần.
  * Trong sản phẩm AI và PropTech, việc khách chốt cọc nhanh hơn (chỉ sau 1–2 lần xem thay vì 10 lần xem) là bằng chứng cho thấy sản phẩm hiệu quả hơn, chứ không phải dùng lâu hơn là tốt hơn.

> 🏁 **GATE 2 — Cadence từ nature, không từ dashboard: ĐẠT.**  
> Đã chứng minh được tần suất tự nhiên xuất phát từ bản chất đời thật của người thuê nhà, không chạy theo DAU ảo.

---

## 03 — METRIC SYSTEM

### 1. Activation Metric (Thời điểm chạm First Value)
* **Start event:** `viewing_scheduled` (Khách xác thực SĐT OTP và đặt lịch xem căn hộ đầu tiên).
* **Activation event:** `viewing_completed` (Khách và Field Host hoàn thành buổi xem thực địa tại căn hộ — thời điểm khách trực tiếp kiểm chứng căn hộ có thật, không phải tin ảo, và đối chiếu bảng All-in Cost).
* **Time window:** Trong vòng **72 giờ** kể từ khi `viewing_scheduled`.
* *Lưu ý tránh bẫy:* Không xem việc "đăng nhập tài khoản" hay "hoàn thành tour onboarding giới thiệu app" là Activation.

### 2. Engagement Metric (2 góc đo)
* **Frequency (trong chiến dịch tìm nhà 14 ngày):** Số lượt xem căn hộ thực địa hoàn tất / active tenant (`viewings_per_active_tenant`). Mức lành mạnh: 2 – 3 căn/chiến dịch trước khi cọc.
* **Depth (Chất lượng quyết định):** Tỷ lệ chuyển đổi từ xem thực tế sang cọc giữ chỗ (`viewing_to_deposit_conversion_rate` = Tổng số `holding_deposit_locked` / Tổng số `viewing_completed`).

### 3. North Star Metric (NSM)
Được cấu thành chính xác theo công thức 3 thành phần:
$$\text{NSM} = \text{Unit of Value} + \text{Quality Threshold} + \text{Frequency}$$

$$\mathbf{NSM} = \text{Số lượng căn hộ được cọc giữ chỗ All-in thành công không phát sinh khiếu nại mỗi tháng}$$

* **Unit of Value:** Căn hộ được cọc giữ chỗ thành công (`holding_deposit_locked`).
* **Quality Threshold:** Tỷ lệ khiếu nại về sai lệch chi phí ẩn bằng 0% (Khách xác nhận tổng chi phí trùng khớp 100% với bảng All-in Cost).
* **Frequency:** Tính theo Tháng (Monthly).

### 4. Leading Indicators (Chỉ số dự báo sớm — Tối đa 3 chỉ số)
1. **Tỷ lệ khách mở và tương tác với Bảng phân rã chi phí All-in Cost (`allin_cost_engaged_rate`):**
   * *Lý do tin cậy:* Khách hiểu cặn kẽ các khoản phí BQL, tiền xe, điện nước trước khi xem sẽ có tâm lý sẵn sàng xuống tiền cọc cao gấp 3 lần so với khách chỉ nhìn giá thuê gốc.
2. **Tỷ lệ buổi xem phòng được Field Host đón tiếp đúng giờ $\le 15$ phút (`host_on_time_arrival_rate`):**
   * *Lý do tin cậy:* Trải nghiệm tiếp đón tại sảnh chuyên nghiệp, mở cửa đúng hẹn là yếu tố quyết định tạo dựng niềm tin pháp lý ngay tại chỗ.
3. **Tỷ lệ căn hộ hiển thị huy hiệu "Căn hời phân khu" (PCS Rank $\ge 10\%$ rẻ hơn thị trường) trong kết quả tìm kiếm:**
   * *Lý do tin cậy:* Mức giá cạnh tranh kích hoạt quy chế "First-to-pay Wins" thúc đẩy khách ra quyết định cọc ngay trong 2 giờ sau khi xem phòng.

### 5. Counter-metrics (Chỉ số kiểm soát rủi ro)
1. **Tỷ lệ yêu cầu hoàn cọc trong 24 giờ (`deposit_refund_request_rate`):**
   * *Mục đích:* Ngăn chặn việc Field Host hoặc giao diện tạo cảm giác FOMO ảo ép khách cọc rồi khách hối hận rút lui. Ngưỡng cảnh báo: $> 5\%$.
2. **Tỷ lệ tranh chấp bàn giao (`handover_dispute_rate`):**
   * *Mục đích:* Ngăn chặn việc cọc nhanh nhưng khi bàn giao căn hộ thực tế không khớp với 32 tiêu chí kiểm định đã cam kết trên hệ thống. Ngưỡng mục tiêu: $< 1\%$.

> 🏁 **GATE 3 — Metric tính được, retention đủ nghĩa: ĐẠT.**  
> Activation có start/event/window chuẩn mực; NSM tuân thủ nghiêm ngặt công thức 3 thành phần; có đầy đủ Leading Indicators và Counter-metrics bảo vệ trải nghiệm khách hàng.

---

## 04 — RETENTION DEFINITION (ĐỦ 6 THÀNH PHẦN)

### 1. Bảng đặc tả 6 thành phần Retention

| Thành phần | Định nghĩa chi tiết cho VinStay AI |
| :--- | :--- |
| **1. Unit** | Khách thuê cá nhân (`Tenant Account`). |
| **2. Cohort Entry** | Sự kiện hoàn thành buổi xem phòng đầu tiên trong tháng $M$ (`first_viewing_completed`). |
| **3. Return Event** | Thực hiện cọc giữ chỗ thành công (`holding_deposit_locked`) HOẶC Tái ký hợp đồng / Cọc căn mới (`lease_renewed` / `subsequent_deposit_locked`). |
| **4. Window** | **Bracket 1:** 14 ngày (Đo lường Retention trong chiến dịch tìm nhà).<br>**Bracket 2:** 12 tháng (Đo lường Retention chu kỳ hợp đồng cư trú). |
| **5. Threshold** | Tối thiểu $\ge 1$ lần trong Window xác định. |
| **6. Segment** | Khách thuê mới có nhu cầu chuyển đến sinh sống tại Vinhomes Ocean Park trong kỳ đánh giá. |

### 2. So sánh Retention với 3 mốc chuẩn (Framework S34)
* **So với Natural Cycle:** Hoàn toàn khớp — người thuê nhà không quay lại cọc hàng tuần (như Shopee) hay hàng ngày (như mạng xã hội), mà quay lại khi phát sinh nhu cầu cư trú mới (14 ngày tìm kiếm hoặc 12 tháng hợp đồng).
* **So với Cohort đúng Segment:** Tách riêng Segment "Sinh viên VinUni" (chu kỳ thuê 10 tháng theo năm học) và Segment "Gia đình trẻ / Người đi làm" (chu kỳ thuê 12–24 tháng).
* **So với Benchmark Category (PropTech / Rental Marketplace):** Tỷ lệ chuyển đổi từ xem phòng sang chốt cọc trong 14 ngày đạt benchmark ngành 25–35%; tỷ lệ tái ký hợp đồng sau 1 năm đạt $\ge 60\%$.

---

## 05 — PRODUCT LOOP & METRIC HYPOTHESIS

### 1. Thiết kế Product Loop (2 chu kỳ liên tiếp)
* **Loại loop:** **Progress & Community Referral Loop** (Vòng lặp tiến trình thuê nhà kết hợp mạng lưới cư dân nội khu).
* **Mô hình 2 chu kỳ vận hành:**

```
[CHU KỲ 1: KHÁCH THUÊ CHỐT CĂN]
Nhu cầu chuyển chỗ ở (Natural Trigger)
       │
       ▼
Xem Catalog All-in & Đặt Field Host đón
       │
       ▼
Quét VietQR cọc 2.000.000đ (Core Action)
       │
       ▼
Căn hộ khóa độc quyền 24h, bảo đảm cọc (Immediate Value)
       │
       ▼
eKYC CCCD, ký hợp đồng số, nhận nhà ở (Investment / Saved State)
       │
       ▼
[CHU KỲ 2: LAN TỎA & DUY TRÌ]
Đồng nghiệp / Bạn bè hỏi kinh nghiệm chuyển về Ocean Park (Next Natural Trigger)
       │
       ▼
Gửi link căn All-in kèm mã giảm giá cư dân (Social Trigger / Share)
       │
       ▼
Bạn bè đặt lịch & Cọc giữ chỗ qua VietQR (Repeat Core Action)
       │
       ▼
Cả hai nhận ưu đãi phí gửi xe / dịch vụ BQL (Repeat Value)
```

* **Kiểm tra Reason to return:** Nếu tắt toàn bộ Push Notification, khách vẫn quay lại app vì:
  1. Hợp đồng thuê số và danh mục 32 hạng mục bàn giao (`Digital Handover Passport`) được lưu trữ tại đây, dùng để đối chiếu khi trả phòng.
  2. Nhu cầu chia sẻ kinh nghiệm cho bạn bè cùng công ty/trường học chuyển về Ocean Park để nhận ưu đãi chi phí sinh hoạt.

### 2. Metric Hypothesis (Giả thuyết định lượng)
> *"Nếu vòng lặp **Giới thiệu cư dân nội khu (Community Referral Loop)** này hoạt động, metric **Tỷ lệ cọc giữ chỗ đến từ nguồn giới thiệu tự nhiên (`organic_referral_deposit_rate`)** sẽ tăng từ **8% lên 25%** trong vòng **90 ngày**, vì **cư dân đang sinh sống tại Ocean Park có mức độ thấu hiểu và uy tín cao nhất khi thuyết phục đồng nghiệp/bạn bè chuyển về cùng phân khu**."*

> 🏁 **GATE 4 — Loop nối metric, event nối loop: ĐẠT.**  
> Loop có đủ 2 chu kỳ, không phụ thuộc vào notification rác, có Metric Hypothesis gắn kết trực tiếp với chỉ số tăng trưởng.

---

## 06 — TRACKING NHANH (4–8 CORE EVENTS)

### 1. Bảng danh mục Core Events chuẩn `object_action`

| Tên Event | Ý nghĩa hành vi đại diện | Thời điểm chính xác ghi nhận event | Map về Metric ở Phase 3 |
| :--- | :--- | :--- | :--- |
| `allin_cost_calculated` | Khách mở bảng chi tiết chi phí và hoàn tất việc xem tổng giá All-in. | Khi modal bảng tính chi phí All-in được hiển thị trọn vẹn trên màn hình. | **Leading Indicator 1** |
| `viewing_scheduled` | Khách nhập đúng OTP SĐT và xác nhận lịch hẹn xem phòng với Field Host. | Backend xác thực OTP thành công và sinh mã `booking_id`. | **Activation Start Event** |
| `viewing_completed` | Buổi xem phòng thực tế tại căn hộ kết thúc thành công. | Field Host bấm "Hoàn thành tiếp đón" và khách xác nhận mã 4 số tại sảnh. | **Activation Event** / Engagement |
| `holding_deposit_initiated` | Khách bấm "Khóa căn giữ chỗ" và màn hình hiển thị mã VietQR động. | Khi mã VietQR động 2.000.000 VNĐ được render thành công. | Phễu chuyển đổi Cọc |
| `holding_deposit_locked` | Tiền cọc 2.000.000đ đã vào tài khoản ký quỹ, căn hộ được khóa 24h. | Webhook ngân hàng trả mã `SUCCESS`, Database cập nhật `unit.status = HOLDING`. | **Core Action / North Star Metric** |
| `holding_deposit_refunded` | Tiền cọc được hoàn trả lại cho khách do phát hiện thông tin sai lệch. | Lệnh hoàn tiền qua Napas/Bank được đối soát hoàn tất. | **Counter-metric 1** |

### 2. Tiêu chí nghiệm thu (Acceptance Criteria)

* **Tiêu chí 1 (Hành vi thực sự hoàn tất — True Completion Rule):**  
  Event `holding_deposit_locked` **tuyệt đối không được bắn ra** khi người dùng mới chỉ bấm nút "Xác nhận cọc" hoặc khi mới mở ứng dụng ngân hàng để quét mã QR. Event này **chỉ được kích hoạt duy nhất một lần** sau khi hệ thống Backend nhận được Webhook từ đối tác thanh toán/ngân hàng xác nhận số dư tài khoản ký quỹ tăng đúng `2,000,000 VNĐ` kèm nội dung chuyển khoản hợp lệ.

* **Tiêu chí 2 (Chống trùng lặp & Idempotency):**  
  Mỗi phiên thanh toán cọc được gán một định danh bất biến `deposit_order_id`. Khi người dùng tải lại trang web (reload), mạng gián đoạn thử lại (retry), hoặc hệ thống ngân hàng bắn Webhook lặp lại, hệ thống phải thực hiện kiểm tra khử trùng lặp (Idempotent Check). Không được phép phát sinh thêm event `holding_deposit_locked` thứ hai cho cùng một giao dịch.

### 3. Đối chiếu Metric Definition Contract (7 chuẩn mực)
1. **Event Name:** Tuân thủ 100% định dạng `object_action` bằng chữ thường và dấu gạch dưới (`snake_case`).
2. **Actor:** Luôn ghi nhận kèm `user_id` và vai trò `role: "tenant"`.
3. **Object:** Luôn truyền kèm `unit_id`, `building_id`, `subdivision_code`.
4. **Properties bắt buộc:** `amount: 2000000`, `currency: "VND"`, `payment_method: "vietqr"`, `transaction_ref`.
5. **Timezone:** Chuẩn hóa toàn bộ Timestamp theo chuẩn ISO-8601 UTC (`YYYY-MM-DDTHH:mm:ssZ`).
6. **Điều kiện loại trừ:** Bộ lọc tự động loại trừ các tài khoản Admin, tài khoản Developer (`test_mode = true`), và các IP nội bộ.
7. **Sự đồng thuận:** Đã đối soát logic khớp 100% giữa Schema Backend Prisma (`backend/prisma/schema.prisma`) và Client Tracker (`apps/web`).

---

## 07 — TỰ SOI LỖI KINH ĐIỂN & REVISION (PHASE 5)

### 1. Bảng đối chiếu 7 câu hỏi tự soi lỗi

| STT | Câu hỏi tự soi lỗi | Kết quả | Giải trình chi tiết |
| :---: | :--- | :---: | :--- |
| **1** | Core action có bị nhầm thành thao tác giao diện hay output hệ thống? | **SẠCH LỖI** | Core action là *Chuyển tiền cọc VietQR 2.000.000đ*, không phải "lướt xem căn" hay "AI trả lời gợi ý". |
| **2** | Activation có bị nhầm thành "xem hết hướng dẫn" hay "đăng nhập"? | **SẠCH LỖI** | Activation là *Hoàn thành buổi xem phòng thực tế với Field Host* (`viewing_completed`), nơi khách trực tiếp nhận First Value. |
| **3** | Frequency có bị ép cao hơn nhu cầu thật của người dùng? | **SẠCH LỖI** | Nhịp đo đặt theo Monthly / 14 ngày tìm nhà / 12 tháng hợp đồng, kiên quyết từ chối ép DAU/WAU cho sản phẩm bất động sản. |
| **4** | Loop có Reason to return tự nhiên ngoài Notification không? | **SẠCH LỖI** | Khách quay lại vì tài liệu bàn giao căn hộ 32 hạng mục được lưu trong app và nhu cầu giới thiệu bạn bè nhận ưu đãi. |
| **5** | Retention có bị dùng chung một window máy móc (như D7)? | **SẠCH LỖI** | Sử dụng 2 khung Bracket: 14 ngày (giai đoạn tìm phòng) và 12 tháng (giai đoạn cư trú/tái ký). |
| **6** | Mọi event trong bảng có đều map về một metric không? | **SẠCH LỖI** | Toàn bộ 6 events đều map trực tiếp về Activation, Engagement, NSM hoặc Counter-metrics. |
| **7** | Metric nào cũng có event để tính toán? | **SẠCH LỖI** | Không có bất kỳ metric nào bị "bỏ lửng" thiếu nguồn dữ liệu event tương ứng. |

### 2. Phần Revision (Ghi nhận cải tiến quan trọng)
* **Quyết định giữ nguyên "phá rule":** Không áp dụng chỉ số DAU (Daily Active Users) hay WAU (Weekly Active Users) làm chỉ số chính cho VinStay AI dù đây là chỉ số phổ biến trên các dashboard mặc định.  
* **Lý do căn bản:** Việc người thuê nhà mở app hàng ngày không đồng nghĩa với việc sản phẩm tốt hơn; ngược lại, việc khách hàng **phải mở app nhiều ngày liền mà không chốt được phòng** là dấu hiệu của việc thuật toán định giá kém và giỏ hàng không chất lượng. VinStay AI đo lường hiệu quả bằng **thời gian từ lúc tìm kiếm đến lúc khóa căn thành công (Time-to-Deposit $\le 7$ ngày)**.

> 🏁 **GATE 5 — Bài sạch lỗi kinh điển: ĐẠT.**  
> Hồ sơ hoàn tất chuỗi logic xuyên suốt: Core action vững $\to$ Cadence tự nhiên $\to$ Metric tính được $\to$ Loop có giả thuyết $\to$ Tracking có kiểm chứng.
