# Quy Tắc, Rào Cản & Nghi Thức — Workshop 1

**Workshop:** 1 — Nền Tảng Vận Hành  
**Ngày:** 7 tháng 5, 2026  
**Trọng tâm:** Nghi thức đội, rào cản, quy tắc vận hành cho startup giai đoạn seed AutoAccess  

---

## I. 3 Nghi Thức (cho đội sáng lập 5 người)

### 1️⃣ Họp Hàng Ngày (9:00 sáng — 15 phút)

**Người tham gia:** Founder + 4 kỹ sư  
**Định dạng:**
- Mỗi người: "Đã làm / Bị chặn / Sẽ làm hôm nay" (tối đa 2 phút)
- Tập trung: Sức khỏe luồng thanh toán + trạng thái tính năng AI + giải quyết chặn
- Không tranh luận Slack → giữ không đồng bộ

**Quy tắc:**
- Nếu hệ thống thanh toán có sự cố → họp kéo dài đến 30 phút để xem xét sự cố
- Nếu 3+ người bị chặn → kích hoạt phiên ghép đôi ngay lập tức

**Kết quả:** Ghi lại trong kênh `#daily-standup` với timestamp

---

### 2️⃣ Đồng Bộ Hàng Tuần (Thứ Năm 3 giờ chiều — 60 phút)

**Chương trình:**
1. **Chỉ số kinh doanh** (5 phút): Doanh thu, khách bỏ đi, tỷ lệ hoàn tiền so với mục tiêu
2. **Xem xét rủi ro** (15 phút): Có sự cố nào tuần này không? Cập nhật điểm sổ đăng ký rủi ro?
3. **Kiểm tra lộ trình** (20 phút): Đúng tiến độ cho MVP Q3? Chặn?
4. **Thảo luận vận hành** (20 phút): Cải thiện quy trình, nợ kỹ thuật, tuyển dụng

**Quy tắc quyết định:**
- Nếu Rủi ro 2 (AI đối mặt khách hàng) hiển thị trường hợp ảo giác → **ngay lập tức** dừng tính năng đó + sửa trước lần ra mắt tiếp
- Nếu doanh thu thanh toán giảm > 20% tuần qua tuần → Gọi Founder cho phiên debug

**Người tham dự:** Founder, Trưởng sản phẩm, Trưởng kỹ thuật  
**Kết quả:** Quyết định được ghi lại trong `DECISIONS.md` với lý do

---

### 3️⃣ Nghi Thức Hàng Tháng: Xem Xét "Giết hoặc Cam Kết" (Thứ Sáu đầu tiên — 120 phút)

**Mục đích:** Quyết định tính năng/dự án nào tiếp tục, cái nào bị giết để bảo toàn thời gian hoạt động

**Người tham gia:** Tất cả 5 thành viên đội  
**Tiêu chí:**
- **Giết nếu:** Tính năng không cải thiện KPI cốt lõi (TTR, giữ chân, doanh thu) VÀ yêu cầu > 40 giờ kỹ thuật
- **Cam kết nếu:** Tính năng nằm trên đường quan trọng cho sự sống còn (Giảm thiểu rủi ro) HOẶC >40% người dùng yêu cầu

**Ví dụ lịch sử:**
- Giết: Bảng điều khiển phân tích nâng cao (tốt để có, 60 giờ)
- Cam kết: Logic thử lại thanh toán (Giảm thiểu rủi ro 4, 20 giờ, tác động cao)

**Kết quả:** Lộ trình v2 + danh sách ưu tiên thấp (minh bạch với đội)

---

## II. 5 Rào Cản (Guardrails = ràng buộc để ngăn quyết định tồi)

### Rào Cản 1: Khóa Hệ Thống Thanh Toán (🔒 Không Thay Đổi YOLO)

**Quy tắc:**
- Bất kỳ thay đổi nào đối với thư mục `payment/` yêu cầu:
  1. Bộ test vượt qua (100% coverage webhook)
  2. Xem xét code từ người không phải tác giả (tối thiểu 1 người)
  3. Ngâm staging 24 giờ trước khi merge production
  4. Runbook rollback được viết TRƯỚC khi triển khai

**Tại sao:** Rủi ro 4 (Ngừng thanh toán) + Rủi ro 3 (Băng thông Founder)  
**Thực thi:** Git pre-push hook chặn commit main trực tiếp vào `payment/`

---

### Rào Cản 2: Cổng Xác Thực Đầu Ra AI (🚨 Ngăn Ảo Giác)

**Quy tắc:**
- Bất kỳ phản hồi AI nào (so sánh bảo hành, gợi ý sản phẩm) phải:
  1. Ghi log đầu vào + đầu ra + điểm confidence
  2. Bao gồm tuyên bố từ chối: "Gợi ý AI — xác minh với chính sách website"
  3. Đánh dấu để xem xét con người nếu confidence < 0.85
  4. Chặn gửi nếu chủ đề chính sách bảo hành/hoàn trả → xem xét con người bắt buộc

**Tại sao:** Rủi ro 2 (Rủi ro AI đối mặt khách hàng = KILL ZONE)  
**Thực thi:** Middleware xác thực trước response.send()

---

### Rào Cản 3: Trần Chi Phí (💰 Bảo Vệ Burndown)

**Quy tắc:**
- Chi tiêu API AI được giám sát hàng ngày
- Cảnh báo nếu chi tiêu hàng tuần > $2.000 (đã ngân sách $1.500)
- Kích hoạt ngay lập tức: Chuyển sang demo Gemini hoặc template dự phòng
- Xem xét tài chính: Kiểm toán chi tiêu hàng tuần bởi Founder

**Tại sao:** Rủi ro 1 (Rủi ro nhà cung cấp)  
**Thực thi:** Giám sát Datadog + cảnh báo Slack

---

### Rào Cản 4: Theo Dõi Phụ Thuộc Nhà Cung Cấp (🏗️ Điểm Thất Bại Đơn)

**Quy tắc:**
- Phụ thuộc quan trọng (OpenAI, VietQR, cổng thanh toán):
  - Phải có ≥ 1 phương án thay thế được tài liệu hóa
  - Test phương án thay thế hàng tháng (không chỉ dự phòng giấy)
  - Runbook cho chuyển đổi <2 giờ tồn tại + đã test
- Không thể ra mắt tính năng phụ thuộc vào nhà cung cấp đơn mà không tuân thủ Rào cản 4

**Tại sao:** Rủi ro 1, 5, 6 (Rủi ro tập trung nhà cung cấp)  
**Thực thi:** Danh sách kiểm tra xem xét code bao gồm "phương án thay thế nhà cung cấp đã xác thực"

---

### Rào Cản 5: Kiến Thức Dự Phòng Founder (📖 Hệ Số Bus)

**Quy tắc:**
- Bất kỳ code nào do Founder viết (logic Laravel + QR Payment) phải:
  1. Có README từng bước (hình ảnh + định dạng lệnh)
  2. Pair-programmed với 1 kỹ sư (ghép đôi trực tiếp, không không đồng bộ)
  3. Xem xét code bởi người không phải Founder (kiểm tra kiến thức, không chỉ cú pháp)
  4. Playbook khôi phục DB + quy trình rollback đã test tồn tại
- Founder không thể là người duy nhất có thể hotfix hệ thống thanh toán

**Tại sao:** Rủi ro 3 (Băng thông Founder)  
**Thực thi:** Kiểm toán kiến thức hàng quý (test kỹ sư dự phòng có thể làm hotfix)

---

## III. Ma Trận Quyền Quyết Định (Ai quyết định cái gì?)

| Quyết định | Chủ sở hữu | Phủ quyết | Dòng thời gian |
| :--- | :--- | :--- | :--- |
| Ưu tiên tính năng | Trưởng sản phẩm | Founder | Hàng tuần |
| Hành động giảm thiểu rủi ro | Trưởng kỹ thuật | Founder | Họp hàng ngày |
| Chi tiêu ngân sách > $500 | Founder | Hội đồng | Hàng tháng |
| Ra mắt go/no-go | Founder | Trưởng kỹ thuật (an toàn) | Hàng quý |
| Bồi thường khách hàng (hoàn tiền) | Founder | Pháp lý (nếu $) | Cùng ngày |
| Giết tính năng / dự án | Founder + Trưởng kỹ thuật | Phản hồi đội | Hàng tháng |

---

## IV. Rào Cản Giao Tiếp

### Kênh Slack (bắt buộc):
- `#daily-standup` — Cập nhật trạng thái
- `#risk-alert` — Chỉ số rủi ro bị vi phạm (bot tự động đăng)
- `#incidents` — Vấn đề production, post-mortem
- `#decisions` — Quyết định được ghi log (tham chiếu chéo DECISIONS.md)

### SLA phản hồi:
- Cảnh báo rủi ro trong `#risk-alert` → Founder phản hồi trong 1 giờ
- Leo thang khách hàng → Phản hồi trong 4 giờ
- Sự cố nghiêm trọng (thanh toán ngừng) → Tất cả tay lên boong, không không đồng bộ

---

## V. Lịch Nghi Thức (Lặp lại mỗi tuần/tháng/quý)

| Nghi thức | Ngày | Giờ | Thời lượng | Người tham dự |
| :--- | :--- | :--- | :--- | :--- |
| Họp hàng ngày | Thứ Hai-Sáu | 09:00 sáng | 15 phút | Tất cả (5) |
| Đồng bộ hàng tuần | Thứ Năm | 3:00 chiều | 60 phút | Founder + 2 trưởng |
| Nghi thức hàng tháng (Giết/Cam kết) | Thứ Sáu đầu | 2:00 chiều | 120 phút | Tất cả (5) |
| Xem xét sổ đăng ký rủi ro | Thứ Sáu thứ 2 | 10:00 sáng | 30 phút | Founder + Trưởng kỹ thuật |
| Kiểm toán bảo mật | Thứ Năm thứ 3 | 4:00 chiều | 45 phút | Founder + DevOps |

---

## VI. Chế Độ Thất Bại & Leo Thang

### Khi Họp Hàng Ngày Bỏ Qua
→ Được coi là **cờ đỏ** (có nghĩa là đội đang trong khủng hoảng hoặc ưu tiên thấp giao tiếp)
→ Founder phải điều tra tại sao trong 24 giờ

### Khi Đồng Bộ Hàng Tuần Thảo Luận Sự Cố Thanh Toán
→ Tự động kích hoạt Xem xét rủi ro (chuyển sang chế độ Playbook sự cố)
→ Post-mortem được lên lịch trong 48 giờ

### Khi Nghi Thức Hàng Tháng Giết Tính Năng Đối Mặt Khách Hàng
→ Founder cá nhân giao tiếp với người dùng bị ảnh hưởng trong 24 giờ
→ Lý do + Phương án thay thế được đề nghị

---

## VII. Đo Lường & Sức Khỏe Nghi Thức

**Mỗi tháng, đo lường:**
- ✅ Tỷ lệ tham dự họp hàng ngày (mục tiêu: 95%+)
- ✅ Quyết định được ghi log (mục tiêu: 100% quyết định lớn trong DECISIONS.md)
- ✅ Sổ đăng ký rủi ro được cập nhật (mục tiêu: hàng tuần)
- ✅ Thời gian phản hồi sự cố (mục tiêu: <1 giờ cho thanh toán, <4 giờ cho khác)

**Nếu <80% tuân thủ → Retrospective về tại sao nghi thức bị phá vỡ**

---

## Ghi Chú

Tài liệu này **đang sống** — cập nhật sau mỗi Nghi thức hàng tháng nếu quy trình cần điều chỉnh. Mục tiêu là ngăn chặn hỗn loạn mà không tạo ra quan liêu.

**Triết lý chính:**
- Quy tắc bảo vệ tài sản chung (thanh toán, niềm tin khách hàng)
- Rào cản ngăn tai nạn (khóa nhà cung cấp, mất kiến thức)
- Nghi thức duy trì sự liên kết (họp hàng ngày, đồng bộ hàng tuần, xem xét hàng tháng)
