# Sổ Đăng Ký Rủi Ro — Workshop 2 (Phân Tích Thủ Công)

**Workshop:** 2 — Workshop Quản Lý Rủi Ro  
**Ngày:** 7 tháng 5, 2026  
**Nguồn:** PRD Ngày 17 + Lộ trình Ngày 20 + workshop thủ công 3 giờ  
**Kết quả:** 3 rủi ro chính cho startup giai đoạn seed AutoAccess

---

## Bối Cảnh

**Công ty:** AutoAccess (Tự động hóa cho thuê tài khoản bằng AI)  
**Quy mô đội:** 5 người  
**Thời gian hoạt động:** 12 tháng  
**Ra mắt MVP:** Quý 3 năm 2026  
**Tính năng chính:** So sánh sản phẩm + quy trình bảo hành AI

---

## Top 3 Rủi Ro (Xác Định Thủ Công)

### Rủi Ro 1: Rủi Ro Nhà Cung Cấp (Vendor Risk)

**Loại:** Nhà cung cấp / Tài chính

**Kịch bản (Nếu-Thì-Dẫn đến):**
- **Nếu:** OpenAI hoặc nhà cung cấp API thay đổi chính sách giá đột ngột (thay đổi giá) hoặc siết chặt giới hạn tốc độ đối với các truy vấn so sánh sản phẩm phức tạp.
- **Thì:** Chi phí vận hành tăng vọt vượt quá biên lợi nhuận của dịch vụ cho thuê tài khoản.
- **Dẫn đến:** Mất **3 tháng thời gian hoạt động** do phải bù lỗ hoặc dừng tính năng để chuyển đổi code sang model khác.

**Tại sao điều này quan trọng:**
- Hiện tại: Mỗi truy vấn so sánh sản phẩm = chi phí OpenAI $0.02-0.05
- 1.000 truy vấn/ngày × trung bình $0.03 = $900/tháng (bền vững với lợi nhuận 40%)
- Nếu OpenAI tăng giá gấp đôi → $1.800/tháng (không bền vững, lợi nhuận -20%)
- Nếu giới hạn tốc độ giảm từ 10K xuống 1K yêu cầu/phút → không thể xử lý lưu lượng cao điểm

**Bằng chứng:**
- OpenAI đã thay đổi giá 3 lần trong 12 tháng qua (gpt-3.5 giảm, GPT-4o ra mắt)
- Giá của Anthropic, Gemini cũng biến động (rủi ro cho startup)

**Chấm điểm:**
- **Khả năng xảy ra:** 4/5 (Nhà cung cấp API thay đổi giá thường xuyên, biến động cao trong ngành)
- **Tác động:** 3/5 (có thể chuyển sang Gemini/Claude, nhưng tốn 1 tháng refactor + 1 tháng test + 1 tháng ảnh hưởng doanh thu = 3 tháng)
- **Điểm:** 4 × 3 = **12**

**Biện pháp giảm thiểu hiện tại (nếu có):**
- ❌ Chưa có — hoàn toàn phụ thuộc vào OpenAI

**Kế hoạch giảm thiểu (cần xây dựng):**
1. **Lớp trừu tượng:** Thiết kế giao diện nhà cung cấp AI để yêu cầu/phản hồi có thể chuyển đổi
   - Công sức: 20 giờ (1 kỹ sư, 1 tuần)
   - Chi phí: <$500 (thời gian dev đã được ngân sách)
   - Thời gian: Tuần 1 của Block 3

2. **Test Gemini/Claude:** Triển khai suy luận song song để đo chi phí/chất lượng
   - Công sức: 15 giờ (1 kỹ sư, 4 ngày)
   - Chi phí: $50 (hạn ngạch test API)
   - Thời gian: Tuần 2 của Block 3

3. **Tối ưu prompt + caching:** Giảm độ phức tạp truy vấn
   - Công sức: 10 giờ (giảm ngữ cảnh dư thừa)
   - Tiết kiệm: Giảm 30% chi phí API
   - Thời gian: Liên tục (đánh giá hàng tuần)

---

### Risk 2: Customer-facing AI Risk (Rủi ro AI đối mặt khách hàng)

**Type:** Customer-facing / Reputational / Regulatory

**Scenario (If-Then-Leading to):**
- **If:** Tính năng "So sánh sản phẩm" bị "ảo giác" (hallucination), đưa ra thông số sai lệch hoặc tư vấn sai quy định bảo hành/hoàn tiền của website.
- **Then:** Khách hàng khiếu nại dựa trên thông tin AI cung cấp (giống case Air Canada), gây khủng hoảng niềm tin và pháp lý.
- **Leading to:** Mất **5 tháng runway** do chi phí bồi thường, xử lý khủng hoảng truyền thông và sụt giảm doanh thu nghiêm trọng.

**Why This Matters:**
- Air Canada precedent: Chatbot hallucinated discount, customer sued, precedent set ($812K settlement)
- AutoAccess risk: If AI says "warranty is 6 months" but actual is "3 months" → customer buys product, complains
- Reputation hit: 1 negative review on social media (especially if legal case) = -30% acquisition this month

**Real Scenario:**
1. Customer: "Tôi muốn so sánh pin Netflix account vs. Spotify account"
2. AI hallucination: "Netflix account warranty covers device theft, Spotify doesn't" (INCORRECT)
3. Customer buys Netflix account, device gets stolen, demands refund citing warranty
4. Legal escalation: Customer posts on Twitter "AutoAccess lied to me"
5. Other users see post, trust drops, churn increases

**Evidence:**
- GPT-3.5 hallucination rate: ~8-15% on domain-specific queries
- Product comparison = high-hallucination domain (requires accuracy on warranty, not just text synthesis)

**Scoring:**
- **Likelihood:** 3/5 (happens on ~10% of complex queries, will eventually hit production)
- **Impact:** 5/5 (can lose 50% of user base + legal fees + 5 months runway to recover trust = existential)
- **Score:** 3 × 5 = **15 (KILL ZONE)**

**Current Mitigation (if any):**
- ⚠️ Partial: Have basic disclaimer "AI is reference only"
- ❌ No validation layer yet
- ❌ No human review gate

**Mitigation Plan (to build):**
1. **Guardrail validation layer:**
   - Only return AI response if confidence ≥ 0.85 (else fallback to human review or template)
   - Effort: 25 hours (design scoring, test thresholds)
   - Cost: <$300
   - Timeline: Must complete before beta (Week 1-2 of Block 3)

2. **Audit logging + disclaimers:**
   - Every AI response logged: [timestamp, user_id, input, output, confidence_score]
   - Display: "This is AI-assisted comparison. Final warranty per website policy."
   - Effort: 10 hours
   - Cost: <$200 (logging infrastructure)
   - Timeline: Week 1 of Block 3

3. **Domain knowledge base + rules engine:**
   - Build canonical list: Netflix warranty = 30 days, Spotify = 14 days, Canva = lifetime free tier
   - Cross-check AI suggestion vs. rules before returning
   - Effort: 30 hours (build + test)
   - Cost: <$500
   - Timeline: Weeks 2-3 of Block 3

**Founder-implementable?**  
⚠️ Requires backend work (validation layer) + frontend (disclaimer UI)  
→ Doable in 1 week if 2 engineers (Founder supervises)

---

### Risk 3: Founder Bandwidth Risk (Rủi ro giới hạn của Founder)

**Type:** Founder / Operational / Knowledge

**Scenario (If-Then-Leading to):**
- **If:** Founder (người nắm logic chính về tích hợp Laravel & QR Payment) gặp vấn đề sức khỏe/cá nhân trong 1 tuần khi hệ thống gặp lỗi logic thanh toán (không nhả tài khoản về mail).
- **Then:** Hệ thống tê liệt, khách hàng không nhận được hàng dù đã trả tiền, không có ai đủ thẩm quyền hoặc kiến thức để hotfix DB/API.
- **Leading to:** Mất **2 tháng runway** do mất khách hàng trung thành và chi phí hoàn tiền thủ công.

**Why This Matters:**
- Founder is single point of failure (SPOF) for Laravel + QR Payment logic
- Only Founder knows:
  - Why DB transaction blocks sometimes (edge case handling)
  - How webhook retry logic works (special case for VietQR timeout)
  - Which tables to check if account delivery fails
- If Founder unavailable (sick, burnout, family issue) → no one can execute hotfix

**Real Scenario:**
1. Monday 9 PM: Bug in payment delivery (account not sent to customer email)
2. 50 customers report "I paid but didn't get account"
3. Founder is sick (or handling other emergency)
4. Team tries to debug but don't know where to look in DB
5. Takes 16 hours to hotfix (should be 20 min with Founder knowledge)
6. Result: 50 customers refund, 15 post negative reviews, churn -10%

**Evidence:**
- Founder has written most of Laravel codebase (60% of payment logic)
- Only pair-programmed with 1 person (not transferred knowledge to others)
- No runbook: "If account delivery fails, check X table, run Y query, restart Z service"

**Scoring:**
- **Likelihood:** 2/5 (startup world: ~40% chance Founder has health/personal issue in 12 months)
- **Impact:** 4/5 (2 months lost: 1 month downtime + 1 month regaining trust; not existential but serious)
- **Score:** 2 × 4 = **8**

**Current Mitigation (if any):**
- ⚠️ Minimal: Founder writes some docs (informal)
- ❌ No knowledge transfer to other engineers
- ❌ No hotfix playbook

**Mitigation Plan (to build):**
1. **Document Laravel + QR Payment flow:**
   - Step-by-step walkthrough: How payment webhook works, DB schema for transactions, how account delivery email is triggered
   - Include: Common failure modes + fixes, rollback procedure, DB commands to debug
   - Effort: 10 hours (Founder + 1 scribe)
   - Cost: <$200
   - Timeline: Week 1-2 of Block 3 (do ASAP)

2. **Pair programming knowledge transfer:**
   - Founder + 1 engineer spend 2 hours/week (8 sessions, 1 month) debugging real issues together
   - Engineer learns: How to read logs, query DB, identify root cause
   - Effort: 16 hours (Founder's time)
   - Cost: <$500
   - Timeline: Ongoing every month

3. **Hotfix runbook + tested rollback:**
   - Build decision tree: "If account delivery fails, is it DB issue / webhook issue / email service issue?"
   - Include exact SQL queries to check status, curl commands to test, rollback steps
   - Test every 2 weeks (run through scenarios, ensure it works)
   - Effort: 8 hours (write) + 4 hours/month (test)
   - Cost: <$300
   - Timeline: Week 2 of Block 3

**Founder-implementable?**  
✅ Yes. This is documentation + training, not new code. Founder can do with 1 engineer shadowing.

---

## Summary Table

| Risk | Type | Likelihood | Impact | Score | Status | Priority |
| :--- | :--- | :---: | :---: | :---: | :--- | :--- |
| 1. Vendor Risk | Vendor/Financial | 4 | 3 | 12 | Identified | HIGH |
| 2. Customer AI Risk | Customer/Reputational | 3 | 5 | 15 | Identified | 🔴 **KILL ZONE** |
| 3. Founder Bandwidth | Founder/Operational | 2 | 4 | 8 | Identified | MEDIUM |

---

## KILL ZONE Identified

**Risk 2 (Customer-facing AI Hallucination) = KILL ZONE**

- Combines: Medium likelihood (3/5) + Extreme impact (5/5)
- Business logic: 1 customer lawsuit = -30% acquisition + legal fees = startup death
- Timeline: Must mitigate BEFORE beta (Week 1 of Block 3)
- Budget: <$1,000 (guardrails + validation layer)
- Effort: <40 hours (team of 2)

**Action:** Make Risk 2 mitigation TOP PRIORITY for Block 3

---

## Next Steps

1. **Present to team:** Share this risk analysis
2. **Create mitigation tickets:** For each risk (25+ hours of work identified)
3. **Assign owners:** Who's responsible for each mitigation?
4. **Track:** Update weekly in risk register

This manual analysis forms the foundation for Lab 4 (AI CRO augmentation) where we'll identify 7 additional risks and comprehensive scoring.
