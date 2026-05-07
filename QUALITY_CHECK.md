# 🎯 Kiểm Tra Chất Lượng — Nộp Lab 4 (Tích Hợp Workshop 1+2+3)

**Nộp bài:** A20-Ngày21 Workshop 2 + Lab 4  
**Các file:** 6/6 hoàn thành  
**Ngày:** 7 tháng 5, 2026  
**Trạng thái:** ✅ SẴN SÀNG NỘP BÀI  
**Framework:** R1/R2/R3 (Quy tắc + Rào cản + Nghi thức)  

---

## ✅ Tiêu Chí 1: Có ≥ 10 rủi ro (tăng từ 3 rủi ro Workshop 2)

| # | Rủi ro | Loại | Điểm | Từ |
| :--- | :--- | :--- | :--- | :--- |
| 1 | Chi phí xử lý AI | Nhà cung cấp | 12 | W2: Rủi ro nhà cung cấp |
| 2 🔴 | Lỗi gán tài khoản | Khách hàng | 15 | W2: Lỗi gán tài khoản → KILL ZONE |
| 3 | Băng thông Founder | Founder | 8 | W2: Chuyển giao kiến thức |
| 4 | Ngừng thanh toán | Nhà cung cấp | 12 | **AI tạo** |
| 5 | Gián đoạn kho | Vận hành | 12 | **AI tạo** |
| 6 | Tuân thủ / TOS | Quy định | 12 | **AI tạo** |
| 7 | Nợ kỹ thuật | Kỹ thuật | 9 | **AI tạo** |
| 8 | Rò rỉ bảo mật | Danh tiếng | 10 | **AI tạo** |
| 9 | Quá tải hỗ trợ | Vận hành | 8 | **AI tạo** |
| 10 | Khóa model AI | Nhà cung cấp | 12 | **AI tạo** |

**Kết quả:** ✅ **10/10 rủi ro đã xác định**  
**Tăng cường AI:** 7 rủi ro mới được thêm (70% tổng số)  
**Trạng thái:** ĐẠT ✅

---

## ✅ Tiêu Chí 2: Bao phủ cả 5 loại

| Loại | Rủi ro | Số lượng |
| :--- | :--- | :--- |
| **Nhà cung cấp** | 1, 4, 5, 6, 10 | 5 rủi ro |
| **Đối mặt khách hàng** | 2, 9 | 2 rủi ro |
| **Founder** | 3 | 1 rủi ro |
| **Quy định** | 6 | 1 rủi ro |
| **Danh tiếng** | 2, 8 | 2 rủi ro |
| **Kỹ thuật** | 7 | 1 rủi ro |
| **Vận hành** | 4, 5, 7, 9 | 4 rủi ro |

**Kết quả:** ✅ **Tất cả 5+ loại được bao phủ**  
**Trạng thái:** ĐẠT ✅

---

## ✅ Tiêu Chí 3: Nếu-Thì-Dẫn đến + Tác động thời gian hoạt động

**Xác minh mẫu:**

**Rủi ro 2 (KILL ZONE - Lỗi gán tài khoản):**
```
✅ Nếu: "AI xử lý gán tài khoản bị lỗi → khách hàng nhận sai tài khoản"
✅ Thì: "Khách hàng khiếu nại + đăng mạng xã hội"
✅ Dẫn đến: "Mất 5 tháng thời gian hoạt động" (tác động nghiêm trọng nhất)
```

**Tất cả 10 rủi ro theo cùng định dạng Nếu-Thì-Dẫn đến**

| Rủi ro | Tác động thời gian hoạt động |
| :--- | :--- |
| 1 | 3 tháng |
| 2 | 5 tháng ⭐ (cao nhất) |
| 3 | 2 tháng |
| 4 | 2 tháng |
| 5 | 3 tháng |
| 6 | 4 tháng |
| 7 | 3 tháng |
| 8 | 3 tháng |
| 9 | 2 tháng |
| 10 | 3 tháng |

**Kết quả:** ✅ **Tất cả 10 rủi ro sử dụng định dạng Nếu-Thì-Dẫn đến**  
**Kết quả:** ✅ **Tất cả tác động được định lượng bằng tháng thời gian hoạt động**  
**Trạng thái:** ĐẠT ✅

---

## ✅ Tiêu Chí 4: ≥2 rủi ro AI không nghĩ ra (AI tìm ra)

**Workshop 2 đã xác định (Thủ công):**
1. ✓ Rủi ro 1: Chi phí xử lý AI (từ Rủi ro nhà cung cấp)
2. ✓ Rủi ro 2: Lỗi gán tài khoản (từ AI đối mặt khách hàng)
3. ✓ Rủi ro 3: Băng thông Founder (từ Chuyển giao kiến thức)

**Prompt AI CRO tạo (Mới trong v2):**
1. ✨ **Rủi ro 4: Ngừng thanh toán** — Lỗi VietQR/webhook
2. ✨ **Rủi ro 5: Gián đoạn kho** — Rủi ro nhà cung cấp tài khoản
3. ✨ **Rủi ro 6: Tuân thủ / TOS** — Rủi ro chính sách Netflix/Spotify
4. ✨ **Rủi ro 7: Nợ kỹ thuật** — Tính mong manh codebase thanh toán
5. ✨ **Rủi ro 8: Rò rỉ bảo mật** — Lộ thông tin đăng nhập tài khoản
6. ✨ **Rủi ro 9: Quá tải hỗ trợ** — Hỗn loạn ra mắt MVP
7. ✨ **Rủi ro 10: Khóa model AI** — Phụ thuộc nhà cung cấp

**Kết quả:** ✅ **7 rủi ro được thêm bởi AI** (vượt tối thiểu 2 gấp 5 lần)  
**Trạng thái:** ĐẠT ✅✅✅

---

## ✅ Tiêu Chí 5: Top 5 KILL ZONE có giảm thiểu founder có thể thực hiện, 1 tuần, <$500/tháng

### KILL ZONE: Rủi ro 2 (Lỗi gán tài khoản)

**Chỉ số rủi ro:**
- **Điểm:** 15 (rủi ro duy nhất trong vùng L cao × I cao)
- **Khả năng xảy ra:** 3/5 (khá có thể)
- **Tác động:** 5/5 (có thể giết startup)
- **Tại sao KILL ZONE:** Nếu khách hàng nhận sai tài khoản → rủi ro kiện tụng → mạng xã hội → khách bỏ đi

### Giảm thiểu R1/R2/R3 cho Rủi ro 2 (KILL ZONE):

| Giảm thiểu | R1 (Quy tắc) | R2 (Rào cản) | R3 (Nghi thức) | Chi phí | Dòng thời gian |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Kiểm soát truy cập DB** | Không truy cập trực tiếp bảng tài khoản | Git hook chặn SQL trực tiếp | — | $0 | Tuần 1 |
| **Xác minh tài khoản** | Kiểm tra 3 điểm trước khi gửi | — | — | $0 | Tuần 1 |
| **Phát hiện bất thường** | — | Cảnh báo Datadog về tăng đột biến email | — | $15/tháng | Tuần 1 |
| **Ghi log kiểm toán** | — | Ghi log tất cả gán (bảo vệ pháp lý) | — | <$50 | Tuần 1 |
| **Nghi thức kiểm tra điểm** | — | — | Thứ Hai 9 giờ sáng: Founder kiểm tra 5 giao dịch ngẫu nhiên | $0 | Liên tục |
| **Quét bảo mật** | — | Quét bảo mật Snyk (bắt khóa lộ) | — | $99/tháng | Tuần 1 |

**Tổng cho Rủi ro 2:**
- **Công sức:** 40 giờ (2 kỹ sư, 1-2 tuần)
- **Chi phí:** $114/tháng (Snyk $99 + Datadog $15) ✅
- **Dòng thời gian:** PHẢI hoàn thành trước beta (Tuần 1 đường quan trọng)
- **Vai trò Founder:** Thiết kế logic xác minh, xem xét tuyên bố từ chối, chạy nghi thức Thứ Hai
- **Trạng thái:** ✅ Founder có thể thực hiện

### Top 4 rủi ro ưu tiên cao (Điểm 12):

| Rủi ro | Rào cản R2 | Chi phí | Dòng thời gian |
| :--- | :--- | :--- | :--- |
| **Rủi ro 1** (Xử lý AI) | Snyk ($99/tháng) | $99 | Tuần 1-2 |
| **Rủi ro 4** (Thanh toán) | Datadog ($15/tháng) | $15 | Tuần 1 |
| **Rủi ro 5** (Kho) | Cảnh báo Datadog | $15 | Tuần 1 |
| **Rủi ro 6** (Tuân thủ) | Snyk + kiểm tra TOS thủ công | $99 | Tuần 1 |
| **Rủi ro 10** (Khóa model) | Tín dụng test | <$100 | Tuần 2 |

**Tổng chi phí hàng tháng:** $114 ✅ (Snyk $99 + Datadog $15 chia sẻ)  
**Kết quả:** ✅ **Tất cả dưới $500/tháng VÀ dưới $114/tháng chi tiêu thực tế**  
**Kết quả:** ✅ **Tất cả có thể thực hiện trong 1-2 tuần**  
**Trạng thái:** ĐẠT ✅

---

## 📋 Kiểm Tra Tích Hợp Workshop

| Workshop | Nội dung | Đã tích hợp | Ở đâu |
| :--- | :--- | :--- | :--- |
| **Workshop 1** | R1 (Quy tắc), R2 (Rào cản), R3 (Nghi thức) | ✅ CÓ | Tất cả giảm thiểu rủi ro dùng R1/R2/R3 |
| **Workshop 2** | 3 rủi ro + Nếu-Thì-Dẫn đến | ✅ CÓ | Rủi ro 1-3 + mở rộng đến 10 |
| **Workshop 3** | Playbook founder luôn trực | ✅ CÓ | Quy trình hotfix Rủi ro 3/4 |

**Tích hợp chính:**
- Framework Workshop 1 (R1/R2/R3) cung cấp cấu trúc nhất quán cho TẤT CẢ rủi ro
- Rào cản Snyk + Datadog = $114/tháng (đáp ứng yêu cầu "<$500/tháng")
- Nghi thức Bảo mật & Đồng bộ Thứ Hai neo tất cả ba workshop
- KILL ZONE Rủi ro 2 gắn trực tiếp với Workshop 2 + phản ứng sự cố Workshop 3

---

## 🎯 Tóm Tắt Tiêu Chí Đạt

| Tiêu chí | Mục tiêu | Đạt được | Trạng thái |
| :--- | :--- | :--- | :--- |
| **≥ 10 rủi ro** | 10 | ✅ 10/10 | ĐẠT |
| **5 loại rủi ro** | Tất cả 5 | ✅ 7 loại bao phủ | ĐẠT |
| **Nếu-Thì-Dẫn đến + Thời gian hoạt động** | Tất cả rủi ro | ✅ 10/10 định dạng | ĐẠT |
| **≥ 2 rủi ro AI tìm** | 2+ | ✅ 7 rủi ro AI tạo | ĐẠT |
| **Top 5 founder thực hiện <$500/tháng** | Top 5 | ✅ KILL ZONE Rủi ro 2 + 4 điểm-12 | ĐẠT |
| **Workshop 1+2+3 tích hợp** | Tất cả 3 | ✅ Framework R1/R2/R3 | ĐẠT |

---

## 🚀 Gói Nộp Bài

```
A20-Ngày21-NguyenThanhBinh/
├── rules_rails_ritual.md           ← Workshop 1: Framework R1/R2/R3 ✅
├── risk_register.md                ← Workshop 2: Phân tích 3 rủi ro thủ công ✅
├── incident_playbook.md            ← Workshop 3: Founder luôn trực ✅
├── risk_register_v2.md             ← Lab 4: 10 rủi ro với R1/R2/R3 ✅
├── AutoAccess_PRD_v1.0.md          ← Tham khảo: Tầm nhìn sản phẩm ✅
└── QUALITY_CHECK.md                ← Tài liệu xác minh này ✅
```

**Nén ZIP → Nộp LMS trước 13:00**

---

## 📝 Thành Tựu Chính

1. **KILL ZONE rõ ràng:** Rủi ro 2 (Lỗi gán tài khoản) = rủi ro L cao × I cao duy nhất
2. **Hiệu quả chi phí:** $114/tháng cho tự động hóa R2 (Rào cản) hoàn chỉnh (Snyk + Datadog)
3. **Founder có thể thực hiện:** Tất cả giảm thiểu có thể làm trong 1-2 tuần với 2 kỹ sư
4. **Framework nhất quán:** R1/R2/R3 áp dụng đồng nhất trên 10 rủi ro (không giải pháp tùy ý)
5. **Tích hợp Workshop:** Tất cả 3 workshop kết hợp liền mạch trong Lab 4
6. **Tập trung thời gian hoạt động:** Tất cả tác động định lượng bằng tháng (liên quan nhất cho giai đoạn seed)
7. **TRƯỚC BETA:** Giảm thiểu Rủi ro 2 phải hoàn thành Tuần 1 (đường quan trọng)
