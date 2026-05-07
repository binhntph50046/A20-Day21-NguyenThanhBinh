# Tài Liệu Yêu Cầu Sản Phẩm (PRD)

## AutoAccess — Nền Tảng Tự Động Hóa Cho Thuê Tài Khoản Bằng AI

**Phiên bản:** 1.0  
**Tác giả:** Nguyễn Thanh Bình  
**Ngày:** 24 tháng 4, 2026  
**Trạng thái:** Nháp → Đang xem xét → Đã phê duyệt  
**Các bên liên quan:** Kỹ thuật, Sản phẩm, Kinh doanh

---

## 📋 Kiểm Soát Tài Liệu

| Phiên bản | Ngày | Tác giả | Thay đổi |
| :---- | :---- | :---- | :---- |
| 1.0 | 2026-04-24 | Nguyễn Thanh Bình | PRD ban đầu |

---

## 🎯 Tóm Tắt Tổng Quan

**Tên Sản Phẩm:** AutoAccess

**Tầm Nhìn Sản Phẩm:**  
Biến việc cho thuê tài khoản số từ quy trình thủ công 100% thành hệ thống tự động hóa hoàn toàn bằng AI, hoạt động 24/7 không cần con người can thiệp.

**Giá Trị Cốt Lõi:**  
Giảm thời gian xử lý lỗi tài khoản từ hàng giờ xuống còn dưới 1 phút, tăng doanh thu 40% nhờ phục vụ khách hàng ban đêm và giờ cao điểm.

**Mục Tiêu Ra Mắt:** Quý 3 năm 2026 (MVP)

---

## 🚧 Vấn Đề Cần Giải Quyết

### Tình Trạng Hiện Tại

Chủ shop cho thuê tài khoản số (Netflix, Spotify, Canva) đang vận hành 100% thủ công:

1. **Thanh toán:** Check bank statement thủ công mỗi 10-15 phút  
2. **Giao hàng:** Copy-paste tài khoản từ Excel → Email/Telegram  
3. **Bảo hành:** Khi khách gặp lỗi (sai mật khẩu, hết hạn, bị khóa):  
   - Khách gửi ảnh lỗi qua Messenger/Telegram  
   - Chủ shop phải xem ảnh, phân tích lỗi  
   - Tìm tài khoản thay thế trong kho  
   - Gửi lại cho khách  
   - **Thời gian trung bình: 2-4 giờ**

### Điểm Đau

| Bên Liên Quan | Điểm Đau | Tác Động |
| :---- | :---- | :---- |
| **Chủ Shop** | Không thể ngủ đủ giấc (phải kiểm tra đơn ban đêm) | Căng thẳng cao, kiệt sức |
| **Chủ Shop** | Mất 40% doanh thu tiềm năng (không xử lý được đơn lúc 22h-6h sáng) | Mất doanh thu |
| **Khách Hàng** | Chờ 2-4 giờ để được bảo hành | Trải nghiệm tệ → không quay lại |
| **Khách Hàng** | Không biết đơn hàng đã thanh toán có được xử lý chưa | Lo lắng → yêu cầu hoàn tiền |

### Tác Động Định Lượng

- **Mất 40% doanh thu** do không xử lý được đơn ban đêm  
- **2-4 giờ** thời gian xử lý bảo hành trung bình  
- **30% tỷ lệ khách bỏ đi** do trải nghiệm bảo hành kém  
- **Hơn 50 tin nhắn mỗi ngày** hỏi "đơn của tôi đâu rồi?"

---

## 🎯 Mục Tiêu & Chỉ Số Thành Công

### Mục Tiêu Kinh Doanh

1. **Tăng doanh thu 40%** nhờ phục vụ 24/7  
2. **Giảm tỷ lệ khách bỏ đi từ 30% xuống 10%** nhờ trải nghiệm tốt hơn  
3. **Giảm khối lượng công việc của chủ shop 90%** (từ 8 giờ/ngày xuống 0.8 giờ/ngày)

### Mục Tiêu Sản Phẩm

1. **Tỷ lệ tự động hóa ≥ 99%** - Không cần can thiệp thủ công  
2. **Thời gian xử lý < 1 phút** - Từ lúc khách gửi ảnh lỗi đến lúc nhận tài khoản mới  
3. **Độ chính xác ≥ 98%** - AI phân loại đúng loại lỗi

### Success Metrics (KPIs)

| Metric | Current | Target (3 months) | Measurement |
| :---- | :---- | :---- | :---- |
| **Time to Resolution (TTR)** | 2-4 giờ | \< 1 phút | Timestamp: error reported → new account sent |
| **Automation Rate** | 0% | ≥ 99% | % orders không cần human intervention |
| **D7 Retention** | 50% | 80% | % users quay lại trong 7 ngày |
| **Refund Rate** | 15% | \< 3% | % orders yêu cầu refund do lỗi |
| **NPS** | 20 | 50 | Net Promoter Score |

---

## 👥 Target Users & Personas

### Primary User: Shop Owner (Solo Operator)

**Demographics:**

- Age: 22-35  
- Location: Vietnam (Tier 1 cities)  
- Tech-savvy: Medium-High  
- Business size: 20-50 orders/day  
- Revenue: 30-100M VND/month

**Behavioral Traits:**

- Vận hành cá nhân, không có nhân sự  
- Online 16-18h/ngày để check đơn  
- Sử dụng Excel để quản lý kho tài khoản  
- Giao tiếp với khách qua Messenger/Telegram

**Jobs to Be Done:**

1. Xác nhận thanh toán nhanh để gửi tài khoản ngay  
2. Xử lý bảo hành tự động để không mất khách  
3. Quản lý kho tài khoản để tránh giao trùng

**Pain Points:**

- "Tôi không thể ngủ đủ giấc vì phải check đơn ban đêm"  
- "Khách chửi khi tài khoản lỗi mà tôi không online"  
- "Tôi mất 40% doanh thu vì không xử lý được đơn lúc 2h sáng"

### Secondary User: Buyer

**Demographics:**

- Age: 18-40  
- Location: Vietnam  
- Tech-savvy: Low-Medium

**Jobs to Be Done:**

1. Nhận tài khoản ngay sau khi thanh toán  
2. Được bảo hành nhanh khi tài khoản lỗi

**Pain Points:**

- "Tôi đã chuyển tiền nhưng không biết bao giờ nhận tài khoản"  
- "Tài khoản lỗi mà phải chờ 3 tiếng mới được đổi"

---

## 💡 Solution Overview

### Product Concept

**AutoAccess** \= "Vending machine cho tài khoản số"

Tự động hóa 100% workflow từ thanh toán → giao hàng → bảo hành, không cần con người.

### Core Features (MVP)

#### 1\. Auto Payment → Account Delivery

**User Flow:**

Buyer quét QR → Chuyển khoản → VietQR webhook → 

System nhận IPN → Validate payment → 

Lấy tài khoản từ kho → Gửi Email/Telegram → 

Buyer nhận tài khoản (\< 10 giây)

**Technical Requirements:**

- Tích hợp VietQR API / Cassie API  
- Webhook endpoint nhận IPN  
- Payment validation logic  
- Email/Telegram sending service  
- Inventory management system

**Acceptance Criteria:**

- [ ] 95% payments được xác nhận trong \< 10 giây  
- [ ] 100% tài khoản được gửi qua Email \+ Telegram  
- [ ] 0% duplicate account (không giao trùng)

---

#### 2\. AI Vision Warranty (Core Feature — MOAT)

**User Flow:**

Buyer gặp lỗi → Gửi ảnh lỗi qua chatbot → 

AI Vision (GPT-4o) phân tích ảnh → 

Phân loại lỗi (sai mật khẩu / hết hạn / bị khóa) → 

Validate order history → 

Lấy tài khoản mới từ kho → 

Gửi tài khoản mới \+ ghi log → 

Buyer nhận tài khoản (\< 60 giây)

**AI System Design:**

| Component | Specification |
| :---- | :---- |
| **Model** | GPT-4o (Vision) |
| **Input** | Screenshot của error message |
| **Output** | Error classification: wrong\_password / expired / banned / unknown |
| **Confidence Threshold** | ≥ 85% → auto-replace; \< 85% → escalate to human |
| **Latency** | \< 10 seconds |
| **Cost** | \~$0.01 per request |

**Error Classification Logic:**

\# Pseudo-code

def classify\_error(image):

    prompt \= """

    Analyze this screenshot and classify the error:

    1\. wrong\_password: "Incorrect password" / "Sai mật khẩu"

    2\. expired: "Subscription expired" / "Hết hạn"

    3\. banned: "Account suspended" / "Tài khoản bị khóa"

    4\. unknown: Cannot determine

    

    Return JSON: {"error\_type": "...", "confidence": 0.XX}

    """

    

    response \= gpt4o\_vision(image, prompt)

    

    if response.confidence \>= 0.85:

        return auto\_replace\_account(response.error\_type)

    else:

        return escalate\_to\_human(image, response)

**Fallback UX — Graceful Handover:**

**Trigger Conditions:**

- Confidence score \< 85%  
- User clicks "Cần người thật"  
- AI phát hiện ảnh không rõ / không đọc được

**System Actions:**

1. Gửi alert qua Telegram cho shop owner:  
     
   🚨 Cần xử lý thủ công  
     
   Order ID: \#12345  
     
   Customer: 0912345678  
     
   Issue: AI confidence 72% (low)  
     
   \[Xem ảnh lỗi\] \[Xem đơn hàng\]  
     
2. Gửi message cho buyer:  
     
   Chúng tôi đang xử lý yêu cầu của bạn.  
     
   Thời gian dự kiến: 15-30 phút.  
     
   Hoặc bạn có thể:  
     
   \[Hoàn tiền về ví\] \[Chờ xử lý\]

**Acceptance Criteria:**

- [ ] 98% accuracy trong phân loại lỗi (test với 1000 ảnh thực tế)  
- [ ] \< 60 giây từ lúc gửi ảnh đến lúc nhận tài khoản mới  
- [ ] \< 2% false positive (cấp tài khoản sai)  
- [ ] 100% escalation cases được alert qua Telegram trong \< 5 giây

---

#### 3\. Inventory Dashboard (Simplified)

**Purpose:**  
Quản lý kho tài khoản real-time, tránh giao trùng, cảnh báo khi sắp hết hàng.

**Features:**

| Feature | Description |
| :---- | :---- |
| **Account Status** | Live (sẵn sàng) / Die (lỗi) / Rented (đã giao) |
| **Real-time Sync** | Update status ngay khi giao hàng hoặc bảo hành |
| **Low Stock Alert** | Telegram notification khi \< 10 accounts còn lại |
| **Bulk Import** | Upload CSV để thêm tài khoản hàng loạt |

**Technical Stack:**

- Laravel backend  
- MySQL database  
- Real-time updates via WebSocket (optional for MVP)

**Acceptance Criteria:**

- [ ] 0% duplicate account (row-level locking)  
- [ ] \< 1 second latency khi update status  
- [ ] Alert gửi trong \< 5 giây khi stock \< 10

---

## ❌ Out of Scope (MVP)

| Feature | Reason | Future Consideration |
| :---- | :---- | :---- |
| **Affiliate System** | Không cần thiết để validate AI warranty | Post-MVP (Month 6-12) |
| **Mobile App** | Web responsive đủ cho MVP | Post-MVP nếu có demand |
| **Multi-language** | Tập trung thị trường VN | SEA expansion (Month 12+) |
| **Analytics Dashboard** | Nice-to-have, không critical | Post-MVP |
| **Multi-shop Management** | MVP chỉ serve 1 shop/account | Post-MVP (enterprise feature) |

---

## 🚫 Non-Goals

- **Không trở thành marketplace** như Shopee/Lazada  
- **Không cung cấp payment gateway** (chỉ integrate existing)  
- **Không quản lý nguồn tài khoản** (shop owner tự lo)  
- **Không xử lý legal compliance** cho việc cho thuê tài khoản (shop owner chịu trách nhiệm)

---

## 🧪 Riskiest Assumptions & Validation Plan

### Assumption 1: AI Vision Accuracy

**Assumption:**  
GPT-4o Vision có thể phân loại chính xác ≥98% các loại lỗi tài khoản từ screenshot.

**Risk Level:** 🔴 Critical

**Validation Plan:**

1. **Cheapest Test (Week 1-2):**  
     
   - Collect 100 real error screenshots từ pilot shops  
   - Manual labeling: wrong\_password / expired / banned  
   - Test GPT-4o Vision accuracy  
   - **Success Criteria:** ≥95% accuracy

   

2. **Landing Page Test (Week 3-4):**  
     
   - Build simple landing page: "Upload ảnh lỗi → AI phản hồi"  
   - Không cần backend thật (mock response)  
   - Track: % users upload ảnh rõ / % users hiểu kết quả  
   - **Success Criteria:** ≥70% users upload ảnh đủ rõ để AI đọc

   

3. **Pilot Test (Week 5-8):**  
     
   - Deploy với 5 pilot shops  
   - Track: accuracy, TTR, escalation rate  
   - **Success Criteria:** ≥98% accuracy, \< 5% escalation rate

---

### Assumption 2: User Trust

**Assumption:**  
Khách hàng tin tưởng và sẵn sàng để AI tự động kiểm tra & thay thế tài khoản, thay vì yêu cầu hỗ trợ trực tiếp từ chủ shop.

**Risk Level:** 🟡 High

**Validation Plan:**

1. **User Interview (Week 1-2):**  
     
   - Interview 10 buyers: "Bạn có tin AI xử lý bảo hành không?"  
   - **Success Criteria:** ≥60% "Có, nếu nhanh hơn"

   

2. **A/B Test (Week 5-8):**  
     
   - Group A: AI warranty (auto)  
   - Group B: Human warranty (manual)  
   - Track: satisfaction score, refund rate, D7 retention  
   - **Success Criteria:** Group A ≥ Group B

---

### Assumption 3: Cost Efficiency

**Assumption:**  
Chi phí AI Vision ($0.01/request) \+ infrastructure không làm margin âm.

**Risk Level:** 🟢 Medium

**Validation Plan:**

1. **Cost Modeling (Week 1):**  
     
   - Calculate: revenue per order \- AI cost \- infra cost  
   - **Success Criteria:** Gross margin ≥ 60%

   

2. **Pilot Monitoring (Week 5-8):**  
     
   - Track actual cost per order  
   - **Success Criteria:** Actual cost ≤ projected cost

---

## 📊 Product-Market Fit (PMF) Scorecard

### Aha Moment

**Definition:**  
User nhận account mới trong **\<30 giây lúc 2h sáng** (khi không có con người online).

**Why This Matters:**  
Đây là lúc user nhận ra "sản phẩm này khác hẳn" — không cần chờ con người.

---

### Leading Indicator (Predict Future)

**Metric:** D7 Retention Rate

**Definition:** % users quay lại đặt đơn trong 7 ngày

**Target:** ≥ 80%

**Why:** Nếu user quay lại trong 7 ngày → họ trust hệ thống → sẽ trở thành loyal customer.

---

### Lagging Indicator (Confirm Success)

**Metric:** Monthly Recurring Revenue (MRR)

**Target:** $5,000 by Month 6

---

### PMF Test Method

**Sean Ellis Test:**

Survey question:

"Bạn sẽ cảm thấy thế nào nếu AutoAccess biến mất?"

- Rất thất vọng  
- Hơi thất vọng  
- Không thất vọng  
- Không dùng nữa

**PMF Threshold:** ≥40% chọn "Rất thất vọng"

**Timeline:** Run survey sau 30 ngày pilot

---

### Vanity Metrics (Ignore)

- ❌ Traffic website  
- ❌ Tổng số account trong kho  
- ❌ Số lượng features shipped  
- ❌ Model accuracy (nếu không translate thành business outcome)

---

## 🔗 Dependencies & Constraints

### External Dependencies

| Dependency | Type | Risk | Mitigation |
| :---- | :---- | :---- | :---- |
| **VietQR API** | Critical | API down / rate limit | Fallback: Cassie API |
| **OpenAI API (GPT-4o)** | Critical | Pricing change / rate limit | Fallback: Claude Vision / Gemini Vision |
| **SMTP Service** | Important | Email deliverability | Fallback: Telegram-first |
| **Telegram Bot API** | Important | API down | Fallback: SMS (costly) |

### Technical Constraints

- **Latency:** Payment confirmation \< 10s, AI warranty \< 60s  
- **Uptime:** ≥ 99.9% (max 43 minutes downtime/month)  
- **Scalability:** Support 5M requests/month by Month 12  
- **Security:** PCI DSS compliance không cần (không store payment info)

### Legal Constraints

- **Disclaimer:** Shop owner chịu trách nhiệm legal compliance cho việc cho thuê tài khoản  
- **Data Privacy:** Không store ảnh lỗi \> 30 ngày (GDPR-like)  
- **Terms of Service:** Rõ ràng về refund policy

---

## 🛠️ Technical Architecture (High-Level)

### System Components

┌─────────────┐

│   Buyer     │

└──────┬──────┘

       │

       ├─── QR Payment ───→ VietQR API ───→ Webhook

       │                                      │

       └─── Upload Error ─→ Chatbot ─────────┤

                                              │

                                              ▼

                                    ┌──────────────────┐

                                    │  Laravel Backend │

                                    │                  │

                                    │  \- Payment       │

                                    │  \- Inventory     │

                                    │  \- AI Vision     │

                                    │  \- Notification  │

                                    └────────┬─────────┘

                                             │

                    ┌────────────────────────┼────────────────────┐

                    │                        │                    │

                    ▼                        ▼                    ▼

              ┌──────────┐            ┌──────────┐         ┌──────────┐

              │  MySQL   │            │ OpenAI   │         │ Telegram │

              │ Database │            │   API    │         │   Bot    │

              └──────────┘            └──────────┘         └──────────┘

### Tech Stack

| Layer | Technology | Reason |
| :---- | :---- | :---- |
| **Backend** | Laravel 10 | Familiar to team, fast development |
| **Database** | MySQL 8.0 | Reliable, row-level locking |
| **AI** | OpenAI GPT-4o Vision | Best OCR \+ context understanding |
| **Queue** | Redis \+ Laravel Queue | Handle async tasks (email, AI) |
| **Hosting** | AWS EC2 / DigitalOcean | Cost-effective for MVP |
| **Monitoring** | Sentry \+ Laravel Telescope | Error tracking \+ debugging |

---

## 📅 Roadmap & Milestones

### Phase 1: MVP (Month 1-3)

**Goal:** Validate AI warranty với 10 pilot shops

**Milestones:**

- Week 1-2: Collect error screenshots, test AI accuracy  
- Week 3-4: Build payment integration \+ inventory system  
- Week 5-6: Build AI warranty chatbot  
- Week 7-8: Pilot with 5 shops  
- Week 9-12: Iterate based on feedback, expand to 10 shops

**Success Criteria:**

- [ ] 10 pilot shops using daily  
- [ ] ≥98% AI accuracy  
- [ ] \< 60s TTR  
- [ ] ≥70% D7 retention

---

### Phase 2: Scale (Month 4-6)

**Goal:** 100 paying shops, $5k MRR

**Features:**

- Mobile-responsive UI  
- Advanced analytics dashboard  
- Multi-account support for shop owners  
- Referral program

---

### Phase 3: Expand (Month 7-12)

**Goal:** 500 shops, $25k MRR, expand to Thailand

**Features:**

- Mobile app (iOS/Android)  
- Multi-language support  
- Enterprise features (multi-shop management)  
- API for third-party integrations

---

## 🤖 AI Critique Log

### Issue 1: Dashboard Complexity

**Original Plan:** Build full-featured dashboard với charts, analytics, reports

**AI Critique:** Dashboard là nice-to-have, không critical cho MVP. Focus on API-first.

**Action Taken:** ✅ Simplify dashboard → chỉ giữ inventory management \+ low stock alert

---

### Issue 2: AI Vision Spoofing Risk

**Original Plan:** Accept bất kỳ ảnh nào user upload

**AI Critique:** AI Vision có thể bị spoof bằng ảnh fake → mất tài khoản oan

**Action Taken:** ✅ Yêu cầu ảnh phải có:

- Timestamp (từ device)  
- Order ID watermark (system generate)  
- Validate: ảnh upload trong vòng 24h sau khi nhận tài khoản

---

### Issue 3: Cost Optimization

**Original Plan:** Dùng GPT-4o Vision cho mọi request

**AI Critique:** Cost $0.01/request → với 50k requests/month \= $500/month → margin thấp

**Action Taken:** ✅ Implement caching:

- Cache common error patterns  
- Chỉ call GPT-4o khi không match cache  
- Expected cost reduction: 60%

---

## 🧠 Open Questions & Risks

### Open Question 1: Cost Optimization

**Question:**  
Làm sao giảm cost AI Vision từ $0.01/request xuống $0.003/request cho đơn hàng 5k-10k VND?

**Options:**

1. Fine-tune smaller model (Llama 3.2 Vision) → trade-off: accuracy  
2. Implement aggressive caching → trade-off: freshness  
3. Negotiate volume discount với OpenAI → need 1M+ requests/month

**Decision Needed By:** Week 8 (before scaling)

---

### Open Question 2: Telegram Integration Architecture

**Question:**  
Thiết kế luồng Graceful Handover trong Laravel: Event-driven? Queue-based? Webhook?

**Options:**

1. **Event-driven (Laravel Events):**  
   - Pro: Clean code, easy to test  
   - Con: Synchronous, có thể slow  
2. **Queue-based (Laravel Queue \+ Redis):**  
   - Pro: Async, scalable  
   - Con: Complexity, need monitoring  
3. **Webhook (Telegram Bot API):**  
   - Pro: Real-time  
   - Con: Need public endpoint, security concern

**Decision Needed By:** Week 4 (before building AI warranty)

---

### Risk 1: Platform Policy Violation

**Risk:**  
Netflix/Spotify phát hiện pattern "account sharing" → ban hàng loạt tài khoản.

**Likelihood:** Medium  
**Impact:** Critical (lose all inventory)

**Mitigation:**

- Diversify account sources  
- Implement IP rotation  
- Monitor ban rate daily  
- Have 3-day inventory buffer

---

### Risk 2: Payment Fraud

**Risk:**  
User fake screenshot thanh toán → nhận tài khoản free.

**Likelihood:** Low  
**Impact:** Medium (lose revenue)

**Mitigation:**

- Validate payment qua API (không tin screenshot)  
- Implement rate limiting (max 3 orders/phone/day)  
- Blacklist suspicious users

---

### Risk Register Summary (Workshop 2)

- Completed full risk register in `risk_register_v2.md`.
- Includes top 10 risks, likelihood/impact scoring, 2x2 matrix, and mitigation plan.
- Confirms **Customer-facing AI Risk** as the **KILL ZONE** and top priority for Block 3.

---

## 📞 Stakeholder Sign-off

| Stakeholder | Role | Sign-off Date | Status |
| :---- | :---- | :---- | :---- |
| Nguyễn Thanh Bình | Product Owner | 2026-04-24 | ✅ Approved |
| \[Engineering Lead\] | Tech Lead | \[Date\] | ⏳ Pending |
| \[Business Owner\] | CEO | \[Date\] | ⏳ Pending |

---

## 📚 Appendix

### A. User Flow Diagrams

*(To be added: Figma/Miro links)*

### B. API Specifications

*(To be added: Swagger/OpenAPI docs)*

### C. Database Schema

*(To be added: ERD diagram)*

### D. Test Cases

*(To be added: Test plan document)*

---

**Document End**

*For questions or feedback, contact: [binh.nguyen@autoaccess.vn](mailto:binh.nguyen@autoaccess.vn)*  
