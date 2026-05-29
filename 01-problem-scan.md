# Lab 02 — Worksheet: AI Product Scoping (Vin Smart Future)

---

## 🏛️ 1. Bối cảnh thực tế: Vin Smart Future (Vingroup)

**Vingroup** — Tập đoàn tư nhân lớn nhất Việt Nam — vừa sáp nhập toàn bộ các phòng ban công nghệ thuộc các công ty thành viên thành một đơn vị công nghệ thống nhất mang tên **Vin Smart Future**. 

Nhiệm vụ của **Vin Smart Future** là xây dựng các giải pháp AI, số hóa, và tự động hóa cốt lõi để nâng cao hiệu suất vận hành và trải nghiệm khách hàng xuyên suốt các công ty thành viên:
* 🚗 **VinFast:** Hệ thống xe điện thông minh (EV), trợ lý AI ảo trong xe, dự đoán bảo trì pin, và quản lý chuỗi cung ứng sản xuất.
* 🚕 **Xanh SM (GSM):** Vận hành đội xe taxi/xe máy điện thông minh, điều vận thông minh (Smart Dispatching), tối ưu hóa lộ trình di chuyển.
* 🏢 **Vinhomes:** Quản lý đô thị thông minh (Smart Cities), trợ lý cư dân thông minh, tối ưu hóa mức tiêu thụ năng lượng.
* 🏥 **Vinmec:** Y tế thông minh, chẩn đoán hình ảnh bằng AI, tối ưu hóa quản lý hồ sơ bệnh án.
* 🎢 **Vinpearl / VinWonders:** Trải nghiệm du lịch số hóa, quản lý phòng và luồng khách thông minh tại các khu vui chơi.

Trong buổi Lab hôm nay, nhóm của bạn sẽ đóng vai trò là **AI Product Engineer** tại **Vin Smart Future**, tiến hành tìm kiếm, scoping, phân tích độ khả thi, thiết lập ranh giới vận hành, và xây dựng một **bản mẫu kỹ thuật (prompt prototype)** cho một bài toán cụ thể thuộc một trong những mảng kinh doanh trên.

# 🔍 Phase 1 — SCAN (Cá nhân, 20 min)

### 4 Lenses tìm bài toán AI cho Vingroup:
1. **Lặp lại (Repetitive):** Tác vụ lặp đi lặp lại nhiều lần hằng ngày. (Ví dụ: So khớp hóa đơn sạc điện tại VinFast, route lại chuyến taxi tại Xanh SM).
2. **Tốn thời gian (Time-consuming):** Tác vụ ngốn thời gian xử lý thủ công của nhân viên. (Ví dụ: Soạn thảo phản hồi đánh giá 1-star của cư dân Vinhomes).
3. **AI có thể tốt hơn (AI-upgrade):** Dịch vụ khách hàng hiện tại còn chậm hoặc phản hồi rập khuôn. (Ví dụ: Chatbot CSKH Vinpearl hỗ trợ đặt vé vui chơi).
4. **Pain từ người khác (Stakeholder Pain):** Bottleneck khiến khách hàng hoặc nhân viên thực địa phàn nàn. (Ví dụ: Tài xế Xanh SM phàn nàn về việc hệ thống gợi ý điểm đón khách không chính xác).

### 📝 List bài toán của tôi:
| # | Subsidiary (VinFast/Xanh SM...) | Lens | Mô tả ngắn bài toán |
|---|----------------------------------|------|---------------------|
| 1 | Vinhomes | Tốn thời gian | Hàng tháng, Ban quản lý phải kiểm tra thủ công số liệu điện, nước, phí dịch vụ từ các đồng hồ điện tổng và đồng hồ căn hộ để phát hành thông báo phí. Việc này dễ sai sót do nhập liệu thủ công hoặc không phát hiện ra rò rỉ đường ống, câu trộm năng lượng ngầm.  |
| 2 | Vinhomes | Lặp lại | Lực lượng bảo vệ phải liên tục đi tuần tra hoặc nhìn màn hình camera để bắt các lỗi: đỗ xe sai quy định dưới lòng đường, lấn chiếm hành lang thoát hiểm, đổ rác sai nơi quy định. |
| 3 | VinMec | Tốn thời gian | Việc điều phối phòng mổ và xếp giường bệnh (phòng đơn, phòng đôi, phòng cách ly) hiện đang làm thủ công trên bảng Excel hoặc hệ thống cơ bản theo nguyên tắc "ai đến trước xếp trước", chưa tối ưu theo thời gian. |
| 4 | Xanh SM | Tốn thời gian | Lịch bảo dưỡng xe hiện tại đang làm theo mốc cố định. Nhưng sẽ có nhiều xe sạc nhanh liên tục sẽ có tốc độ chai pin và hao mòn linh kiện khác các xe thông thường. Việc bảo dưỡng "cào bằng" dẫn đến việc xe chưa hỏng cũng vào xưởng, hoặc xe hỏng giữa đường rồi mới kéo về. |
| 5 | Vinhomes | Tốn thời gian | Việc phân bổ kỹ thuật viên sửa chữa điện / nước / thang máy hiện đang làm thủ công qua bộ đàm/group chat, chưa tối ưu việc sắp xếp thời gian.|

---

# 🃏 Phase 2 — QUICK-ASSESS (Cá nhân, 30 min)

Chọn **top 3 bài toán** từ danh sách trên và hoàn thiện **3 Quick Problem Cards** dưới đây (10 phút/card).

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                       │
│                                                             │
│ Bài toán: Kiểm tra và phát hiện bất thường trong hóa đơn    │
│ số liệu điện, nước, phí dịch vụ căn hộ định kỳ hàng tháng.  │
│ Công ty thành viên: [x] Vinhomes                            │
│                                                             │
│ Ai đang đau? Kế toán Ban quản lý, Cư dân                    │
│                                                             │
│ Workflow thủ công hiện tại (5 bước):                        │
│   1. Đội kỹ thuật chốt số và nhập liệu thủ công từ các      │
│      đồng hồ (meter) tổng và đồng hồ căn hộ lên hệ thống    │
│   → 2. Kế toán chạy script đối chiếu chênh lệch giữa lượng  │
│      nước tiêu thụ tổng và tổng các căn hộ                  │
│   → 3. Rà soát thủ công các căn hộ có chỉ số tăng đột biến   │
│   → 4. Cử kỹ thuật đi kiểm tra thực địa (nghi rò rỉ/câu trộm)│
│   → 5. Chốt số liệu, xuất hóa đơn thủ công gửi lên App      │
│                                                             │
│ Bước nào tốn nhất? Bước 2-3-4 ( 5-7 ngày làm việc/tháng)  │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2-3              │
│ (Anomaly Detection tự động phát hiện rò rỉ/sai số tức thời) │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ - Giảm thời gian đối soát tháng từ 5 ngày ──> dưới 2 tiếng. │
│ - Giảm tỷ lệ thất thoát nước ngầm/câu trộm từ 5% ──> dưới 1%│
│                                                             │
│ Quick Architecture: [x] Rule                                │
└─────────────────────────────────────────────────────────────┘
```
```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                       │
│                                                             │
│ Bài toán: Giám sát an ninh ảo phát hiện lấn chiếm không     │
│ gian chung, đổ rác sai quy định và đỗ xe sai vị trí.        │
│ Công ty thành viên: [x] Vinhomes                            │
│                                                             │
│ Ai đang đau? Đội ngũ an ninh (mỏi mắt/quá tải), Cư dân      │
│                                                             │
│ Workflow thủ công hiện tại (5 bước):                        │
│   1. Bảo vệ liên tục đi tuần tra cơ học bám địa bàn nội khu │
│   → 2. Nhân sự trực sảnh nhìn thủ công hàng trăm màn CCTV   │
│   → 3. Phát hiện vi phạm (đỗ sai xe, lấn chiếm hành lang)   │
│   → 4. Dùng bộ đàm điều phối bảo vệ cơ động đến hiện trường │
│   → 5. Lập biên bản giấy, chụp ảnh lưu chứng cứ thủ công    │
│                                                             │
│ Bước nào tốn nhất? Bước 1-2 (Chiếm 40% thời gian ca trực)   │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2-3-4            │
│ (Computer Vision tự động nhận diện vi phạm & alert tự động) │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                        │
│ - Tỷ lệ phát hiện vi phạm tăng từ 30% ──> trên 95%.         │
│ - Thời gian từ lúc vi phạm đến lúc cảnh báo: < 30 giây.     │
│                                                             │
│ Quick Architecture: [x] Agent                               │
└─────────────────────────────────────────────────────────────┘
```
```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                       │
│                                                             │
│ Bài toán: Tối ưu hóa phân bổ phòng mổ và xếp giường bệnh    │
│ nội trú động (phòng đơn, đôi, cách ly) theo thời gian thực. │
│ Công ty thành viên: [x] Vinmec                              │
│                                                             │
│ Ai đang đau? Điều dưỡng trưởng, Bác sĩ phẫu thuật, Bệnh nhân│
│                                                             │
│ Workflow thủ công hiện tại (5 bước):                        │
│   1. Nhận yêu cầu nhập viện/lịch mổ từ các khoa lâm sàng    │
│   → 2. Điều dưỡng trưởng check thủ công bảng Excel/HIS để   │
│      tìm phòng trống phù hợp (đơn/đôi/cách ly)              │
│   → 3. Gọi điện/Chat đối chiếu lịch trống của ekip mổ       │
│   → 4. Sắp xếp thủ công theo nguyên tắc "ai đến trước xếp   │
│      trước", không tối ưu được thời gian xuất viện dự kiến │
│   → 5. Cập nhật lại trạng thái giường lên bảng theo dõi     │
│                                                             │
│ Bước nào tốn nhất? Bước 2-3-4 ( 30-45 phút/ca điều phối)   │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2-3-4            │
│ (Thuật toán tối ưu tổ hợp kết hợp học máy dự đoán downtime) │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                        │
│ - Giảm tỷ lệ lãng phí công suất phòng mổ từ 15% ──> < 5%.   │
│ - Giảm thời gian chờ đợi xếp giường của bệnh nhân: > 40%.   │
│                                                             │
│ Quick Architecture: [x] Rule                               │
└─────────────────────────────────────────────────────────────┘
```