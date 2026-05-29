# 🔍 Phase 1 — SCAN: Tìm kiếm cơ hội (Cá nhân)

Dùng **4 Lenses** quét qua vận hành của các công ty thành viên Vingroup.

| #   | Subsidiary   | Lens               | Mô tả ngắn bài toán                                                                                                           |
| --- | ------------ | ------------------ | ----------------------------------------------------------------------------------------------------------------------------- |
| 1   | **Vinhomes** | AI-upgrade         | AI sàng lọc phản ánh cư dân: hiểu nội dung mơ hồ, đánh giá khẩn cấp, phát hiện thiếu thông tin, gom cụm sự cố và ưu tiên SLA. |
| 2   | **Vinhomes** | Tốn thời gian      | CSKH phải tổng hợp nội dung nhiều phản ánh trùng lặp để gửi báo cáo hằng ngày cho ban vận hành.                               |
| 3   | **VinFast**  | AI-upgrade         | Tự động gợi ý lịch sạc tối ưu và trạm sạc phù hợp loại cổng dựa trên lịch di chuyển của xe.                                   |
| 4   | **Vinmec**   | Pain từ người khác | Điều dưỡng nhập tay tóm tắt đơn thuốc và dặn dò sau khám từ ghi chú bác sĩ (mất 15-20 phút/ca).                               |
| 5   | **Vinpearl** | Tốn thời gian      | Đọc email đặt phòng đoàn và trích xuất yêu cầu (số phòng, ngày, dịch vụ) để tạo booking thủ công.                             |
| 6   | **Xanh SM**  | Lặp lại            | Đối soát khiếu nại giá cước: tổng đài tra log chuyến, map giá, và giải thích thủ công cho khách.                              |

# 🃏 Phase 2 — QUICK-ASSESS (Cá nhân, 30 min)

Chọn top 3 từ danh sách SCAN: **#1 (Vinhomes phản ánh cư dân), #5 (Vinpearl email booking), #4 (Vinmec tóm tắt đơn thuốc).**

## Thẻ bài toán tiêu biểu: Card #1 — Vinhomes triage phản ánh cư dân

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                       │
│                                                             │
│ Bài toán: AI sàng lọc phản ánh cư dân để hiểu nội dung mơ hồ, │
│ đánh giá mức khẩn cấp, phát hiện thiếu thông tin và ưu tiên │
│ SLA trước khi chuyển ban quản lý.                           │
│ Công ty thành viên: [x] Vinhomes                            │
│                                                             │
│ Ai đang đau? CSKH (quá tải), Ban quản lý (trễ SLA)          │
│                                                             │
│ Workflow thủ công hiện tại (4 bước):                        │
│   1. Cư dân gửi phản ánh qua App                             │
│   → 2. CSKH đọc, xác định mức khẩn cấp/thiếu thông tin       │
│   → 3. Chuyển tiếp đến ban quản lý/tòa                       │
│   → 4. Theo dõi SLA và cập nhật trạng thái                   │
│                                                             │
│ Bước nào tốn nhất? Bước 2 (⏱ 8 phút/lượt)                    │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2-3              │
│ (Sàng lọc khẩn cấp -> phát hiện thiếu info -> gợi ý route)    │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                        │
│ Giảm First Response Time từ 30 phút -> dưới 5 phút;         │
│ giảm ticket thiếu thông tin từ 25% -> 10%; giảm SLA trễ 40%.│
│                                                             │
│ Quick Architecture: [x] LLM Feature (Triage + SLA assist)   │
└─────────────────────────────────────────────────────────────┘
```

## Thẻ bài toán tiêu biểu: Card #2 — Vinpearl trích xuất booking đoàn

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                       │
│                                                             │
│ Bài toán: Đọc email đặt phòng đoàn và trích xuất yêu cầu    │
│ (số phòng, ngày, dịch vụ) để tạo booking sơ bộ.             │
│ Công ty thành viên: [x] Vinpearl                            │
│                                                             │
│ Ai đang đau? Sales/Reservation (quá tải mùa cao điểm)       │
│                                                             │
│ Workflow thủ công hiện tại (4 bước):                        │
│   1. Nhận email đặt phòng đoàn                               │
│   → 2. Đọc nội dung và trích xuất yêu cầu                    │
│   → 3. Kiểm tra phòng trống                                  │
│   → 4. Tạo booking sơ bộ/quote                               │
│                                                             │
│ Bước nào tốn nhất? Bước 2 (⏱ 12 phút/email)                  │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2                │
│ (Trích xuất + chuẩn hóa trường dữ liệu)                     │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                        │
│ 90% email trích xuất đúng trong < 2 phút.                   │
│                                                             │
│ Quick Architecture: [x] LLM Feature (Information extraction)│
└─────────────────────────────────────────────────────────────┘
```

## Thẻ bài toán tiêu biểu: Card #3 — Vinmec tóm tắt đơn thuốc

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                       │
│                                                             │
│ Bài toán: Tóm tắt đơn thuốc và dặn dò sau khám từ ghi chú   │
│ bác sĩ để giao cho bệnh nhân.                               │
│ Công ty thành viên: [x] Vinmec                              │
│                                                             │
│ Ai đang đau? Điều dưỡng (quá tải), Bác sĩ (review cuối)     │
│                                                             │
│ Workflow thủ công hiện tại (4 bước):                        │
│   1. Bác sĩ ghi chú chẩn đoán/đơn thuốc                      │
│   → 2. Điều dưỡng đọc và tóm tắt                             │
│   → 3. Soạn dặn dò bằng ngôn ngữ dễ hiểu                     │
│   → 4. Bác sĩ kiểm tra và bàn giao bệnh nhân                │
│                                                             │
│ Bước nào tốn nhất? Bước 2-3 (⏱ 15 phút/ca)                   │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2-3              │
│ (Tóm tắt + draft dặn dò), có bác sĩ duyệt                   │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                        │
│ Giảm thời gian 15 phút ──> dưới 5 phút/ca.                  │
│                                                             │
│ Quick Architecture: [x] LLM Feature (Draft + HITL)          │
└─────────────────────────────────────────────────────────────┘
```
