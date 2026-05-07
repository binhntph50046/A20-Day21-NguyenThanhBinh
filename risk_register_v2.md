# Sổ Đăng Ký Rủi Ro v2 — Workshop 2 (Kiểm Toán AI CRO)

**Phiên bản:** 2.0  
**Ngày:** 7 tháng 5, 2026  
**Trạng thái:** Hoàn thành - Lab 4  
**Phương pháp:** Prompt kiểm toán AI CRO + Đánh giá Workshop thủ công  

---

## Giới Thiệu

Tài liệu này là kết quả của **Lab 4: Cập Nhật Sổ Đăng Ký Rủi Ro** trong khóa học A20-Ngày21. Nó kết hợp:

1. **PRD Ngày 17:** Tầm nhìn sản phẩm AutoAccess, mục tiêu, và chỉ số thành công (AI xử lý tự động cho thuê tài khoản)
2. **Đầu vào Workshop 1:** Quy tắc (R1) - Quy định bảo mật DB tài khoản
3. **Đầu vào Workshop 2:** 3 rủi ro chính được phân tích từ workshop
4. **Đầu vào Workshop 3:** Playbook sự cố cho founder luôn trực
5. **Prompt AI CRO:** Framework để xác định top 10 rủi ro của startup giai đoạn seed
6. **Chấm điểm thủ công:** Phân tích khả năng xảy ra & tác động với xác định KILL ZONE

**Đặc điểm nổi bật:**  
- **Tập trung:** Rủi ro liên quan tới sự sinh tồn của dịch vụ cho thuê tài khoản tự động (rủi ro sinh tồn) dựa trên tác động thời gian hoạt động
- **Định dạng:** Nếu-Thì-Dẫn đến + Chấm điểm khả năng xảy ra/tác động + Hành động giảm thiểu (R1/R2/R3)
- **Ưu tiên:** KILL ZONE (Khả năng xảy ra cao × Tác động cao) = Rủi ro lỗi gán tài khoản
- **Ngữ cảnh AI:** AutoAccess sử dụng AI để tự động xử lý cho thuê tài khoản, ghép khách hàng với tài khoản, và xử lý logic bảo hành/hoàn tiền (KHÔNG phải nghiên cứu AI)

---

## Top 10 Rủi Ro

### Rủi ro 1: Chi Phí Xử Lý AI Cho Tự Động Hóa Tài Khoản

**Loại:** Nhà cung cấp / Tài chính

**Kịch bản (Nếu-Thì-Dẫn đến):**
- **Nếu:** OpenAI hoặc nhà cung cấp API thay đổi chính sách giá đột ngột hoặc siết chặt giới hạn tốc độ đối với các lệnh xử lý tự động gán tài khoản (AI ghép tài khoản với khách hàng).
- **Thì:** Chi phí vận hành tăng vọt vượt quá biên lợi nhuận của dịch vụ cho thuê tài khoản.
- **Dẫn đến:** Mất **3 tháng thời gian hoạt động** do phải bù lỗ hoặc dừng tính năng để chuyển đổi code sang model khác.

**Ngữ cảnh kinh doanh:**
- Chi phí hiện tại: Mỗi lần xử lý tự động (ghép khách hàng → tài khoản → gửi QR) = ~\.02-0.05 OpenAI API
- Khối lượng: ~2.000 giao dịch/ngày × trung bình \.03 = \.800/tháng (bền vững với lợi nhuận 40%)
- Rủi ro: Nếu OpenAI tăng giá gấp đôi → \.600/tháng (lợi nhuận âm)
- Nếu giới hạn tốc độ giảm từ 10K xuống 1K yêu cầu/phút → không thể xử lý giờ cao điểm (khách bỏ đi)

- Khả năng xảy ra: 4
- Tác động: 3
- Điểm: 12

**Giảm thiểu (R1/R2/R3, Founder có thể thực hiện, <\/tháng, 1-2 tuần):**

**R1 — QUY TẮC: Ngăn khóa nhà cung cấp AI**
1. **Chính sách lớp trừu tượng** (không gọi OpenAI trực tiếp)
   - Quy tắc: Tất cả gọi AI phải định tuyến qua giao diện \AIProvider\
   - Không hardcode thông tin đăng nhập OpenAI trong code
   - Quyết định: Dùng biến môi trường, không code
   - Thực thi: Danh sách kiểm tra xem xét code: "Có gọi giao diện AIProvider hay API trực tiếp không?"
   - Chi phí: \ (chỉ chính sách)
   - Chủ sở hữu: Founder (định nghĩa quy tắc), Trưởng kỹ thuật (thực thi)
   - Dòng thời gian: Tuần 1 (tài liệu + thông báo)

**R2 — RÀO CẢN: Giám sát chi phí tự động & Chuyển đổi dự phòng**
1. **Quét bảo mật Snyk** (Phát hiện rủi ro lộ khóa API)
   - Quét hàng ngày tự động cho thông tin đăng nhập hardcode
   - Cảnh báo nếu tìm thấy khóa OpenAI trong lịch sử git
   - Chi phí: \/tháng (gói Team) - cũng giúp ngăn xâm phạm khóa
   - Chủ sở hữu: Kỹ sư DevOps (thiết lập) + Founder (xem xét cảnh báo)
   - Dòng thời gian: Tuần 1 (thiết lập) + liên tục
   - Bảng điều khiển: Theo dõi lỗ hổng thời gian thực

2. **Cảnh báo trần chi phí + Logic dự phòng**
   - Giám sát chi tiêu hàng ngày: Cảnh báo nếu hàng tuần >\.000 (đã ngân sách \.500)
   - Kích hoạt: Tự động chuyển sang phản hồi demo Gemini hoặc template dự phòng
   - Founder thấy cảnh báo trong Slack, có thể quyết định: "Dùng template" hoặc "Trả thêm tuần này"
   - Chi phí: <\ (cơ sở hạ tầng ghi log + cảnh báo)
   - Chủ sở hữu: 1 kỹ sư backend (thực hiện)
   - Dòng thời gian: Tuần 1-2
   - Chỉ số thành công: Không bao giờ bị bất ngờ bởi hóa đơn OpenAI nữa

**R3 — NGHI THỨC: Xem xét chi phí hàng tuần (Bảo mật & Đồng bộ - Thứ Hai 9 giờ sáng)**
- Founder xem xét: "Chúng ta có đạt bất kỳ cảnh báo chi phí nào tuần này không? Bao nhiêu lần chúng ta dự phòng sang template?"
- Câu hỏi cho đội: "Nếu OpenAI tăng giá gấp đôi ngày mai, chúng ta có thể chuyển nhanh như thế nào?"
- Hành động nếu cần: "Bắt đầu test song song Gemini sprint tiếp"
- Thời gian: 10 phút (bao gồm trong nghi thức Bảo mật & Đồng bộ)
- Chủ sở hữu: Founder
- Dòng thời gian: Mỗi Thứ Hai (liên tục)

**Tổng công sức:** 25 giờ (1-2 tuần với 1-2 kỹ sư)  
**Tổng chi phí:** \/tháng (chỉ Snyk, logic dự phòng là code nội bộ)  
**Trạng thái:** ✅ Founder có thể thực hiện

---

### Rủi ro 2: Lỗi Gán Tài Khoản (Lỗi Xử Lý AI)

**Loại:** Đối mặt khách hàng / Danh tiếng / Quy định

**Kịch bản (Nếu-Thì-Dẫn đến):**
- **Nếu:** AI xử lý tự động gán tài khoản (ghép khách hàng → tài khoản + gửi mã QR qua email/Telegram) bị lỗi logic, khiến khách hàng nhận sai tài khoản, nhận tài khoản của khách khác, hoặc không nhận được tài khoản dù đã thanh toán.
- **Thì:** Khách hàng khiếu nại, yêu cầu hoàn tiền, và đăng khiếu nại trên mạng xã hội rằng "AutoAccess cấp tài khoản sai, tôi không thể dùng được".
- **Dẫn đến:** Mất **5 tháng thời gian hoạt động** do chi phí bồi thường, xử lý khủng hoảng truyền thông, sụt giảm doanh thu nghiêm trọng, và mất niềm tin từ khách.

**Ngữ cảnh kinh doanh:**
- Hàng ngày: 1.000-2.000 giao dịch tự động (AI ghép tài khoản và gửi)
- Rủi ro: Tỷ lệ lỗi 1% = 10-20 khách hàng nhận sai tài khoản mỗi ngày
- Lan truyền: 1 khách hàng đăng trên Facebook → 30-50 người thấy → 20% trong số họ hủy
- Lịch sử: Gửi email lỗi (sai địa chỉ email) đã xảy ra 2 lần trong tháng 4 (tỷ lệ thất bại 0.5%)

- Khả năng xảy ra: 3
- Tác động: 5
- Điểm: 15 🔴 **KILL ZONE** (KHẨN CẤP)

**Giảm thiểu (R1/R2/R3, KHẨN CẤP - Block 3, Founder có thể thực hiện, <\/tháng, 1 tuần):**

**R1 — QUY TẮC: Hạn chế truy cập dữ liệu & Xử lý tài khoản**

1. **Chính sách không truy cập DB trực tiếp (Quy định bảo mật cơ sở dữ liệu)**
   - Quy tắc: Cấm nhân viên truy cập trực tiếp vào DB chứa thông tin tài khoản thô (danh sách tài khoản thô)
   - Chỉ truy cập: Bảng quản trị Laravel (tất cả hành động được ghi log)
   - Hậu quả vi phạm:
     - Lần 1: Đình chỉ - Founder điều tra trực tiếp
     - Lần 2 (hoặc mất dữ liệu): Cho thôi việc
   - Chi phí: \ (thực thi chính sách nội bộ)
   - Chủ sở hữu: Founder (thực thi)
   - Dòng thời gian: Tuần 1 (thông báo + thiết lập kiểm soát truy cập)
   - Thực hiện: Xóa thông tin đăng nhập DB khỏi laptop kỹ sư, chỉ Founder có quyền truy cập shell

2. **Cổng xác minh gán tài khoản**
   - Trước khi AI gửi tài khoản cho khách hàng: Kiểm tra 3 lần
     - ✅ Tài khoản được AI ghép có tồn tại trong kho không?
     - ✅ ID khách hàng này có đúng không?
     - ✅ Đây có phải lần thử đầu tiên không (không thử lại cùng tài khoản)?
   - Nếu BẤT KỲ kiểm tra nào thất bại → Định tuyến đến Founder để xem xét thủ công (đừng gửi sai tài khoản!)
   - Chi phí: \ (logic nội bộ)
   - Chủ sở hữu: Kỹ sư Backend (thực hiện kiểm tra)
   - Dòng thời gian: Tuần 1
   - Chỉ số thành công: 0 sự cố tài khoản sai trong beta

**R2 — RÀO CẢN: Phát hiện tự động + Phát hiện bất thường**

1. **Phát hiện bất thường Snyk + Datadog** (\ + \ = \/tháng)
   - Snyk: Quét bảo mật hàng ngày trên code Laravel (bắt mật khẩu hardcode, khóa lộ)
   - Datadog: Giám sát thời gian thực
     - Cảnh báo nếu # email gửi trong 1 giờ >2x thường (ví dụ: spam thử lại)
     - Cảnh báo nếu # tài khoản chuyển >2x thường (ví dụ: lỗi hệ thống)
     - Cảnh báo nếu truy vấn DB vào bảng tài khoản tăng đột biến (ví dụ: truy cập trái phép)
     - Tự động kill quy trình nếu phát hiện bất thường (dừng gửi sai tài khoản!)
   - Chi phí: \/tháng tổng ✅ (dưới \)
   - Chủ sở hữu: Kỹ sư DevOps (thiết lập) + Founder (xem xét cảnh báo)
   - Dòng thời gian: Tuần 1 (thiết lập)
   - Bảng điều khiển: Khả năng hiển thị thời gian thực vào chuyển tài khoản

2. **Ghi log kiểm toán cho chuyển tài khoản**
   - Ghi log mọi gán tài khoản: [timestamp, customer_id, account_id, assigned_by (AI/Thủ công), email_sent_to, email_status]
   - Lưu trữ trong bảng bảo mật riêng (để bảo vệ pháp lý nếu khách hàng tranh chấp)
   - Chi phí: <\ (cơ sở hạ tầng ghi log)
   - Chủ sở hữu: Kỹ sư Backend (thực hiện)
   - Dòng thời gian: Tuần 1
   - Tham khảo: Tương tự trường hợp Air Canada - ghi log chứng minh chúng ta theo dõi lỗi

**R3 — NGHI THỨC: Bảo mật & Đồng bộ (Thứ Hai 9:00 sáng, 30 phút)**

**Chương trình cho rủi ro gán tài khoản:**
1. **Kiểm tra điểm thủ công (15 phút):**
   - Founder chọn ngẫu nhiên 5 giao dịch thành công từ 7 ngày qua
   - Kiểm tra: Email có đến đúng khách hàng không? Tài khoản có hợp lệ không?
   - Truy vấn SQL: \SELECT * FROM account_assignments ORDER BY RAND() LIMIT 5\
   - Xác minh: Kiểm tra email đã gửi, xác minh tài khoản đang hoạt động

2. **Câu hỏi Founder cho đội (5 phút):**
   - "Nếu logic gửi mã QR hỏng hôm nay, chúng ta sẽ phát hiện nhanh như thế nào?"
   - Câu trả lời mong đợi: "Cảnh báo Datadog trong <2 phút, chúng ta kill quy trình, xem xét thủ công cho đơn bị kẹt"
   - Nếu không có câu trả lời rõ ràng → Lên lịch xem xét kiến trúc

3. **Xem xét bất thường tuần trước (10 phút):**
   - Báo cáo Datadog: "Bao nhiêu cảnh báo sai? Có vấn đề thực sự nào không?"
   - Cập nhật tài liệu Notion: [Security-Standard-v1]
   - Quyết định: Ngưỡng có quá nhạy không? Cần điều chỉnh?

**Tổng công sức:** 40 giờ (2 kỹ sư, 1-2 tuần)  
**Tổng chi phí:** \/tháng (Snyk + Datadog) ✅  
**Dòng thời gian:** Phải hoàn thành TRƯỚC ra mắt beta (Tuần 1 đường quan trọng)  
**Trạng thái:** ✅ Founder có thể thực hiện

---

### Rủi ro 3-10: Tóm tắt

**Rủi ro 3: Rủi ro băng thông Founder** (Điểm: 8)
- Founder là điểm thất bại đơn cho logic thanh toán Laravel + QR
- Giảm thiểu: Tài liệu, pair programming, runbook hotfix
- Chi phí: <\/tháng

**Rủi ro 4: Ngừng cổng thanh toán** (Điểm: 12)
- VietQR/Cassie ngừng trong giờ cao điểm
- Giảm thiểu: Logic thử lại, giám sát Datadog, chuyển đổi dự phòng
- Chi phí: \/tháng (Datadog chia sẻ)

**Rủi ro 5: Gián đoạn nguồn kho** (Điểm: 12)
- Nhà cung cấp tài khoản bị khóa hàng loạt
- Giảm thiểu: 3+ nhà cung cấp, giám sát kho Datadog
- Chi phí: \/tháng (Datadog chia sẻ)

**Rủi ro 6: Tuân thủ & TOS nền tảng** (Điểm: 12)
- Netflix/Spotify cấm chia sẻ tài khoản
- Giảm thiểu: Ngôn ngữ pháp lý, giám sát chính sách Snyk
- Chi phí: \/tháng (Snyk chia sẻ)

**Rủi ro 7: Nợ kỹ thuật** (Điểm: 9)
- Codebase thanh toán mong manh
- Giảm thiểu: Test tự động, git hook
- Chi phí: \ (nội bộ)

**Rủi ro 8: Rò rỉ bảo mật** (Điểm: 10)
- Lộ thông tin đăng nhập tài khoản
- Giảm thiểu: Quét bảo mật Snyk hàng ngày
- Chi phí: \/tháng (Snyk chia sẻ)

**Rủi ro 9: Quá tải hỗ trợ** (Điểm: 8)
- Ra mắt MVP với lỗi
- Giảm thiểu: Ra mắt mềm, template phản hồi đóng hộp
- Chi phí: <\/tháng

**Rủi ro 10: Khóa model AI** (Điểm: 12)
- Khó chuyển nhà cung cấp
- Giảm thiểu: Lớp trừu tượng AIProvider, test Gemini/Claude
- Chi phí: <\ (tín dụng test API)

---

## Tóm Tắt Chấm Điểm

| Rủi ro | Tên ngắn | Khả năng | Tác động | Điểm | Chi phí R1/R2/R3/tháng |
| :--- | :--- | :---: | :---: | :---: | :--- |
| 1 | Chi phí xử lý AI | 4 | 3 | 12 | \ (Snyk) |
| 2 🔴 | Lỗi gán tài khoản | 3 | 5 | 15 | **\** (Snyk + Datadog) |
| 3 | Băng thông Founder | 2 | 4 | 8 | <\ (git hook) |
| 4 | Ngừng thanh toán | 4 | 3 | 12 | \ (Datadog) |
| 5 | Gián đoạn kho | 3 | 4 | 12 | \ (Datadog) |
| 6 | Tuân thủ / TOS | 3 | 4 | 12 | \ (Snyk) |
| 7 | Nợ kỹ thuật | 3 | 3 | 9 | \ (nội bộ) |
| 8 | Rò rỉ bảo mật | 2 | 5 | 10 | \ (Snyk) |
| 9 | Quá tải hỗ trợ | 4 | 2 | 8 | <\ (template) |
| 10 | Khóa model AI | 3 | 4 | 12 | <\ (tín dụng test) |

**Tổng chi phí hàng tháng:** \ ✅ (Snyk \ + Datadog \ chia sẻ trên tất cả rủi ro)

---

## Ma Trận Rủi Ro 2x2

`
        Tác động (Mất thời gian hoạt động)
        └─ 5 ┐
            │     🔴 CAO-CAO      🔴 CAO-CAO
        4   │  R3  (KILL ZONE)   R2 R5 R6 R10
            │      
        3   │  R8        R1 R4 R7
            │        R9
        2   │
            │
        1   └────────────────────────────
              1    2    3    4    5
              Khả năng xảy ra (Xác suất)

        🔴 KILL ZONE (L≥3, I≥4): Chỉ rủi ro 2
        🟠 THEO DÕI CAO (L≥4 hoặc I≥4): Rủi ro 1, 4, 5, 6, 10
        🟡 TRUNG BÌNH: Rủi ro 7, 8, 9
        🟢 THẤP: Rủi ro 3 (nếu có tài liệu)
`

### Xác Định Kill Zone

🔴 **Rủi ro 2 (Lỗi gán tài khoản) = KILL ZONE** — Rủi ro duy nhất trong vùng khả năng xảy ra cao × tác động cao
- Khả năng xảy ra 3/5 (khá có thể xảy ra)
- Tác động 5/5 (có thể giết startup trong 5 tháng)
- Điểm 15 (nguy hiểm nhất)

Tại sao KILL ZONE?
- **Rủi ro ngay lập tức:** Nếu khách hàng nhận sai tài khoản hoặc tài khoản từ khách hàng khác → rủi ro kiện tụng
- **Hiệu ứng lan truyền:** 1 khách hàng đăng trên mạng xã hội → 30-50 thấy → 20% hủy
- **Sụp đổ niềm tin Founder:** Nếu AutoAccess thậm chí không thể giao đúng tài khoản, tại sao phải trả tiền?

**Giải pháp:** Thực hiện R1/R2/R3 trước beta (Tuần 1 đường quan trọng)
- R1: Không truy cập DB trực tiếp, cổng xác minh trên tất cả gán tài khoản
- R2: Phát hiện bất thường Datadog + tự động kill khi lỗi + bảo mật Snyk
- R3: Nghi thức Thứ Hai - Founder kiểm tra điểm 5 giao dịch ngẫu nhiên

---

## Kết Luận

**Trạng thái Lab 4:** ✅ HOÀN THÀNH
- Đã trình bày: Sổ đăng ký rủi ro với 10+ rủi ro sử dụng framework R1/R2/R3
- Giảm thiểu: Hiệu quả chi phí (\/tháng) + founder có thể thực hiện (<2 tuần)
- Ưu tiên: KILL ZONE rõ ràng (Rủi ro 2: Lỗi gán tài khoản)
- Định dạng: Tiếng Việt + AI CRO + Tích hợp workshop
- Sẵn sàng nộp trước 13:00
