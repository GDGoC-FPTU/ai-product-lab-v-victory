## 🏛️ Bối cảnh: Tôi là ai?

Tôi là **Minh**, AI Engineer tại **Vin Smart Future**. Nhóm chúng tôi được giao nhiệm vụ phối hợp với Khối Vận Hành của **Xanh SM (GSM)** để tìm kiếm các cơ hội tối ưu hóa bằng trí tuệ nhân tạo. 

Thông qua khảo sát thực địa tại Trung tâm Điều vận Xanh SM Hà Nội, tôi nhận thấy các điều phối viên (Dispatchers) đang gặp một áp lực cực kỳ lớn vào giờ cao điểm, dẫn đến việc rò rỉ hiệu suất điều xe và tăng tỉ lệ khách hàng hủy chuyến. Bài toán tôi mang vào buổi Lab hôm nay đến từ chính quan sát thực tế này.


# 🔍 Phase 1 — SCAN: Tìm kiếm cơ hội (Cá nhân)
### 📝 List bài toán của tôi:
| # | Subsidiary (VinFast/Xanh SM...) | Lens | Mô tả ngắn bài toán |
|---|----------------------------------|------|---------------------|
| 1 | Vinhomes| Lặp lại | Đội ngũ bảo vệ an ninh phải ngồi giám sát hàng ngàn luồng camera 24/7 để phát hiện xe đỗ sai quy định|
| 2 |Vinmec  | AI-upgrade | Khi bệnh nhân gọi điện hoặc nhắn tin đặt lịch với triệu chứng chung chung, tổng đâì viên thường không có chuyên môn để để xác định thường sẽ chỉ xếp vào khoa khám bệnh đa khoa.|
| 3 |Vinhomes |Pain từ người khác | Cư dân phàn nàn vì báo lỗi hỏng hóc (thấm nước, hỏng điều hòa) qua App mất nhiều thời gian mô tả, thợ đến nơi lại mang thiếu đồ nghề hoặc sai chuyên môn. |
| 4 |VinFast |Tốn thời gian |Mỗi khi ra mắt dòng xe mới hoặc cập nhật phần mềm, đội ngũ kỹ sư và kỹ thuật viên bảo hành phải soạn thảo, rà soát và dịch hàng ngàn trang tài liệu kỹ thuật  ra nhiều ngôn ngữ . |
| 5 |XanhSM|AI-upgrade |Vào giờ tan tầm hoặc lúc trời mưa, khách hàng ở các tòa nhà văn phòng hoặc trong ngõ sâu ồ ạt đặt xe. Tài xế nhận cuốc nhưng không thể tiếp cận điểm đón do đường tắc nghẽn cục bộ hoặc ngập nước. |


# 🃏 Phase 2 — QUICK-ASSESS: 3 Quick Problem Cards (Cá nhân)

Chọn top 3 từ danh sách SCAN: **#1 (Vinhomes an ninh), #4 (Vinfast), #5 (Xanh SM ).**

## Thẻ bài toán tiêu biểu: Card #1 — Vinhomes xác định đỗ sai quy định

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #001                                     │
│                                                             │
│ Bài toán (1 câu): Tự động phát hiện xe đỗ sai quy định qua luồng camera an ninh.  │
│                                                             │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [x] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Đội ngũ bảo vệ trực phòng điều khiển.  │
│                                                             │
│ Workflow thủ công hiện tại (4 bước):                        │
│   1. Mắt nhìn liên tục màn hình ghép hàng chục camera.      │
│   ──> 2. Nhận diện sự cố (xe đỗ lâu, có khói, người lạ...). │
│   ──> 3. Phóng to camera để xem xét và xác minh.            │
│   ──> 4. Bộ đàm điều động bảo vệ tuần tra tới hiện trường.  │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 1 & 2 (Dễ bỏ sót do   │
│ giới hạn tập trung của mắt người sau 1-2 tiếng trực), thông 
|báo trực tiếp vào máy của nhân viên an ninh để có thể  tối ưu
 thời gian di chuyển   │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 1 & 2 (AI Vision │
│ phân tích video 24/7 và đẩy cảnh báo pop-up kèm ảnh chụp).  │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│   Giảm thời gian phát hiện sự cố từ >5 phút ──> dưới 10 giây│
│   Tỷ lệ bỏ lọt sự cố (False Negative) ──> dưới 2%           │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [ ] LLM  [x] Agent [x] Vision│
└─────────────────────────────────────────────────────────────┘
```

## Thẻ bài toán tiêu biểu: Card #3 - Phản ánh từ cư dân
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #003                                     │
│                                                             │
│ Bài toán (1 câu): AI tự động nhận diện lỗi hỏng hóc qua ảnh/│
│ video để phân công đúng thợ và chuẩn bị sẵn vật tư từ đầu.  │
│                                                             │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [x] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Cư dân (chờ đợi, ức chế) & Thợ kỹ thuật│
│ (phải đi lại nhiều lần để khảo sát và lấy đồ nghề).         │
│                                                             │
│ Workflow thủ công hiện tại (4 bước):                        │
│   1. Cư dân gõ text báo lỗi chung chung (VD: "hỏng bồn cầu")│
│   ──> 2. BQL đọc, đoán bệnh và điều phối thợ đến kiểm tra.  │
│   ──> 3. Thợ đến căn hộ khảo sát thực tế mới biết rõ bệnh.  │
│   ──> 4. Thợ chạy về kho tìm đúng vật tư, quay lên để sửa.  │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 3 & 4 (Khảo sát và đi │
│ lấy đồ, ngốn 30-60 phút vô ích, gây chậm trễ SLA).          │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 1 & 2 (Cư dân up │
│ ảnh/video, AI phân tích lỗi, tự động tag đúng thợ chuyên môn│
│ và xuất sẵn danh sách vật tư cần mang theo).                │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│   First Time Fix (Tỷ lệ sửa xong ngay lần đầu) ──> >85%     │
│   Giảm thời gian đóng ticket (Lead time) từ 2-3h ──> <1h    │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘

## Thẻ bài toán tiêu biểu: Card #4 - Dịch tài liệu
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #004                                     │
│                                                             │
│ Bài toán (1 câu): Tự động dịch thuật và rà soát thuật ngữ   │
│ chuyên ngành cho hàng ngàn trang tài liệu kỹ thuật xe điện. │
│                                                             │
│ Công ty thành viên: [x] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Đội ngũ R&D và kỹ thuật viên bảo hành. │
│                                                             │
│ Workflow thủ công hiện tại (4 bước):                        │
│   1. Kỹ sư chốt nội dung tài liệu bản gốc (VN/EN).          │
│   ──> 2. Gửi cho biên dịch viên hoặc Agency dịch thủ công.  │
│   ──> 3. Kỹ sư review chéo để đảm bảo chuẩn thuật ngữ ô tô. │
│   ──> 4. Dàn trang lại (Format) và xuất bản xuống các xưởng.│
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2 & 3 (Khâu dịch thuật│
│ và đối chiếu tính nhất quán thuật ngữ ngốn hàng tuần/tháng).│
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2 & 3 (LLM kết   │
│ hợp RAG chứa bộ từ điển VinFast tự động dịch nhanh, highlight│
│ các điểm cần người review thay vì phải đọc từ đầu đến cuối).│
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│   Giảm thời gian bản địa hóa tài liệu từ 3 tuần ──> < 24h.  │
│   Tiết kiệm 80% - 90% chi phí thuê Agency dịch thuật ngoài. │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘

