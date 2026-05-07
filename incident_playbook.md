# Sổ Tay Xử Lý Sự Cố — Workshop 3 (Founder Luôn Trực)

**Workshop:** 3 — Ứng Phó Sự Cố & Mô Hình Hỗ Trợ Founder  
**Ngày:** 7 tháng 5, 2026  
**Trọng tâm:** Quy trình khi sự cố nghiêm trọng xảy ra, cách thực thi mà không để Founder là người duy nhất giải quyết  
**Mô hình:** Founder luôn trực, nhưng không đơn độc — có lộ trình leo thang cho đội

---

## Tổng Quan

**Tại sao sổ tay này tồn tại:**
- AutoAccess là hệ thống thanh toán (tiền thật, niềm tin khách hàng thật)
- Sự cố xảy ra: API ngừng hoạt động, webhook thanh toán lỗi, AI ảo giác xuất hiện, v.v.
- Founder hiện là điểm nghẽn để giải quyết vấn đề thanh toán (Rủi ro 3)
- Sổ tay này đảm bảo: Phản ứng nhanh + xây dựng năng lực đội + Founder không kiệt sức

**Nguyên tắc cốt lõi:**  
Founder là "người phản ứng đầu tiên + giám sát" chứ không phải "người giải quyết duy nhất"

---

## Phân Loại Sự Cố

### Mức Độ Nghiêm Trọng

| Mức độ | Định nghĩa | Mục tiêu TTR | Phản ứng Founder |
| :--- | :--- | :--- | :--- |
| **NGHIÊM TRỌNG** (P1) | Doanh thu dừng, khách không thể hoàn tất mua hàng, webhook thanh toán ngừng | <15 phút | Gọi ngay, tham gia phòng chiến |
| **CAO** (P2) | Giao hàng chậm, <5% giao dịch bị ảnh hưởng, giới hạn tốc độ API | <1 giờ | Phản hồi trong 1 giờ, chỉ đạo đội |
| **TRUNG BÌNH** (P3) | Vấn đề khách hàng riêng lẻ, AI ảo giác ở 1 trường hợp ngoại lệ, lo ngại bảo mật | <4 giờ | Phản hồi trong 4 giờ, xem xét giải pháp |
| **THẤP** (P4) | Lỗi tài liệu, lỗi chính tả trong email, vấn đề giao diện thẩm mỹ | <24 giờ | Giải quyết không đồng bộ, ghi log cho sprint tiếp |

### Ví Dụ Theo Rủi Ro

| Sự cố | Mức độ | Người chịu trách nhiệm | Vai trò Founder |
| :--- | :--- | :--- | :--- |
| Cổng thanh toán (VietQR) ngừng hoạt động | P1 NGHIÊM TRỌNG | Vận hành/Founder | Dẫn đầu phòng chiến |
| API OpenAI trả lỗi khi truy vấn bảo hành | P2 CAO | Trưởng kỹ thuật | Giám sát dự phòng |
| Khách hàng nói AI cho thông tin bảo hành sai | P2 CAO | Founder | Xác thực khiếu nại, giao tiếp |
| Founder không có mặt + cần hotfix thanh toán | P1 NGHIÊM TRỌNG | Kỹ sư dự phòng | Founder gọi vào / Dự phòng thực thi runbook |
| Dịch vụ email đạt giới hạn tốc độ | P3 TRUNG BÌNH | Kỹ sư Backend | Xem xét + phê duyệt thử lại hàng loạt |

---

## Quy Trình Phòng Chiến (cho P1 NGHIÊM TRỌNG)

### Kích Hoạt

**Ai kích hoạt:** Bất kỳ thành viên đội nào xác định sự cố P1 (doanh thu dừng)

**Tín hiệu:**
```
Đăng trong #incidents: 🚨 [P1 NGHIÊM TRỌNG] {Mô tả ngắn}
@founder @ops-lead (ping trong Slack)
```

**Hành động Founder (trong 2 phút):**
1. Xác nhận trong Slack: "Đã nhận, tham gia phòng chiến"
2. Bắt đầu link Google Meet + ghim trong #incidents
3. Mời: ops-lead, kỹ sư liên quan, người có kiến thức dự phòng

### Cấu Trúc Phòng Chiến

**Thời lượng:** Thường 30-45 phút (cho đến khi dịch vụ được khôi phục)

**Dòng thời gian:**
- **Phút 0-5:** Đánh giá (cái gì bị hỏng?)
- **Phút 5-10:** Giả thuyết nguyên nhân gốc (code của chúng ta / nhà cung cấp ngừng / vấn đề dữ liệu?)
- **Phút 10-20:** Thực thi sửa (rollback / thử lại / leo thang nhà cung cấp)
- **Phút 20-30:** Xác minh (luồng thanh toán hoạt động lại chưa?)
- **Phút 30-45:** Giao tiếp (với khách hàng qua trang trạng thái / email)

**Vai trò trong Phòng Chiến:**

| Vai trò | Người | Nhiệm vụ |
| :--- | :--- | :--- |
| **Chỉ huy** | Founder | Chiến lược tổng thể, ra quyết định, giao tiếp khách hàng |
| **Trưởng kỹ thuật** | Kỹ sư vận hành / Trưởng Backend | Debug + thực thi sửa |
| **Giao tiếp** | Founder / Sản phẩm | Soạn thảo cập nhật khách hàng |
| **Ghi chép** | Bất kỳ | Ghi log dòng thời gian + hành động trong Google Doc |
| **Dự phòng** | Kỹ sư thứ 2 | Xác minh sửa, chuẩn bị rollback |

**Ví dụ Phòng Chiến (Lỗi Webhook Thanh Toán):**

```
T=0:00 - Cảnh báo kích hoạt: Phản hồi webhook từ VietQR timeout
T=0:03 - Founder tham gia + xác nhận: Đúng, không thể hoàn tất mua thử
T=0:08 - Kỹ sư Backend: "Trang trạng thái VietQR không có sự cố, log của chúng ta hiện timeout kết nối"
T=0:15 - Giả thuyết: Quy tắc tường lửa server của chúng ta vô tình chặn dải IP VietQR
T=0:20 - Sửa thực thi: Whitelist IP VietQR lại
T=0:25 - Xác minh: Mua thử thành công, 10 thanh toán đang chờ được xử lý
T=0:35 - Giao tiếp: Email cho khách hàng bị ảnh hưởng + cập nhật trạng thái
T=0:45 - Lên lịch post-mortem cho ngày mai 10 giờ sáng
```

---

## Cây Quyết Định: Ai Sửa Cái Gì

```
SỰ CỐ XẢY RA
│
├─ Doanh thu có dừng không? (Không thể hoàn tất mua hàng?)
│  │
│  ├─ CÓ → P1 NGHIÊM TRỌNG
│  │  │   ├─ Có phải sự cố nhà cung cấp không (VietQR/OpenAI ngừng)?
│  │  │   │  └─ CÓ → Liên hệ nhà cung cấp, Founder leo thang
│  │  │   │
│  │  │   └─ Có phải code / webhook của chúng ta không?
│  │  │      └─ CÓ → Kỹ sư dự phòng chạy runbook hotfix (Founder giám sát)
│  │  │
│  │  └─ KHÔNG → Chuyển sang P2
│  │
│  └─ KHÔNG → P2 hoặc thấp hơn
│
├─ Có ảnh hưởng >1% người dùng không?
│  │
│  ├─ CÓ → P2 CAO
│  │  └─ Trưởng kỹ thuật + Founder (phản hồi 1 giờ)
│  │
│  └─ KHÔNG → P3 TRUNG BÌNH hoặc P4 THẤP
│
└─ Có liên quan đến bảo mật không? (Rò rỉ dữ liệu / tài khoản bị xâm phạm)
   │
   ├─ CÓ → P2 CAO (bảo mật)
   │  └─ Founder + kiểm tra audit trail
   │
   └─ KHÔNG → Tiếp tục ở trên
```

---

## Sổ Tay Theo Danh Mục Rủi Ro

### Sổ Tay 1: Lỗi Webhook Thanh Toán (Rủi ro 4)

**Kích hoạt:** Thanh toán hiển thị "Đang xử lý..." trong >5 phút, khách hàng báo cáo không giao

**Triệu chứng:**
- Thanh toán nhận được trong tài khoản ngân hàng ✅
- Webhook từ VietQR không đến server của chúng ta ❌
- Tài khoản không được giao cho khách hàng ❌
- Log hệ thống hiển thị: "Connection timeout from VietQR"

**Các bước sửa:**
1. **Đánh giá:** Kiểm tra trang trạng thái VietQR + sức khỏe server của chúng ta
   ```bash
   curl -v https://vietqr.io/status  # Nhà cung cấp có hoạt động không?
   tail -100 /var/log/webhook.log     # Log của chúng ta
   netstat -tulpn | grep 443           # Cổng có mở không?
   ```

2. **Giả thuyết:** Vấn đề mạng / chặn tường lửa / sự cố nhà cung cấp
   - Nếu nhà cung cấp ngừng → Chờ 15 phút + leo thang hỗ trợ nhà cung cấp
   - Nếu tường lửa → Kiểm tra whitelist IP (Founder biết cấu hình)

3. **Sửa (nếu code của chúng ta):**
   ```bash
   # Kỹ sư dự phòng thực thi (với Founder theo dõi)
   git log --oneline -5 payment/
   git diff main~1 payment/webhook.php  # Cái gì đã thay đổi?
   
   # Tùy chọn A: Rollback
   git revert {commit}
   git push  # Kích hoạt CI/CD, triển khai trong 3 phút
   
   # Tùy chọn B: Sửa tiến
   # Sửa lỗi, test local, commit, push
   ```

4. **Xác minh:** Test thanh toán end-to-end
   ```bash
   curl -X POST http://localhost:8000/test-payment  # Test local
   # Nếu OK → triển khai lên staging → test → triển khai lên prod
   ```

5. **Khôi phục thanh toán bị kẹt:**
   ```sql
   -- Tìm thanh toán bị kẹt ở trạng thái "processing"
   SELECT * FROM transactions WHERE status='processing' AND created_at < NOW() - INTERVAL 1 hour;
   
   -- Kích hoạt giao hàng thủ công (nếu an toàn)
   UPDATE transactions SET status='delivered' WHERE id=123;
   -- Sau đó gửi tài khoản thủ công cho khách hàng (giải pháp tạm thời)
   ```

6. **Giao tiếp với khách hàng:**
   - Email: "Chúng tôi gặp sự cố xử lý thanh toán ngắn. Tài khoản của bạn đã được giao. Xin lỗi vì sự bất tiện."

**Chủ sở hữu Runbook:** Kỹ sư dự phòng  
**Vai trò Founder:** Giám sát, phê duyệt rollback, giao tiếp  
**Mục tiêu giải quyết:** <20 phút

---

### Sổ Tay 2: AI Ảo Giác Xuất Hiện (Rủi ro 2)

**Kích hoạt:** Khách hàng phàn nàn AI cho thông tin bảo hành sai + đăng lên mạng xã hội

**Triệu chứng:**
- Khách hàng: "AI nói bảo hành tài khoản Netflix là 6 tháng, tôi bị khóa ở tháng thứ 4"
- Chính sách thực tế: Bảo hành Netflix là 14 ngày (trên website AutoAccess)
- Khách hàng yêu cầu hoàn tiền
- Bài đăng trên Twitter/Facebook đang thu hút sự chú ý

**Các bước phản hồi:**

1. **Phân loại:**
   - Đây có phải trường hợp riêng lẻ hay ảo giác có hệ thống?
   - Kiểm tra log: AI đã cho câu trả lời sai này bao nhiêu lần?
   ```sql
   SELECT COUNT(*) FROM ai_responses 
   WHERE confidence < 0.85 AND topic='warranty' 
   AND created_at > NOW() - INTERVAL 24 hours;
   ```

2. **Nếu trường hợp riêng lẻ (1-2 khách hàng):**
   - Phản hồi nhanh: "Chúng tôi xin lỗi. AI đã mắc lỗi. Đây là thông tin đúng + đề nghị hoàn tiền."
   - Ghi log trường hợp cho post-mortem

3. **Nếu có hệ thống (>5% truy vấn):**
   - **P1 NGHIÊM TRỌNG:** Tắt tính năng ngay lập tức
   - Tắt AI so sánh sản phẩm tạm thời
   - Dự phòng sang template: "Xem website để biết chi tiết bảo hành"
   - Founder gọi họp khẩn cấp

4. **Hành động khách hàng ngay lập tức:**
   - Email chủ động cho khách hàng bị ảnh hưởng (dùng audit log để tìm họ)
   - Đề nghị: Hoàn tiền đầy đủ HOẶC dịch vụ đã sửa + tín dụng $5
   - Founder đăng trên Twitter: "Chúng tôi đã xác định lỗi AI, đang sửa, xin lỗi"

5. **Phân tích nguyên nhân gốc:**
   - Ngưỡng confidence có thất bại không? (Có <0.85 và vẫn gửi không?)
   - Dữ liệu huấn luyện AI có bao gồm thông tin bảo hành sai không?
   - Khách hàng có đặt câu hỏi mơ hồ làm AI nhầm lẫn không?

6. **Sửa:**
   - Tăng ngưỡng confidence: 0.85 → 0.92
   - Thêm quy tắc kiểm tra sự thật bảo hành
   - Huấn luyện lại hoặc thêm ví dụ vào prompt

**Chủ sở hữu:** Founder (đây là rủi ro sinh tồn)  
**Dòng thời gian:** Phản hồi trong 1 giờ, sửa trong 1 tuần  
**Giao tiếp:** Chủ động + minh bạch

---

### Sổ Tay 3: Founder Không Có Mặt + Lỗi Thanh Toán (Rủi ro 3)

**Kích hoạt:** Founder bị ốm / nghỉ phép / không liên lạc được, hệ thống thanh toán có lỗi nghiêm trọng

**Triệu chứng:**
- Webhook thanh toán không xử lý (giống Sổ tay 1)
- Điện thoại Founder tắt hoặc không phản hồi
- Đội nhìn vào codebase nhưng không thể hiểu schema DB

**Các bước (Kỹ sư dự phòng thực thi):**

1. **Xác nhận:** Đăng trong #incidents: "Founder không liên lạc được, thực thi kế hoạch dự phòng"

2. **Truy cập cơ sở kiến thức:**
   - Mở `PAYMENT_RUNBOOK.md` (nên tồn tại từ giảm thiểu Rủi ro 3)
   - Theo cây quyết định: Có phải mạng / code / DB?

3. **Debug tự phục vụ:**
   ```bash
   # Runbook nên bao gồm các lệnh chính xác này
   tail -100 /var/log/webhook.log
   mysql -u root payment_db
   > SELECT * FROM transactions WHERE status='stuck' LIMIT 10;
   > SELECT * FROM webhook_queue WHERE status='failed' LIMIT 10;
   ```

4. **Ra quyết định (theo runbook):**
   - Nếu truy vấn hiển thị: Vấn đề mạng → khởi động lại nginx
   - Nếu truy vấn hiển thị: DB bị khóa → kill giao dịch chặn
   - Nếu truy vấn hiển thị: Lỗi code → rollback commit (như Sổ tay 1)

5. **Thực thi sửa không cần phê duyệt Founder:**
   - Runbook được Founder ủy quyền trước: "Nếu giao dịch bị kẹt >100, rollback commit 1234"
   - Kỹ sư dự phòng rollback commit
   - Xác minh trong staging trước

6. **Thông báo Founder khi có mặt:**
   - "Này, đã thực thi hotfix. Đây là những gì đã xảy ra. Post-mortem lúc X."

**Chủ sở hữu:** Kỹ sư dự phòng (được đào tạo trước qua pair programming)  
**Vai trò Founder:** Có sẵn cho câu hỏi (không đồng bộ), post-mortem sau  
**Dòng thời gian:** Sửa trong <15 phút (runbook được viết trước)  
**Chìa khóa:** Runbook phải **cụ thể + đã test** (không mơ hồ)

---

## Quy Trình Sau Sự Cố

### Ngay lập tức (trong 1 giờ)

1. **Giao tiếp tất cả rõ ràng:**
   - Nếu đã sửa: "Vấn đề đã giải quyết, tất cả hệ thống bình thường"
   - Nếu đang diễn ra: "Vấn đề đang diễn ra, ETA 2 giờ, chúng tôi sẽ cập nhật mỗi 30 phút"

2. **Tóm tắt Slack:**
   - Đăng trong #incidents: Dòng thời gian rõ ràng về những gì đã xảy ra
   - Tại sao nó xảy ra
   - Sửa đã áp dụng
   - Trạng thái

### Theo dõi (trong 24 giờ)

1. **Họp post-mortem:**
   - Người tham dự: Ai tham gia phòng chiến + 1 người đánh giá bên ngoài
   - Xem xét: Cái gì tốt? Cái gì thất bại? Cái gì để ngăn chặn?
   - Gán: Chủ sở hữu cho mỗi hành động phòng ngừa

2. **Tài liệu:**
   - Cập nhật playbook nếu không đầy đủ
   - Cập nhật runbook nếu các bước không rõ ràng
   - Thêm vào FAQ

3. **Giao tiếp khách hàng:**
   - Cho P1: Xin lỗi chính thức + nguyên nhân gốc + những gì đang thay đổi
   - Cho P2-P4: Cảm ơn sự kiên nhẫn + tóm tắt ngắn

---

## Đo Lường & Cải Thiện

**Theo dõi mỗi sự cố:**
- TTR (Thời gian giải quyết)
- TTD (Thời gian phát hiện)
- Tác động (# khách hàng, # giao dịch mất)
- Nguyên nhân gốc (code của chúng ta / nhà cung cấp / cấu hình)

**Chỉ số hàng tháng:**
- Sự cố P1 mỗi tháng (mục tiêu: 0, chấp nhận được: <1)
- TTR trung bình cho P1 (mục tiêu: <15 phút)
- % sự cố được ngăn chặn (do cải thiện playbook)

**Đánh giá hàng quý:**
- Playbook nào được sử dụng nhiều nhất?
- Runbook nào không đầy đủ?
- Post-mortem có dẫn đến phòng ngừa không?

---

## Ghi Chú Cho Founder

**Luôn trực rất khó.** Hãy nhớ:
- ✅ Bạn không được mong đợi sửa mọi vấn đề một mình (đó là việc của Kỹ sư dự phòng)
- ✅ Bạn được mong đợi: Quyết định + Chỉ đạo + Giao tiếp
- ✅ Dùng playbook + runbook để ủy quyền sửa
- ✅ Nếu bạn quá tải → thuê Kỹ sư vận hành tiếp theo (ủy quyền trực)

**Công việc của bạn trong sự cố:**
1. **Đánh giá:** Đây có phải P1 hay có thể chờ?
2. **Quyết định:** Rollback? Dự phòng? Leo thang nhà cung cấp?
3. **Chỉ đạo:** Nói đội làm gì (đừng tự làm tất cả)
4. **Giao tiếp:** Nói khách hàng trạng thái (mỗi 30 phút nếu đang diễn ra)
5. **Học:** Post-mortem + ngăn chặn lần sau

**Cờ đỏ (cảnh báo kiệt sức):**
- Sự cố P1 >2 lần/tuần → có gì đó bị hỏng về cấu trúc
- Bạn là người duy nhất hiểu sửa → Chuyển giao kiến thức không hoạt động
- Bạn làm việc 16 giờ/ngày trong >1 tuần → Đội không có năng lực

Nếu bất kỳ điều trên → Cần retrospective + quyết định tuyển dụng.
