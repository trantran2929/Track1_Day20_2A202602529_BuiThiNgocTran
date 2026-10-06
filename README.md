# Track1 Day 20 — Metrics Pack

## Thông tin học viên

- **Họ và tên:** Bùi Thị Ngọc Trân
- **MHV:** 2A202602529

---

## Dự án chọn làm

### AI Outfit Copilot

AI Outfit Copilot là sản phẩm gợi ý outfit từ chính tủ đồ hiện có của người dùng, dựa trên hoàn cảnh, thời tiết và phong cách cá nhân.

### Persona

Người quan tâm đến cách ăn mặc và phong cách cá nhân, thường xuyên gặp khó khăn hoặc mất thời gian khi phải chọn outfit phù hợp trước khi ra ngoài.

### Core job

> “Mỗi khi chuẩn bị ra ngoài, tôi muốn nhanh chóng chọn được một bộ đồ phù hợp với nơi mình sắp đến và đúng với phong cách của mình, thay vì mất nhiều thời gian thử đi thử lại nhiều bộ.”

---

## Metrics Pack

**Link Metrics Pack:** [https://drive.google.com/file/d/1qa0haJ7ynehqhoAozr-uMy8_6kvl6EwA/view?usp=sharing](Link Drive)

Metrics Pack gồm:

- `00 — Dự án, persona, core job`
- `01 — Core Action Card`
- `02 — Action Nature Card + kết luận cadence`
- `03 — Metric System`
- `04 — Retention Definition`
- `05 — Product Loop`
- `06 — Tracking nhanh`

Core logic của bài:

```text
Core job
→ Core action
→ Nature & cadence
→ Metric system
→ Retention
→ Product loop
→ Tracking
```

---

## Tóm tắt quyết định chính

### Core Action

`outfit_selected`

Người dùng chọn một outfit được sản phẩm gợi ý để mặc cho lần ra ngoài hiện tại.

### Core Value Event

`outfit_worn`

Người dùng xác nhận rằng họ đã thực sự mặc outfit được sản phẩm gợi ý.

Việc tách hai event này giúp phân biệt rõ giữa:

- **ý định sử dụng recommendation**;
- và **value thực sự xảy ra ngoài đời**.

### Nature & cadence

Hành vi được xem là **event-response**.

Trigger tự nhiên xuất hiện khi người dùng có một `outfit opportunity`:

> “Tôi sắp ra ngoài và cần quyết định mặc gì.”

Do đó, cadence chính không bị ép thành daily. Daily/weekly chỉ được dùng như measurement window khi phù hợp với dữ liệu thực tế.

### North Star Metric

**Successful Outfit Wears per Active User per Week**

Một Successful Outfit Wear được tính khi:

- có `outfit_worn`;
- user đã gửi feedback sau khi mặc;
- feedback là `positive` hoặc `neutral`.

### Retention

Retention được đo theo **Weekly Outfit Retention** như một giả thuyết ban đầu, cần tiếp tục validate bằng frequency thực tế của `outfit opportunity`.

---

## Điều tôi mang về áp dụng cho dự án thật

Điều quan trọng nhất tôi rút ra là metric không nên bắt đầu từ những con số phổ biến như DAU, MAU hay số lượt sử dụng AI.

Metric cần bắt đầu từ câu hỏi:

> **Hành vi nào chứng minh người dùng thực sự nhận được value?**

Trong AI Outfit Copilot, việc AI tạo ra một outfit chưa có nghĩa người dùng đã nhận được value. Ngay cả khi người dùng chọn outfit, họ vẫn có thể đổi ý.

Vì vậy tôi tách:

- `outfit_selected` — Core Action;
- `outfit_worn` — Core Value Event.

Từ đó các metric phía sau như activation, engagement, retention, North Star Metric và tracking đều có thể nối ngược về cùng một core value.

Tôi cũng nhận ra rằng cadence không nên được suy ra từ dashboard hoặc từ giả định “người dùng mặc đồ mỗi ngày”. Nhu cầu thật xuất hiện khi người dùng có một `outfit opportunity` và thực sự cần hỗ trợ chọn đồ.

Điều này giúp tôi nhìn product metrics như một chuỗi quyết định có logic:

```text
Use case
→ Core action
→ Nature
→ Metric
→ Retention
→ Loop
→ Event
```

thay vì chọn metric trước rồi cố giải thích ngược lại.

---


