## 00 — Chốt phạm vi

**1. Dự án:**  
AI Outfit Copilot — sản phẩm gợi ý outfit từ chính tủ đồ hiện có của người dùng, dựa trên hoàn cảnh, thời tiết và phong cách cá nhân.

**2. Persona:**  
Người quan tâm đến cách ăn mặc và phong cách cá nhân, thường xuyên gặp khó khăn hoặc mất thời gian khi phải chọn outfit phù hợp trước khi ra ngoài.

**3. Core job:**  
> “Mỗi khi chuẩn bị ra ngoài, tôi muốn nhanh chóng chọn được một bộ đồ phù hợp với nơi mình sắp đến và đúng với phong cách của mình, thay vì mất nhiều thời gian thử đi thử lại nhiều bộ.”

# 01 — Core Action

## 1. Phân biệt bốn khái niệm

| Khái niệm | Câu trả lời |
|---|---|
| **Core job** | Khi chuẩn bị ra ngoài, người dùng muốn nhanh chóng chọn được một bộ đồ phù hợp với nơi sắp đến và đúng với phong cách cá nhân, thay vì mất nhiều thời gian thử đi thử lại nhiều bộ. |
| **Core action** | Người dùng chọn một outfit được sản phẩm gợi ý để mặc cho lần ra ngoài hiện tại. |
| **Core value** | Người dùng giảm được thời gian và sự phân vân khi chọn đồ, đồng thời tìm được một outfit đủ phù hợp để thực sự mặc ra ngoài. |
| **Core value event** | `outfit_worn` — người dùng xác nhận rằng họ đã thực sự mặc outfit được sản phẩm gợi ý. |

### Vì sao Core Action và Core Value Event khác nhau?

AI gợi ý outfit chưa có nghĩa người dùng đã nhận được value.

Ngay cả khi user chọn một outfit, họ vẫn có thể:

- thử lên rồi không thích;
- đổi sang outfit khác;
- tự phối lại;
- cuối cùng không mặc outfit AI đề xuất.

Vì vậy hành trình giá trị là:

```text
AI gợi ý outfit
        ↓
User xem recommendation
        ↓
User chọn một outfit
        ↓
outfit_selected
        ↓
User thực sự mặc outfit đó
        ↓
outfit_worn
```

`outfit_selected` là **Core Action** vì đây là hành vi chủ động của user trong sản phẩm để tiến rất gần tới core value.

`outfit_worn` là **Core Value Event** vì nó xác nhận recommendation đã thực sự được áp dụng ngoài đời.

---

## 2. Core Action Card

| Thành phần | Câu trả lời |
|---|---|
| **Target user** | Người quan tâm đến cách ăn mặc và phong cách cá nhân, thường xuyên gặp khó khăn hoặc mất thời gian khi lựa chọn outfit trước khi ra ngoài. |
| **Core job** | Nhanh chóng chọn được một bộ đồ phù hợp với nơi mình sắp đến và đúng với phong cách cá nhân. |
| **Core action** | Chọn một outfit được sản phẩm gợi ý để mặc cho lần ra ngoài hiện tại. |
| **Object** | Một outfit cụ thể được tạo từ các món đồ trong tủ đồ hiện có của người dùng. |
| **Preconditions** | Người dùng đang có nhu cầu chuẩn bị trang phục; sản phẩm có thông tin cơ bản về wardrobe; biết context như nơi đến, hoạt động, thời tiết hoặc phong cách mong muốn; hệ thống đã tạo recommendation. |
| **Completion rule** | Action hoàn tất khi người dùng chủ động xác nhận một outfit là lựa chọn mình dự định mặc, ví dụ nhấn `Wear this`. |
| **Core value** | Người dùng đi đến quyết định mặc gì nhanh hơn và ít phải thử nhiều outfit khác nhau. |
| **Evidence of value** | Người dùng sau đó xác nhận đã thực sự mặc outfit được chọn khi ra ngoài. |
| **Candidate event** | Core Action: `outfit_selected`. Core Value Event: `outfit_worn`. |

---

## 3. Tại sao không chọn các hành vi khác?

### `app_opened`

Không chứng minh người dùng giải quyết được vấn đề chọn đồ.

User có thể mở app rồi thoát.

### `outfit_generated`

Đây là output của hệ thống, không phải value mà user nhận được.

AI có thể tạo 20 outfit nhưng không có bộ nào được dùng.

### `outfit_viewed`

Chỉ chứng minh recommendation được nhìn thấy.

### `outfit_saved`

Có thể chỉ là inspiration cho tương lai, chưa giải quyết nhu cầu hiện tại.

### `outfit_selected`

Người dùng đã chuyển từ:

> “Không biết mặc gì.”

sang:

> “Tôi sẽ mặc bộ này.”

Đây là Core Action.

### `outfit_worn`

Đây là bằng chứng cuối cùng rằng recommendation đủ hữu ích để trở thành hành vi thật.

Đây là Core Value Event.

---

# 4. Tự kiểm Core Action

Core Action:

> **`outfit_selected` — người dùng chọn một outfit được gợi ý để mặc cho lần ra ngoài hiện tại.**

| Tiêu chí | Kết quả | Giải thích |
|---|---|---|
| **1. Gần core value** | ✅ | Khi chọn được outfit, user đã giải quyết phần lớn sự phân vân ban đầu. |
| **2. Có thể lặp lại** | ✅ | Mỗi lần có nhu cầu lựa chọn trang phục mới, hành vi có thể xuất hiện lại. |
| **3. Có thể quan sát** | ✅ | Có thể track chính xác khi user nhấn `Wear this` hoặc xác nhận outfit. |
| **4. Có ý nghĩa** | ✅ | Recommendation dẫn tới lựa chọn outfit nhiều hơn thường cho thấy sản phẩm hữu ích hơn, nhưng vẫn cần `outfit_worn` để xác nhận value thật. |
| **5. Có thể tác động** | ✅ | Team có thể cải thiện recommendation, personalization, context và UX để tăng khả năng outfit được chọn. |

**Kết quả: 5/5 tiêu chí đạt.**

---

## GATE 1 — Core Action đứng vững

**Core Action**

> `outfit_selected`

**Core Value Event**

> `outfit_worn`

Core Action không phải thao tác giao diện chung như mở app hay hỏi AI. Nó đại diện cho một quyết định cụ thể: user đã chọn một recommendation để giải quyết vấn đề “mặc gì”.

---

# 02 — Nature & cadence

## 1. Action Nature Card

| Thành phần | Câu trả lời |
|---|---|
| **Actor** | Một người dùng cá nhân đang chuẩn bị trang phục trước khi ra ngoài. |
| **Intent** | Muốn nhanh chóng quyết định mặc gì mà vẫn phù hợp với địa điểm, hoạt động, thời tiết và phong cách cá nhân. |
| **Trigger** | Chủ yếu xuất phát từ nhu cầu thực tế của người dùng khi chuẩn bị ra ngoài. Occasion, lịch trình, thời tiết hoặc một sự kiện cụ thể có thể kích hoạt nhu cầu. |
| **Effort** | Thấp đến trung bình. Sau khi wardrobe đã được thiết lập, user chỉ cần cung cấp thêm context nếu cần và lựa chọn giữa một số recommendation. Mục tiêu là hoàn thành trong vài phút. |
| **Value timing** | Value xuất hiện gần như ngay khi user chọn được outfit; value được xác nhận sau đó khi outfit thực sự được mặc. |
| **State** | Sản phẩm có thể lưu outfit đã chọn, outfit đã mặc, item được dùng, context của lần mặc và feedback. Dữ liệu này giúp AI hiểu preference tốt hơn theo thời gian. |
| **Dependency** | Phụ thuộc vào việc user thực sự có nhu cầu chọn trang phục, wardrobe hiện tại, context của lần ra ngoài và chất lượng recommendation. Không phụ thuộc vào thành viên khác. |
| **Repeat condition** | Hành vi có lý do xuất hiện lại mỗi khi user chuẩn bị cho một lần ra ngoài mới và cần quyết định outfit. |

---

## 2. Dạng hành vi

Dạng hành vi phù hợp nhất:

> **Phản ứng theo sự kiện, với frequency tương đối cao.**

Trigger tự nhiên không phải:

> “Đã sang ngày mới.”

Mà là:

> **“Tôi sắp ra ngoài và cần quyết định mặc gì.”**

Ví dụ:

```text
Đi làm
   ↓
Cần outfit

Đi cafe
   ↓
Cần outfit

Đi date
   ↓
Cần outfit

Đi sự kiện
   ↓
Cần outfit
```

Một ngày thậm chí có thể có nhiều hơn một outfit opportunity.

Ngược lại, cũng có ngày user không cần AI vì họ đã biết mình muốn mặc gì.

Vì vậy bản chất hành vi phù hợp hơn với **event-driven** thay vì ép thành daily habit.

---

## 3. Nature vs Nurture

### Nature

Nhu cầu tự nhiên:

> “Tôi sắp ra ngoài nhưng chưa biết mặc gì.”

Sản phẩm không tạo ra nhu cầu đó.

Nó chỉ giúp người dùng giải quyết quyết định nhanh hơn.

### Nurture

Nurture có thể hỗ trợ đúng lúc, ví dụ:

> “Chiều nay có mưa, bạn có muốn điều chỉnh outfit không?”

hoặc:

> “Bạn đã chọn outfit cho buổi tối chưa?”

Nhưng notification không nên trở thành:

> “Bạn chưa tạo outfit hôm nay.”

Nếu user không có nhu cầu lựa chọn đồ, việc ép họ mở app không tạo thêm core value.

---

## 4. Frequency cao hơn có luôn tốt hơn không?

Không.

Ví dụ:

### User A

```text
7 outfit sessions
20 recommendations/session
2 outfit_worn
```

### User B

```text
4 outfit sessions
3 recommendations/session
4 outfit_worn
```

User B có khả năng nhận nhiều value hơn.

Do đó, sản phẩm không nên tối ưu:

- thời gian trong app;
- số outfit generate;
- số session;
- số lần mở app.

Mà nên tập trung vào khả năng chuyển từ:

```text
Need outfit
     ↓
Recommendation
     ↓
outfit_selected
     ↓
outfit_worn
```

---

# 5. Kết luận cadence

> Đối với **người quan tâm đến phong cách cá nhân và thường gặp khó khăn khi lựa chọn trang phục trước khi ra ngoài**, core action **chọn một outfit được sản phẩm gợi ý để mặc** thường xuất hiện **mỗi khi người dùng có một nhu cầu lựa chọn trang phục mới** vì **mỗi lần ra ngoài với bối cảnh, hoạt động hoặc thời tiết khác nhau đều có thể tạo ra một quyết định outfit mới**. Do đó, nhịp đo phù hợp là **theo từng outfit opportunity**, ở cấp **user**.

### Dạng hành vi

**Phản ứng theo sự kiện**

### Nhịp chính

**Theo từng outfit opportunity**

### Đơn vị

**User**

---

## Có nên theo dõi Daily không?

Có thể dùng daily như một **reporting window**, nhưng không nên nhầm nó với bản chất của hành vi.

Ví dụ có thể báo cáo:

> Daily Successful Outfit Decisions

nhưng underlying opportunity vẫn là:

```text
một lần user cần quyết định outfit
```

Điều này giúp tránh lỗi:

> user hôm nay không dùng app = churn.

Có thể đơn giản hôm đó họ không có nhu cầu.

---

# GATE 2 — Cadence từ Nature

**Nature**

> User cần quyết định outfit khi chuẩn bị cho một lần ra ngoài.

**Cadence**

> Theo từng `outfit opportunity`.

**Lý do**

> Nhu cầu phát sinh từ đời sống thật của user, không phải từ lịch của sản phẩm.

**Nurture**

> Chỉ hỗ trợ user hoàn thành một outfit decision đang tồn tại; không tạo artificial daily habit.

# 03 — Metric System

## 1. Activation Metric

### Start event
`wardrobe_ready`

Được ghi nhận khi người dùng đã thêm đủ số lượng item tối thiểu để hệ thống có thể tạo một outfit recommendation có ý nghĩa.

Ví dụ MVP có thể yêu cầu:

- ít nhất 3 tops;
- ít nhất 2 bottoms;
- ít nhất 1 đôi giày.

Mục tiêu của start event không phải chứng minh value, mà xác định thời điểm user đã **sẵn sàng sử dụng core use case**.

---

### Activation event

`outfit_worn`

Activation xảy ra khi người dùng lần đầu tiên xác nhận rằng họ đã thực sự mặc một outfit được sản phẩm gợi ý.

Lý do:

`outfit_generated` chưa chứng minh value.

`outfit_selected` cho thấy user đã đi tới một quyết định, nhưng vẫn có thể đổi ý.

`outfit_worn` là bằng chứng gần nhất cho thấy recommendation của sản phẩm đã đi vào hành vi thực tế.

---

### Time window

**Initial measurement window: trong vòng 7 ngày kể từ `wardrobe_ready` — cần được validate bằng user research / dữ liệu thực tế.**

Lý do chọn window này:

Persona mục tiêu thường xuyên gặp nhu cầu lựa chọn outfit trước khi ra ngoài. Nếu trong một tuần sau khi setup wardrobe mà user vẫn chưa mặc bất kỳ outfit nào do sản phẩm gợi ý, khả năng onboarding hoặc recommendation chưa tạo đủ value là đáng lo.

Activation metric có thể viết:

> **7-day Outfit Activation Rate**  
> = % user đạt `outfit_worn` ít nhất một lần trong vòng 7 ngày kể từ `wardrobe_ready`.

Ví dụ:

```text
100 users đạt wardrobe_ready

↓

72 users có ít nhất 1 outfit_worn
trong 7 ngày tiếp theo

Activation Rate = 72%
```

---

## Active ≠ Activated

Hai khái niệm cần tách rõ.

### Active user

Trong Metrics Pack này, **Weekly Active Outfit User** được định nghĩa là user có ít nhất một `recommendation_shown` trong tuần đo.

Định nghĩa này giúp denominator của các metric theo tuần có event contract rõ ràng. Một user có thể active nhưng chưa activated nếu họ đã xem recommendation nhưng chưa từng đạt `outfit_worn`.

### Activated user

User đã trải nghiệm core value ít nhất một lần:

> `outfit_worn`

Một user có thể:

```text
Mở app
↓
Xem 10 outfits
↓
Save 3
↓
Không mặc outfit nào
```

User đó là **active**, nhưng chưa **activated**.

---

# 2. Engagement Metrics

Chọn hai góc:

## A. Frequency — Worn Outfit Frequency

Đo:

> Số `outfit_worn` trung bình trên mỗi active user trong một natural measurement window.

Ví dụ theo tuần:

```text
User A: 4 outfit_worn
User B: 2
User C: 5
```

Metric:

> **Average Worn Outfits per Active User / Week**

Lý do:

Core value có thể lặp lại nhiều lần khi user có các outfit opportunity khác nhau.

Tuy nhiên metric này không nên được tối ưu một cách mù quáng, vì user có nhiều occasion hơn không nhất thiết sản phẩm tốt hơn.

---

## B. Depth — Wear-through Rate

Đo:

> Tỷ lệ outfit được user chọn rồi thực sự mặc.

Công thức:

```text
Wear-through Rate
=
outfit_worn
/
outfit_selected
```

Ví dụ:

```text
100 outfit_selected

↓

76 outfit_worn

Wear-through Rate = 76%
```

Metric này phản ánh chất lượng recommendation tốt hơn số lượt generate.

Nếu user thường xuyên nhấn `Wear this` nhưng sau đó đổi ý, sản phẩm đang tạo **decision giả**, chưa tạo value thật.

---

# 3. North Star Metric

## Proposed NSM

> **Successful Outfit Wears per Active User per Week**

Một Successful Outfit Wear được tính khi:

1. user nhận một outfit recommendation;
2. user chọn outfit đó;
3. user xác nhận đã thực sự mặc;
4. outfit không nhận negative feedback ngay sau đó.

### Unit of value

Một **outfit thực sự được mặc**.

### Quality threshold

Một **Successful Outfit Wear** chỉ được tính khi:

- có `outfit_worn`; và
- user đã gửi `outfit_feedback_submitted`; và
- feedback thuộc `{positive, neutral}`.

Nếu user chưa gửi feedback, lần mặc đó vẫn được tính vào `outfit_worn` nhưng **chưa được tính là Successful Outfit Wear**.

### Frequency

Số Successful Outfit Wears trên mỗi active user trong một tuần.

---

### Công thức

```text
NSM
=
Successful Outfit Wears
/
Active Users
/
Week
```

Ví dụ:

```text
500 active users

1,350 outfits được mặc

1,180 trong số đó
không nhận negative feedback

↓

NSM = 2.36
Successful Outfit Wears
per Active User / Week
```

---

## Vì sao không dùng số outfit generated?

Vì có thể game metric:

```text
AI tạo 100 outfits
↓
User không mặc cái nào
```

Metric tăng nhưng value bằng 0.

NSM phải gắn với hành vi thực tế:

> user đã sử dụng recommendation để giải quyết quyết định mặc gì.

---

# 4. Leading Indicators

## Leading indicator 1 — Outfit Selection Rate

```text
outfit_selected
/
recommendation_sessions
```

### Vì sao tin nó dự báo core action lặp lại?

Nếu recommendation thường xuyên khiến user đi tới một lựa chọn cụ thể, khả năng outfit đó tiếp tục chuyển thành `outfit_worn` sẽ cao hơn.

Nếu user xem nhiều recommendation nhưng không chọn gì, chất lượng recommendation có thể chưa đủ tốt.

---

## Leading indicator 2 — Time to Outfit Decision

Đo thời gian median từ:

```text
recommendation_shown
↓
outfit_selected
```

### Vì sao tin nó dự báo core action lặp lại?

Core job của sản phẩm là giảm sự phân vân và thời gian chọn đồ.

Nếu user ngày càng quyết định outfit nhanh hơn mà Wear-through Rate không giảm, sản phẩm đang giải quyết pain tốt hơn và có khả năng được dùng lại ở occasion tiếp theo.

---

## Leading indicator 3 — Positive Post-Wear Feedback Rate

```text
positive_feedback
/
outfit_worn
```

Ví dụ feedback:

```text
 Loved it
 Worked well
 Didn't work
```

### Vì sao tin nó dự báo core action lặp lại?

User không chỉ mặc recommendation mà còn cảm thấy nó phù hợp sẽ có lý do mạnh hơn để tin AI ở lần chọn outfit tiếp theo.

---

# 5. Counter-metrics

## Counter-metric 1 — Negative Outfit Rate

```text
negative_feedback
/
outfit_worn
```

Core action có thể tăng nhưng nếu ngày càng nhiều user nói:

> “Mặc rồi nhưng không hợp.”

thì value thực sự đang giảm.

Ví dụ:

```text
Month 1

outfit_worn ↑ 20%
negative rate = 8%

Month 2

outfit_worn ↑ 35%
negative rate = 24%
```

Không thể kết luận Month 2 tốt hơn.

---

## Counter-metric 2 — Recommendation Ignore Rate

```text
sessions_without_selection
/
recommendation_sessions
```

Nếu hệ thống cố tạo quá nhiều outfit hoặc recommendation kém phù hợp, tỷ lệ bị bỏ qua sẽ tăng.

---

## Counter-metric 3 — Time to Decision

Không nên để:

```text
outfit_worn ↑
```

nhưng:

```text
time to decision ↑ mạnh
```

Nếu user phải dành 20 phút để xem 30 recommendation mới chọn được một bộ, sản phẩm đang đi ngược core job ban đầu.

---

# 04 — Retention Definition

## 1. Retention Definition

| Thành phần | Định nghĩa |
|---|---|
| **Unit** | User |
| **Cohort entry** | User đạt `outfit_worn` lần đầu tiên và trở thành activated user. |
| **Return event** | User có thêm ít nhất một `outfit_worn` trong một outfit opportunity tiếp theo. |
| **Window** | **Initial retention window: Weekly** — giả thuyết ban đầu vì use case có thể phát sinh nhiều lần trong tuần nhưng không nhất thiết mỗi ngày; cần validate bằng frequency thực tế của `outfit opportunity`. |
| **Threshold** | Ít nhất 1 `outfit_worn` trong tuần đo retention. |
| **Segment** | Activated users thuộc persona mục tiêu: người quan tâm đến phong cách cá nhân và thường xuyên gặp khó khăn hoặc mất thời gian lựa chọn outfit trước khi ra ngoài. |

---

## 2. Retention Definition đầy đủ

> **Weekly Outfit Retention (initial hypothesis)** là tỷ lệ user đã có `outfit_worn` đầu tiên trong cohort week và tiếp tục có ít nhất một `outfit_worn` trong tuần tiếp theo.

Ví dụ:

```text
Week 0

100 users
first outfit_worn
↓

Week 1

62 users
có outfit_worn khác

↓

Week 1 Retention = 62%
```

---

## 3. Vì sao không dùng D1 retention?

Không phải ngày nào user cũng có:

> một outfit decision đủ khó để cần AI.

Nếu hôm sau user:

- ở nhà;
- mặc uniform;
- đã biết sẵn outfit;
- hoặc không có occasion mới,

thì không quay lại chưa chắc là churn.

Do đó D1 dễ tạo false negative.

---

## 4. Vì sao Weekly Retention phù hợp hơn?

Một tuần bao phủ được nhiều context tự nhiên:

```text
Work
School
Cafe
Date
Weekend
Event
```

và tăng khả năng user có ít nhất một outfit opportunity mới.

Vì vậy weekly window có khả năng gần natural cycle hơn daily.

---

# 5. Retention nên đọc cùng ba mốc

## A. Natural cycle

Cần kiểm chứng:

> Persona thực sự gặp bao nhiêu outfit opportunity mỗi tuần?

Nếu user interview cho thấy trung bình 3–5 lần/tuần thì weekly retention đứng vững.

---

## B. Cohort đúng segment

Không nên trộn:

```text
fashion enthusiast
```

với:

```text
người chỉ thử app vì tò mò
```

Nếu hai nhóm có motivation khác nhau, retention sẽ rất khác.

---

## C. Category benchmark

Chỉ so retention với các sản phẩm có nature tương tự như:

- fashion utility;
- wardrobe apps;
- personal styling;
- recurring consumer utility.

Không nên lấy benchmark của:

- social media;
- messaging;
- games;

vì các category này có natural frequency hoàn toàn khác.

---

# 6. Metric System tổng thể

```text
                    ACTIVATION

wardrobe_ready
      ↓
outfit_selected
      ↓
outfit_worn
      ↓
Activated


                    ENGAGEMENT

How often?
↓
Worn Outfit Frequency

How good?
↓
Wear-through Rate


                    NORTH STAR

Successful Outfit Wears
per Active User / Week


                    RETENTION

First outfit_worn
      ↓
next week
      ↓
another outfit_worn


                    COUNTER-METRICS

Negative Outfit Rate
Recommendation Ignore Rate
Time to Outfit Decision
```

---

# GATE 3 — Metric tính được, retention đủ nghĩa

## Activation

**Start event:** `wardrobe_ready`

**Activation event:** `outfit_worn`

**Window:** initial window = 7 ngày, cần validate bằng user research / dữ liệu thực tế.

---

## Engagement

**Frequency:** Worn Outfit Frequency

**Depth:** Wear-through Rate

---

## Retention

**Unit:** User  
**Cohort:** first `outfit_worn`  
**Return:** another `outfit_worn`  
**Window:** initial weekly window, cần validate với natural cycle  
**Threshold:** ≥ 1  
**Segment:** target persona đã activated

---

## North Star Metric

> **Successful Outfit Wears per Active User per Week**

Unit of value:

> outfit được mặc.

Quality threshold:

> không nhận negative feedback.

Frequency:

> per active user per week.

---

## Leading indicators

1. Outfit Selection Rate  
2. Median Time to Outfit Decision  
3. Positive Post-Wear Feedback Rate

---

## Counter-metrics

1. Negative Outfit Rate  
2. Recommendation Ignore Rate  
3. Median Time to Outfit Decision

# 05 — Product Loop

## 1. Loại loop chính

**Event-response loop**

Lý do: sản phẩm không tạo ra nhu cầu mặc đồ. Loop bắt đầu khi người dùng có một trigger tự nhiên:

> “Tôi chuẩn bị ra ngoài và cần quyết định mặc gì.”

Sản phẩm phản ứng với nhu cầu đó bằng recommendation, sau đó học từ lựa chọn thực tế của user để recommendation ở lần tiếp theo tốt hơn.

---

## 2. Product Loop — Chu kỳ 1

```text
Natural trigger
User chuẩn bị ra ngoài và chưa biết mặc gì
        ↓
AI tạo outfit recommendation
        ↓
Core action
User chọn một outfit
        ↓
outfit_selected
        ↓
User thực sự mặc outfit
        ↓
outfit_worn
        ↓
Immediate value
User nhanh chóng có được outfit phù hợp
và giảm thời gian phân vân
        ↓
Saved state / investment
Lưu:
- outfit đã mặc
- item đã sử dụng
- occasion
- thời tiết
- preference
- feedback
```

Ở chu kỳ đầu tiên, sản phẩm tạo value bằng cách giúp user đi từ:

> “Không biết mặc gì”

sang:

> “Tôi đã mặc bộ này.”

---

# 3. Product Loop — Chu kỳ 2

Khi nhu cầu tiếp theo xuất hiện:

```text
Next natural trigger
User chuẩn bị cho một lần ra ngoài mới
        ↓
AI sử dụng dữ liệu đã lưu
        ↓
Biết rõ hơn:
- user thích style nào
- item nào thường được chọn
- outfit nào từng bị reject
- context nào phù hợp
        ↓
Recommendation tốt hơn
        ↓
Core action tiếp theo
outfit_selected
        ↓
outfit_worn
        ↓
Repeat value
User quyết định outfit nhanh hơn
và recommendation phù hợp hơn
        ↓
Thêm dữ liệu mới được lưu
        ↓
Recommendation tiếp tục cải thiện
```

Loop đầy đủ:

```text
Need outfit
    ↓
Recommendation
    ↓
Select
    ↓
Wear
    ↓
Feedback / behavior data
    ↓
Taste model improves
    ↓
Next outfit need
    ↓
Better recommendation
    ↓
Select
    ↓
Wear
```

---

## 4. Reason to return

Nếu bỏ toàn bộ notification, lý do user quay lại vẫn tồn tại:

> Người dùng lại gặp một tình huống mới mà họ cần quyết định mặc gì.

Đồng thời, sản phẩm có thêm reason to return thứ hai:

> Recommendation ngày càng hiểu gu và wardrobe của họ hơn nhờ dữ liệu từ những lần sử dụng trước.

Vì vậy loop không phụ thuộc vào streak, badge hay reminder.

---

## 5. Metric Hypothesis

Đây là câu hypothesis bạn có thể dùng làm bản nháp để tự chỉnh:

> **Nếu product loop hoạt động, metric Successful Outfit Wears per Active User per Week sẽ tăng theo thời gian trong các cohort người dùng đã activated, vì mỗi lần user thực sự mặc một outfit sẽ tạo thêm dữ liệu về preference và context, giúp recommendation ở những outfit opportunity tiếp theo chính xác hơn và có khả năng tiếp tục được mặc cao hơn.**

Metric liên quan:

> **North Star Metric — Successful Outfit Wears per Active User per Week**

Supporting metrics có thể cùng cải thiện:

```text
Wear-through Rate ↑

Positive Post-Wear Feedback Rate ↑

Median Time to Outfit Decision ↓
```

---

# 06 — Tracking nhanh

## 1. Core Events

| Tên event | Ý nghĩa | Thời điểm ghi nhận | Metric sử dụng |
|---|---|---|---|
| `wardrobe_ready` | Wardrobe đã có đủ dữ liệu tối thiểu để sản phẩm tạo recommendation có ý nghĩa. | Chỉ ghi khi wardrobe lần đầu đạt điều kiện tối thiểu đã định nghĩa. | 7-day Outfit Activation Rate |
| `recommendation_shown` | Một recommendation session đã tạo xong và ít nhất một outfit thực sự được hiển thị cho user. | Khi recommendation render thành công trên màn hình của user. | Outfit Selection Rate, Recommendation Ignore Rate, Time to Outfit Decision |
| `outfit_selected` | User đã chọn một outfit cụ thể làm lựa chọn dự định mặc cho occasion hiện tại. | Khi outfit chuyển từ trạng thái chưa được chọn → được user xác nhận `Wear this`. | Core Action, Wear-through Rate, Outfit Selection Rate, Time to Outfit Decision |
| `outfit_worn` | User xác nhận họ thực sự đã mặc outfit được recommend. | Chỉ ghi sau khi user xác nhận outfit đã được mặc, không ghi tại thời điểm chọn. | Activation, NSM, Worn Outfit Frequency, Wear-through Rate, Retention |
| `outfit_feedback_submitted` | User đã đánh giá trải nghiệm thực tế sau khi mặc outfit. | Khi user submit feedback sau `outfit_worn`. | Positive Post-Wear Feedback Rate, Negative Outfit Rate, NSM quality threshold |
| `recommendation_session_ended` | Một outfit decision session kết thúc mà user có hoặc không chọn outfit. | Khi session được đóng hoặc timeout theo rule đã định nghĩa. | Recommendation Ignore Rate |

---

# 2. Event → Metric Map

## Activation

```text
wardrobe_ready
      ↓
outfit_worn
```

Tính:

> 7-day Outfit Activation Rate

---

## Outfit Selection Rate

```text
outfit_selected
/
recommendation sessions
```

Events:

- `recommendation_shown`
- `outfit_selected`

---

## Wear-through Rate

```text
outfit_worn
/
outfit_selected
```

Events:

- `outfit_selected`
- `outfit_worn`

---

## Time to Outfit Decision

```text
timestamp(outfit_selected)
-
timestamp(recommendation_shown)
```

Events:

- `recommendation_shown`
- `outfit_selected`

---

## Successful Outfit Wears

Dùng:

```text
outfit_worn
+
outfit_feedback_submitted
```

Một outfit được tính là Successful Outfit Wear khi:

```text
outfit_worn = true

AND

outfit_feedback_submitted = true

AND

feedback_type ∈ {positive, neutral}
```

Nếu chưa có feedback, event `outfit_worn` vẫn hợp lệ cho activation, engagement và retention nhưng chưa đủ điều kiện để tính vào NSM.

---

## Retention

Cohort entry:

```text
first outfit_worn
```

Return event:

```text
another outfit_worn
```

Từ cùng event `outfit_worn`, nhưng xảy ra trong các window khác nhau.

---

# 3. Acceptance Criteria

## AC1 — `outfit_selected` không được ghi quá sớm

Với mỗi `user_id + recommendation_session_id`, hệ thống chỉ ghi `outfit_selected` khi user thực sự xác nhận một outfit là lựa chọn để mặc.

Các hành vi sau **không** được tạo event:

- chỉ xem outfit;
- scroll qua outfit;
- mở detail;
- save outfit;
- hover/tap preview.

Nếu user đổi từ Outfit A sang Outfit B, trạng thái selection cuối cùng phải được lưu chính xác để phân tích hành vi.

---

## AC2 — `outfit_worn` chỉ ghi khi có xác nhận thực tế

`outfit_worn` chỉ được ghi khi user xác nhận rằng outfit đã thực sự được mặc.

Nhấn `Wear this`:

```text
→ outfit_selected
```

không được tự động tạo:

```text
→ outfit_worn
```

Hai event phải được tách biệt.

---

## AC3 — Không duplicate event do reload/retry

Với cùng:

```text
user_id
outfit_id
occasion_id
wear_instance_id
```

một lần mặc chỉ được ghi **một `outfit_worn`**.

Các trường hợp sau không được tạo thêm event:

- reload trang;
- retry API;
- reopen app;
- autosave;
- network reconnect.

---

## AC4 — Feedback chỉ hợp lệ sau khi outfit đã được mặc

`outfit_feedback_submitted` chỉ được tính vào Post-Wear Feedback metric nếu tồn tại một `outfit_worn` hợp lệ trước đó cho cùng wear instance.

Không cho feedback trước khi user thực sự mặc outfit làm sai quality metric.

---

# 4. Properties tối thiểu nên lưu

Nếu làm tracking thật, các event chính nên có:

```text
user_id
outfit_id
recommendation_session_id
occasion_id
timestamp
```

Với `outfit_worn` có thể thêm:

```text
weather_context
occasion_type
items_count
recommendation_rank
```

Với feedback:

```text
feedback_type
reason
```

Ví dụ:

```text
feedback_type:
positive
neutral
negative
```

---

# 5. Tổng Product Loop + Tracking

```text
Natural need
"Tôi sắp ra ngoài"
        ↓
recommendation_shown
        ↓
outfit_selected
        ↓
outfit_worn
        ↓
outfit_feedback_submitted
        ↓
Taste / wardrobe state updated
        ↓
Next natural need
        ↓
Better recommendation
        ↓
outfit_selected
        ↓
outfit_worn
```

Các event được chọn đều map trực tiếp về metric ở Phase 3.

Không track các click không giúp tính metric như:

```text
tab_clicked
button_hovered
screen_scrolled
AI_prompt_typed
```

nếu chúng không phục vụ một câu hỏi đo lường cụ thể.

---

# GATE 4 — Loop nối metric, event nối loop

**Loop:** Event-response loop

**Core loop:**

> Need → Recommend → Select → Wear → Learn → Better recommendation → Wear again

**Metric hypothesis:**

> Nếu loop hoạt động, Successful Outfit Wears per Active User per Week sẽ tăng vì recommendation ngày càng phù hợp hơn với preference và context thực tế của user.

**Core events:** 6

**Mọi event đều map được về ít nhất một metric của Phase 3.**

# 07 — Tự soi lỗi & Revision

## 1. Core action không phải thao tác giao diện hay output hệ thống?

**Đạt.**

Core Action là:

> `outfit_selected`

Đây không phải hành vi như mở app, đăng nhập hoặc xem recommendation. Nó thể hiện người dùng đã đưa ra một quyết định cụ thể cho nhu cầu “mặc gì”.

Core Value Event là:

> `outfit_worn`

Event này xác nhận recommendation đã được áp dụng trong đời thực.

---

## 2. Activation không phải onboarding hay đăng nhập?

**Đạt.**

Activation không dùng:

- account created;
- onboarding completed;
- wardrobe setup completed.

Activation chỉ xảy ra khi:

> người dùng có `outfit_worn` đầu tiên trong window đã định nghĩa.

`wardrobe_ready` chỉ là start event, không phải activation.

---

## 3. Frequency có bị cao hơn nhu cầu thật không?

**Đạt, nhưng cần tiếp tục validate bằng user research.**

Không mặc định user phải dùng sản phẩm hàng ngày.

Nature đã được xác định là:

> **event-response**

Core action xuất hiện khi có một **outfit opportunity**:

> người dùng chuẩn bị ra ngoài và cần quyết định mặc gì.

Daily hoặc weekly chỉ có thể được dùng như reporting window nếu phù hợp với dữ liệu thực tế.

---

## 4. Loop có reason to return ngoài notification?

**Đạt.**

Reason to return chính là:

> Người dùng có một outfit opportunity mới.

Reason to return thứ hai là:

> Sản phẩm hiểu preference và wardrobe của user tốt hơn sau mỗi lần sử dụng, nên recommendation ở lần tiếp theo có thể phù hợp hơn.

Loop không phụ thuộc vào:

- streak;
- badge;
- push notification.

Notification chỉ đóng vai trò nurture.

---

## 5. Retention có dùng window phù hợp với cadence?

**Đạt, với một giả thuyết cần kiểm chứng.**

Retention hiện được đo theo:

> **Weekly Outfit Retention**

Lý do là một tuần có khả năng chứa nhiều outfit opportunities tự nhiên hơn một ngày.

Không sử dụng D1 retention vì không có nhu cầu mới vào ngày tiếp theo không đồng nghĩa với churn.

Weekly window cần được kiểm chứng bằng dữ liệu hoặc phỏng vấn user thật.

---

## 6. Mọi event có map về ít nhất một metric?

Sau khi rà soát, có một event cần chỉnh.

### Event nên bỏ khỏi core tracking

`outfit_rejected`

Lý do:

Event này hữu ích cho personalization nhưng trong Metric System hiện tại chưa được dùng trực tiếp để tính một metric chính thức.

Theo rule:

> Event nào không map được về metric thì bỏ.

Do đó core event set được rút từ 7 xuống còn **6 events**.

### Core events cuối cùng

| Event | Metric |
|---|---|
| `wardrobe_ready` | Activation Rate |
| `recommendation_shown` | Outfit Selection Rate, Ignore Rate, Time to Decision |
| `outfit_selected` | Core Action, Selection Rate, Wear-through Rate |
| `outfit_worn` | Activation, NSM, Engagement, Retention |
| `outfit_feedback_submitted` | Positive Feedback Rate, Negative Outfit Rate, NSM quality threshold |
| `recommendation_session_ended` | Recommendation Ignore Rate |

---

## 7. Mỗi metric đều có event để tính?

**Đạt.**

### Activation Rate

```text
wardrobe_ready
+
outfit_worn
```

### Outfit Selection Rate

```text
recommendation_shown
+
outfit_selected
```

### Wear-through Rate

```text
outfit_selected
+
outfit_worn
```

### Time to Outfit Decision

```text
recommendation_shown
+
outfit_selected
+
timestamp
```

### Successful Outfit Wears

```text
outfit_worn
+
outfit_feedback_submitted
```

### Positive / Negative Outfit Rate

```text
outfit_feedback_submitted
```

### Weekly Retention

```text
first outfit_worn
+
subsequent outfit_worn
```

### Recommendation Ignore Rate

```text
recommendation_shown
+
recommendation_session_ended
+
absence of outfit_selected
```

---

# Revision Log

### Revision 1 — Cadence

**Trước:**

Có lúc giả định sản phẩm có daily cadence vì người dùng mặc đồ mỗi ngày.

**Sau:**

Chuyển sang:

> **event-response theo từng outfit opportunity.**

**Lý do:**

Mặc quần áo mỗi ngày không đồng nghĩa với việc mỗi ngày user đều cần hỗ trợ chọn outfit. Cadence phải xuất phát từ nhu cầu thật, không từ mong muốn tạo daily habit.

---

### Revision 2 — Core Action và Core Value Event

Tách:

```text
outfit_selected
```

thành **Core Action**

và:

```text
outfit_worn
```

thành **Core Value Event**.

**Lý do:**

Một outfit được chọn chưa chắc được mặc. `outfit_worn` là bằng chứng mạnh hơn rằng recommendation đã tạo ra value ngoài đời thực.

---

### Revision 3 — Tracking

Loại:

```text
outfit_rejected
```

khỏi bộ core events.

**Lý do:**

Event chưa map trực tiếp về metric Phase 3. Có thể giữ lại trong tracking mở rộng cho personalization sau này, nhưng không thuộc Metrics Pack hiện tại.

---

# Gate 5 — Kết luận

| Kiểm tra | Kết quả |
|---|---|
| Core Action gần value | ✅ |
| Activation gắn với first value | ✅ |
| Frequency không vượt nature | ✅ |
| Loop có natural reason to return | ✅ |
| Retention window phù hợp cadence | ✅ |
| Mọi event map về metric | ✅ |
| Mọi metric có event để tính | ✅ |

