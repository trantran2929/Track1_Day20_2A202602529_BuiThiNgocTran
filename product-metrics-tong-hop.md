# Product Metrics — Tổng hợp bài học

> **Ý chính:** Metrics giúp team hiểu người dùng có nhận được giá trị hay không, tìm chỗ cần cải thiện và kiểm tra quyết định sản phẩm bằng dữ liệu.

Tài liệu tổng hợp từ nội dung bạn cung cấp trong file ghi chú và các đoạn bài giảng trong cuộc trò chuyện. Các con số là ví dụ học tập; các trường hợp doanh nghiệp được trình bày theo bài học, không phải xác nhận về chỉ số họ đang sử dụng hiện nay.

## Mục lục

1. [Vì sao sản phẩm cần metrics?](#1-vì-sao-sản-phẩm-cần-metrics)
2. [Phễu đo lường và cách tìm điểm nghẽn](#2-phễu-đo-lường-và-cách-tìm-điểm-nghẽn)
3. [Các chỉ số nền tảng và công thức](#3-các-chỉ-số-nền-tảng-và-công-thức)
4. [Activation và Time to Value](#4-activation-và-time-to-value)
5. [Cohort và Retention](#5-cohort-và-retention)
6. [CAC, LTV và thời gian hoàn vốn](#6-cac-ltv-và-thời-gian-hoàn-vốn)
7. [Activated, Active và Core user](#7-activated-active-và-core-user)
8. [Thống nhất định nghĩa metric](#8-thống-nhất-định-nghĩa-metric)
9. [North Star Metric và ba nhóm giá trị](#9-north-star-metric-và-ba-nhóm-giá-trị)
10. [Input metrics: phân rã North Star](#10-input-metrics-phân-rã-north-star)
11. [Leading, Lagging và Measurement Ladder](#11-leading-lagging-và-measurement-ladder)
12. [Ví dụ tổng hợp: app học tiếng Anh](#12-ví-dụ-tổng-hợp-app-học-tiếng-anh)
13. [Những nhầm lẫn cần tránh](#13-những-nhầm-lẫn-cần-tránh)
14. [Bản ôn tập nhanh](#14-bản-ôn-tập-nhanh)

---

## 1. Vì sao sản phẩm cần metrics?

Khi có vài người dùng, team có thể quan sát trực tiếp. Khi có hàng nghìn hoặc hàng triệu người, team cần những con số để hiểu điều đang xảy ra.

**Product metric** là một con số trả lời câu hỏi về hành vi người dùng hoặc hiệu quả sản phẩm.

Ví dụ:

- Quảng cáo có khiến người ta bấm vào không?
- Người mới có nhận được giá trị đầu tiên không?
- Sau một tháng, họ còn quay lại không?
- Chi phí thu hút khách hàng có được thu hồi không?

**Cách bắt đầu:** xác định câu hỏi và quyết định cần đưa ra, rồi mới chọn metric.

Ví dụ, nếu vấn đề là “người mới bỏ cuộc trước khi học được gì”, số lượt tải app chưa đủ để trả lời. Team cần đo tỷ lệ hoàn thành bài đầu và tìm bước người dùng bỏ dở.

> Metric hữu ích khi nó giúp team quyết định làm gì tiếp theo.

## 2. Phễu đo lường và cách tìm điểm nghẽn

### 2.1. Funnel là gì?

**Funnel — phễu đo lường** mô tả các bước người dùng đi qua để nhận giá trị và tạo kết quả cho sản phẩm.

Hành trình thường gặp:

**Thấy sản phẩm → Quan tâm → Bắt đầu dùng → Nhận giá trị → Quay lại → Tạo doanh thu.**

Trong một phễu tuần tự của cùng nhóm người dùng, số người thường giảm qua từng bước.

### 2.2. Ví dụ ứng dụng đặt xe

| Bước | Số lượng trong ví dụ | Điều team muốn biết |
| --- | ---: | --- |
| Lượt hiển thị quảng cáo | 30.000 | Sản phẩm được tiếp cận tới đâu? |
| Lượt bấm quảng cáo | 300 | Quảng cáo có hấp dẫn không? |
| Người mở app | 200 | Có bao nhiêu người bắt đầu dùng? |
| Người đi chuyến đầu | 120 | Có bao nhiêu người sử dụng dịch vụ lần đầu? |
| Người quay lại ngày 1 | 84 | Sau lần đầu, họ có quay lại sớm không? |
| Người quay lại ngày 7 | 60 | Sau một tuần, họ còn dùng không? |
| Người quay lại ngày 30 | 40 | Sau một tháng, họ còn dùng không? |

Các hàng retention là những mốc theo dõi của cùng cohort, không có nghĩa mọi người quay lại D30 đều đã quay lại đúng D7 và D1. Lượt hiển thị cũng không mặc nhiên là số người duy nhất.

### 2.3. Funnel giúp phát hiện chỗ nghẽn

Giả sử số liệu thay đổi như sau:

| Chỉ số | Trước | Sau |
| --- | ---: | ---: |
| Lượt hiển thị | 30.000 | 30.000 |
| Lượt bấm | 300 | 600 |
| Người mở app | 200 | 400 |
| Người đi chuyến đầu | 120 | 120 |
| CTR | 1% | 2% |
| Tỷ lệ mở app rồi đi chuyến đầu | 60% | 30% |

Quảng cáo kéo được nhiều lượt bấm hơn, nhưng số người đi chuyến đầu không tăng. Team cần kiểm tra đoạn từ mở app đến sử dụng dịch vụ.

Một giả thuyết là quảng cáo thu hút nhiều người tò mò nhưng ít người có nhu cầu đặt xe. Cũng có thể giá cao, thiếu xe hoặc luồng đặt xe gặp lỗi.

> Funnel chỉ ra bước cần điều tra. Để biết nguyên nhân, cần kết hợp dữ liệu, quan sát và phỏng vấn người dùng.

## 3. Các chỉ số nền tảng và công thức

| Chỉ số | Nghĩa dễ hiểu | Công thức hoặc cách đo |
| --- | --- | --- |
| **CTR — Click-through Rate** | Tỷ lệ bấm quảng cáo | Lượt bấm / Lượt hiển thị × 100% |
| **CAC — Customer Acquisition Cost** | Chi phí có được một khách hàng mới | Chi phí thu hút / Số khách hàng mới |
| **Time to Value — TTV** | Thời gian tới giá trị đầu tiên | Thời điểm đạt mốc giá trị − Thời điểm bắt đầu đã định nghĩa |
| **Activation Rate** | Tỷ lệ người mới đạt mốc activation | Người đạt mốc trong cửa sổ quy định / Người mới đủ điều kiện × 100% |
| **Retention Rate** | Tỷ lệ một nhóm người còn quay lại hoặc tiếp tục sử dụng | Người trong cohort đạt điều kiện retention / Người trong cohort đủ điều kiện đo × 100% |
| **LTV — Lifetime Value** | Giá trị một khách hàng mang lại trong vòng đời | Cần xác định cách tính, thời gian và cơ sở doanh thu hay lợi nhuận đóng góp |
| **Payback Period** | Thời gian thu hồi chi phí thu hút khách hàng | Thời điểm giá trị tích lũy đủ bù chi phí thu hút |
| **DAU / WAU / MAU** | Người hoạt động theo ngày / tuần / tháng | Số người duy nhất thực hiện hành động được định nghĩa trong kỳ |
| **Churn Rate** | Tỷ lệ rời bỏ hoặc hủy gói | Người rời bỏ / Nhóm người có nguy cơ rời bỏ trong kỳ × 100% |

Trong ví dụ bài học, chi phí được chia cho người mở app mới. Nếu mẫu số là người cài, người đăng ký hay khách hàng trả tiền, cần ghi rõ; những cách tính ấy không tương đương nhau.

## 4. Activation và Time to Value

### 4.1. Activation là nhận được giá trị đầu tiên

Trong tài liệu này, **activation** là mốc người mới lần đầu trải nghiệm giá trị cốt lõi mà team đã định nghĩa.

Tải app, đăng ký hoặc mở app chưa chắc đồng nghĩa với nhận giá trị.

Ví dụ ứng dụng đặt xe:

| Hành vi | Đã đạt activation chưa? |
| --- | --- |
| Mở app | Chưa |
| Đăng ký tài khoản | Chưa chắc |
| Nhập điểm đến | Chưa chắc |
| Xe tới đón | Có, nếu team chọn đây là mốc activation |

Bài học cũng dùng “đi chuyến đầu” để minh họa tỷ lệ chuyển đổi. Khi đo thực tế, phải chọn một sự kiện nhất quán: xe tới đón và hoàn thành chuyến là hai mốc khác nhau.

Ví dụ tính tỷ lệ:

```text
200 người mới mở app
120 người đạt mốc activation đã chọn

Activation Rate = 120 / 200 × 100% = 60%
```

### 4.2. Time to Value đo tốc độ nhận giá trị

Nếu team chọn “mở app → xe tới đón” và khoảng thời gian đó là 8 phút, TTV của lượt trải nghiệm này là **8 phút**.

Hai metric trả lời hai câu hỏi khác nhau:

- **Activation Rate:** có bao nhiêu người đạt giá trị đầu tiên?
- **TTV:** họ cần bao lâu để đạt được giá trị đó?

## 5. Cohort và Retention

### 5.1. Cohort là gì?

**Cohort** là nhóm người dùng có chung mốc bắt đầu hoặc đặc điểm mà team muốn theo dõi.

Ví dụ:

- Những người cài app trong tháng 9.
- Những người đến từ cùng một chiến dịch.
- Những người hoàn thành chuyến đầu trong cùng một tuần.

Theo dõi cohort giúp team thấy một nhóm cụ thể thay đổi qua thời gian, thay vì trộn người mới và người cũ vào một con số tổng.

### 5.2. Retention đo việc còn ở lại

**Retention** hỏi: sau một khoảng thời gian, bao nhiêu người trong nhóm ban đầu còn thực hiện hành vi được team chọn?

Ví dụ, lấy 120 người đã đi chuyến đầu làm cohort:

| Mốc | Người quay lại | Tỷ lệ trên 120 người |
| --- | ---: | ---: |
| D1 — ngày 1 | 84 | 70% |
| D7 — ngày 7 | 60 | 50% |
| D30 — ngày 30 | 40 | Khoảng 33,3% |

### 5.3. Mẫu số quyết định ý nghĩa

Với cùng 40 người quay lại D30:

```text
40 / 120 = 33,3% của nhóm đã đi chuyến đầu
40 / 200 = 20% của nhóm mới mở app
```

Hai số trả lời hai câu hỏi khác nhau. Khi báo cáo, phải ghi rõ cohort và mẫu số.

Cũng cần thống nhất “quay lại D7” là quay lại **đúng ngày thứ 7**, **trong một cửa sổ quanh ngày 7**, hay **từ ngày 7 trở đi**. Chỉ so sánh những số có cùng cách đo và những cohort đã đủ thời gian quan sát.

### 5.4. Active khác Retention

**MAU** đếm người hoạt động trong tháng, có thể gồm cả người mới. **Retention** theo dõi tỷ lệ người của một cohort trước đó còn ở lại.

MAU tăng vẫn có thể đi cùng retention giảm nếu sản phẩm liên tục thu hút nhiều người mới để bù số người cũ rời đi.

## 6. CAC, LTV và thời gian hoàn vốn

### 6.1. CAC: mất bao nhiêu tiền để có người mới?

Ví dụ bài học:

```text
Chi phí thu hút = 30.000.000 đồng
Người mới theo định nghĩa của ví dụ = 200

Chi phí trên mỗi người mới = 150.000 đồng
```

### 6.2. LTV: mỗi khách hàng mang lại bao nhiêu giá trị?

Sau 5 tháng, cohort tạo ra 35,2 triệu đồng:

```text
35.200.000 / 200 = 176.000 đồng/người
```

Nếu 35,2 triệu là doanh thu, đây là **doanh thu tích lũy bình quân trong 5 tháng**. Nó chưa phải toàn bộ LTV vì người dùng có thể tiếp tục tạo giá trị sau đó.

Muốn đánh giá hiệu quả kinh tế, cần làm rõ đang dùng doanh thu hay phần còn lại sau các chi phí phục vụ khách hàng.

### 6.3. Payback: bao lâu thu hồi được chi phí?

Bài học minh họa payback là 5 tháng. Để kết luận chính xác, cần biết dòng tiền hoặc giá trị đóng góp tích lũy đã bù 30 triệu vào thời điểm nào.

**Doanh thu 35,2 triệu cao hơn chi phí thu hút 30 triệu chưa đủ chứng minh đã hoàn vốn**, nếu chưa trừ chi phí vận hành, phục vụ và các khoản liên quan.

> So sánh LTV với CAC chỉ có ý nghĩa khi cách tính nhất quán. LTV cao hơn CAC là tín hiệu cần thiết trong mô hình so sánh này, chưa bảo đảm doanh nghiệp có lợi nhuận.

## 7. Activated, Active và Core user

### 7.1. Ba khái niệm trả lời ba câu hỏi

| Khái niệm | Câu hỏi | Ví dụ Graph Food trong bài |
| --- | --- | --- |
| **Activated user** | Người này đã đạt mốc giá trị đầu tiên chưa? | Nhận đơn đầu trong 7 ngày kể từ khi cài |
| **Active user** | Trong kỳ đo, người này có làm hành động cốt lõi không? | Đặt ít nhất một đơn trong tháng |
| **Core user** | Trong chu kỳ, người này có dùng đủ thường xuyên không? | Đặt ít nhất 4 đơn/tháng; ngưỡng tạm thời |

**Core action — hành động cốt lõi** là việc chính người dùng đến sản phẩm để làm. Trong ví dụ Graph Food, đó là đặt đơn đồ ăn.

### 7.2. Activated là cột mốc; Active tính lại theo kỳ

Một người nhận đơn đầu trong tháng 9 nhưng tháng 10 không đặt đơn:

- Đã activated: **Có**.
- Active tháng 10: **Không**.
- Core user tháng 10: **Không**.

Việc từng đạt activation không chứng minh người đó sẽ tiếp tục sử dụng.

### 7.3. DAU, WAU và MAU

| Chỉ số | Tên đầy đủ | Kỳ đo |
| --- | --- | --- |
| DAU | Daily Active Users | Một ngày |
| WAU | Weekly Active Users | Một tuần |
| MAU | Monthly Active Users | Một tháng |

Ví dụ cùng cohort 1.000 người cài trong tháng 9:

| Chỉ số | Số người |
| --- | ---: |
| Đạt activation trong cửa sổ 7 ngày | 450 |
| Active tháng 10 | 300 |
| Active tuần cuối tháng 10 | 180 |
| Core user tháng 10, với ngưỡng tạm 4 đơn | 120 |

Activation Rate của cohort là **450 / 1.000 = 45%**.

Nếu tuần đo nằm hoàn toàn trong tháng và cùng định nghĩa active, **WAU ≤ MAU**. Không áp dụng máy móc khi cửa sổ tuần và tháng khác nhau hoặc tuần vắt qua hai tháng.

### 7.4. Core user phụ thuộc nhịp dùng tự nhiên

Người gọi đồ ăn có thể quay lại nhiều lần mỗi tháng. Người đặt phòng du lịch có thể dùng ít lần hơn trong năm. Vì vậy, không lấy một ngưỡng chung cho mọi sản phẩm.

```text
Core user = người thực hiện core action ít nhất N lần
            trong chu kỳ sử dụng đã định nghĩa
```

Team có thể đặt ngưỡng ban đầu để nghiên cứu, nhưng cần kiểm tra bằng dữ liệu.

### 7.5. Cách tìm ngưỡng N từ dữ liệu

Câu chuyện Twitter trong bài học mô tả cách làm:

1. Chia người mới thành các nhóm theo số lần xem feed trong tháng đầu.
2. Đo retention về sau của từng nhóm.
3. Vẽ quan hệ giữa tần suất dùng và retention.
4. Tìm vùng mà retention tăng rõ rồi bắt đầu ổn định.
5. Kiểm tra ngưỡng với dữ liệu khác và thí nghiệm phù hợp.

Theo câu chuyện được kể, khoảng **8 lần/tháng** là vùng retention cao và bắt đầu đi ngang; nhóm core cũng thường theo dõi hơn 30 tài khoản, với khoảng một phần ba quan hệ theo dõi qua lại.

Đó là tín hiệu để nghiên cứu cách giúp người mới kết nối tốt hơn. Nó chưa chứng minh ép người dùng xem feed 8 lần hoặc theo dõi 30 tài khoản sẽ khiến họ ở lại.

> Tìm ngưỡng giúp nhận diện hành vi liên quan đến việc ở lại. Muốn biết một can thiệp có cải thiện retention không, cần kiểm chứng thêm.

## 8. Thống nhất định nghĩa metric

**Metric Definition Contract** là thỏa thuận để cả team hiểu và tính một metric theo cùng cách.

Cùng chữ “activated”, bài học này dùng nghĩa “đạt mốc giá trị đầu tiên”; một số tài liệu được nhắc trong bài dùng nghĩa gần với “core user”. Nếu không thống nhất, cùng cohort có người báo 450, người khác báo 120.

### Bản định nghĩa tối thiểu

| Thành phần | Cần ghi rõ |
| --- | --- |
| Tên và mục đích | Metric trả lời câu hỏi nào? |
| Đối tượng | Người dùng nào được tính? |
| Hành động | Sự kiện nào được coi là đạt? |
| Thời gian | Kỳ đo và cửa sổ hoàn thành là gì? |
| Cách đếm | Đếm người duy nhất hay số sự kiện? |
| Công thức | Tử số và mẫu số là gì? |
| Điều kiện dữ liệu | Loại trừ gì, dùng múi giờ nào và dữ liệu từ đâu? |

Đây là bảng thực hành để viết định nghĩa rõ ràng; nội dung bạn gửi có nhắc bài riêng về “7 điều”, nhưng chưa cung cấp đầy đủ bài đó.

Ví dụ:

> **Activation Rate của cohort cài tháng 9:** số người duy nhất nhận thành công đơn đầu trong 7 ngày kể từ khi cài, chia cho tổng số người cài mới hợp lệ của cohort, nhân 100%. Chỉ chốt khi mọi người trong cohort đã đủ cửa sổ quan sát 7 ngày.

## 9. North Star Metric và ba nhóm giá trị

### 9.1. North Star là gì?

**North Star Metric — chỉ số dẫn đường** phản ánh giá trị chính mà người dùng nhận được và giúp team tập trung cải thiện sản phẩm.

Câu hỏi để bắt đầu:

> Khi người dùng sử dụng sản phẩm thành công, họ nhận được điều gì? Con số nào thể hiện điều đó?

Ví dụ trong bài: với người nghe nhạc, giá trị được minh họa bằng thời gian nghe; với người mua hàng, bằng số đơn hàng.

### 9.2. Ba nhóm North Star trong khung bài học

| Nhóm | Câu hỏi chính | Ví dụ được nêu |
| --- | --- | --- |
| **Monetization — giao dịch/kiếm tiền** | Khách có giao dịch để nhận giá trị không? | Amazon: số đơn/tháng; Airbnb: số đêm đặt phòng |
| **Retention — giữ chân** | Người dùng có tiếp tục quay lại không? | Facebook: DAU; Canva: người dùng hài lòng và còn active |
| **Engagement — mức sử dụng** | Người dùng sử dụng nhiều và sâu đến đâu? | Spotify: thời gian nghe; YouTube: thời gian xem |

North Star thuộc nhóm monetization không nhất thiết là doanh thu. Số đơn hoặc số đêm đặt phòng phản ánh giao dịch mà khách nhận giá trị.

Ba nhóm có liên quan: dùng sâu hơn có thể giúp quay lại, quay lại đều có thể hỗ trợ doanh thu lâu dài. Team chọn câu hỏi chính phù hợp với sản phẩm và tiếp tục theo dõi các khía cạnh còn lại.

### 9.3. Phân biệt North Star với kết quả kinh doanh

- **North Star:** giá trị người dùng nhận được, theo định nghĩa team chọn.
- **Kết quả kinh doanh:** doanh thu, lợi nhuận hoặc khả năng hoàn vốn.

Hai lớp cần có quan hệ được kiểm chứng. Một metric được gọi là North Star cũng không tự động là chỉ báo sớm đáng tin cho doanh thu.

Bài giảng có nhắc “phép thử 7 điều” để kiểm tra North Star, nhưng phần chi tiết chưa có trong nội dung bạn gửi.

## 10. Input metrics: phân rã North Star

### 10.1. North Star là ngọn, input metrics là các nhánh

**Input metric — chỉ số đầu vào** là yếu tố team có thể tác động để cải thiện North Star.

Với một người nghe nhạc trong một tuần:

```text
Tổng thời gian nghe = Số phiên nghe × Số phút trung bình mỗi phiên
```

Ví dụ:

```text
5 phiên × 30 phút = 150 phút/tuần
```

Đây là công thức cho một người. Nếu đo toàn sản phẩm, phải tính cả quy mô người nghe và phân bố phiên nghe; không lấy công thức cá nhân làm tổng thời gian nghe của mọi người.

### 10.2. Mỗi team có thể chịu trách nhiệm một nhánh

| Nhánh | Việc team có thể thử | Metric theo dõi |
| --- | --- | --- |
| Tần suất quay lại | Thông báo nghệ sĩ ra bài mới, gợi ý bài phù hợp | Số phiên nghe/người/tuần |
| Độ dài phiên nghe | Playlist, phát tiếp bài phù hợp, khám phá nhạc mới | Phút nghe trung bình/phiên |

Các tính năng là giả thuyết can thiệp. Chúng cần được đo để biết có cải thiện trải nghiệm và metric hay không.

### 10.3. Một nhánh tăng có thể làm ngọn giảm

| Tình huống của một người | Phiên/tuần | Phút/phiên | Tổng phút/tuần |
| --- | ---: | ---: | ---: |
| Ban đầu | 4 | 30 | 120 |
| Thêm một lần quay lại nhờ thông báo phù hợp | 5 | 30 | 150 |
| Phiên dài hơn nhờ playlist | 5 | 40 | 200 |
| Gửi quá nhiều thông báo, người dùng thấy phiền | 8 | 10 | 80 |

Ở tình huống cuối, tần suất tăng từ 5 lên 8 nhưng thời lượng mỗi phiên giảm từ 40 xuống 10 phút. North Star giảm từ 200 xuống 80 phút.

> Từng team theo dõi nhánh của mình; cả team phải đánh giá kết quả chung. Một nhánh đẹp lên chưa đủ để kết luận thành công.

## 11. Leading, Lagging và Measurement Ladder

### 11.1. Chỉ báo sớm và chỉ báo trễ

| Loại | Nghĩa | Giá trị sử dụng |
| --- | --- | --- |
| **Leading indicator — chỉ báo sớm** | Tín hiệu xuất hiện trước và có khả năng dự báo kết quả sau | Giúp team còn thời gian can thiệp |
| **Lagging indicator — chỉ báo trễ** | Số đo xác nhận kết quả đã xảy ra | Giúp kiểm tra kết quả cuối cùng |

Ví dụ người dùng gói trả phí:

- Tuần 1: đăng ký.
- Tuần 2–3: chưa thấy giá trị, mở app thưa dần.
- Tuần 4: gần như ngừng sử dụng.
- Tháng 3: hủy gói.

Sự giảm sử dụng có thể là tín hiệu sớm. Việc hủy gói và doanh thu mất đi xuất hiện muộn hơn.

**Sớm/trễ là quan hệ giữa các metric.** Retention có thể là kết quả trễ của onboarding, đồng thời là tín hiệu sớm hơn cho doanh thu tương lai. Chúng không phải nhãn cố định cho mọi tình huống.

### 11.2. Đo sớm chưa đủ để trở thành chỉ báo sớm

Lượt tải app có ngay, nhưng tải xong chưa chắc học, quay lại hoặc trả tiền.

Một metric sớm đáng dùng khi:

1. Có thể đo trước kết quả cần dự báo.
2. Có bằng chứng liên quan đến kết quả đó.
3. Cho team thời gian và cơ hội hành động.
4. Quan hệ được kiểm tra lại khi sản phẩm hoặc người dùng thay đổi.

Tương quan giúp tìm tín hiệu dự báo. Thí nghiệm giúp kiểm tra liệu hành động của team có thực sự cải thiện kết quả phía sau.

### 11.3. Measurement Ladder là gì?

**Measurement Ladder — thang đo lường** nối hoạt động của team với hành vi người dùng, giá trị nhận được và kết quả kinh doanh.

Ví dụ Spotify theo bài học:

| Bậc | Nội dung theo dõi | Nhịp đọc minh họa | Vai trò |
| --- | --- | --- | --- |
| 1. Can thiệp | Thử thông báo nghệ sĩ mới và phản ứng với thông báo | Hằng ngày | Kiểm tra thay đổi team vừa làm |
| 2. Input metric | Số lần quay lại | Hằng tuần | Kiểm tra nhánh hành vi |
| 3. North Star | Thời gian nghe | Hằng tháng | Kiểm tra giá trị sử dụng |
| 4. Kết quả kinh doanh | Doanh thu Premium | Hằng quý | Kiểm tra kết quả cuối |

Nhịp đọc này là minh họa; doanh thu cũng có thể theo dõi hằng ngày. Điều quan trọng là thời gian cần để tác động của một thay đổi hiện rõ, không chỉ tốc độ dashboard cập nhật.

Trong một quý khoảng 90 ngày, team có nhiều lần quan sát tín hiệu hằng ngày nhưng chỉ có một lần chốt kết quả quý. Tín hiệu sớm giúp sửa sớm, với điều kiện mối liên hệ giữa các bậc có bằng chứng.

### 11.4. Ví dụ dự báo doanh thu từ ngày thứ Hai

Bài học minh họa một quy luật: doanh thu các ngày trong tuần giữ tỷ lệ ổn định so với thứ Hai.

| Ngày | Doanh thu minh họa |
| --- | ---: |
| Thứ Hai | 10 triệu |
| Thứ Ba | 8 triệu |
| Thứ Tư | 7 triệu |
| Thứ Năm | 6 triệu |
| Thứ Sáu | 4 triệu |
| Thứ Bảy | 3 triệu |
| Chủ nhật | 4 triệu |

Tổng tuần là **42 triệu**, bằng **4,2 lần thứ Hai**.

Nếu tháng có 31 ngày và bắt đầu vào thứ Hai, ba ngày đầu tuần xuất hiện 5 lần, các ngày còn lại xuất hiện 4 lần:

```text
Dự báo tháng = (10 + 8 + 7) × 5 + (6 + 4 + 3 + 4) × 4
             = 125 + 68
             = 193 triệu đồng
```

Có thể ước lượng sớm vì đã giả định được quy luật ổn định. Nếu có lễ, khuyến mãi hoặc thay đổi nhu cầu, phải kiểm tra lại giả định.

### 11.5. Trường hợp Netflix trong bài học

Netflix muốn biết thuật toán gợi ý nào giúp thành viên ở lại lâu hơn. Nhưng khi retention đã cao, tác động nhỏ có thể khó phát hiện trực tiếp.

Bài học kể rằng giờ xem tương quan mạnh với retention và nhạy hơn trước các thay đổi. Team đo giờ xem cùng tỷ lệ hủy trong các thí nghiệm A/B, với thời gian quan sát được nêu khoảng 2–6 tháng.

| Thành phần | Ví dụ Netflix |
| --- | --- |
| Can thiệp | Thay đổi thuật toán gợi ý |
| Tín hiệu sớm hơn | Giờ xem |
| Kết quả trễ hơn | Retention, tỷ lệ hủy |
| Cách kiểm tra | So sánh các nhóm thí nghiệm và tiếp tục theo dõi kết quả sau |

**Correlation ≠ causation — tương quan không đồng nghĩa quan hệ nhân quả.** Người xem nhiều thường ở lại lâu hơn chưa chứng minh mọi cách làm tăng giờ xem đều làm giảm hủy gói.

## 12. Ví dụ tổng hợp: app học tiếng Anh

Giả sử cùng cohort 100 người cài app:

| Mốc | Số người | Tỷ lệ trên 100 người cài |
| --- | ---: | ---: |
| Xong bài đầu ngay hôm cài | 72 | 72% |
| Giữ chuỗi học 7 ngày | 31 | 31% |
| Còn học sang tháng 2 | 22 | 22% |
| Mua gói trả phí vào ngày 90 | 6 | 6% |

Mọi tỷ lệ trong bảng dùng chung mẫu số 100. Không được đọc 31% thành tỷ lệ chuyển đổi từ 72 người xong bài đầu; muốn tính chuyển đổi giữa hai bước còn phải xác nhận những người đó thuộc cùng nhóm nối tiếp.

### Team nên theo dõi gì từ tuần này?

Mục tiêu là tăng doanh thu quý sau. Trong tình huống bài học, dữ liệu cho thấy người hoàn thành bài đầu **trong tuần 1** có retention tốt hơn.

Team nên theo dõi **tỷ lệ hoàn thành bài đầu trong tuần 1**, đồng thời tiếp tục kiểm tra retention và doanh thu về sau.

- Lượt tải cho biết có người đến, chưa cho biết họ học được gì.
- Doanh thu quý xác nhận kết quả nhưng quá muộn để hướng dẫn mọi quyết định trong tuần.
- Hoàn thành bài đầu là tín hiệu gần trải nghiệm giá trị và có bằng chứng liên quan đến việc ở lại.

Lưu ý: **xong bài đầu trong ngày cài** và **xong bài đầu trong tuần 1** là hai metric khác nhau. Con số 72% ở bảng không tự động là tỷ lệ hoàn thành trong tuần 1.

### Cách áp dụng thang đo

| Lớp | Ví dụ cần đo hoặc thử |
| --- | --- |
| Vấn đề | Người mới bỏ dở trước khi nhận giá trị |
| Can thiệp | Rút gọn onboarding hoặc giúp chọn bài phù hợp |
| Tín hiệu sớm | Tỷ lệ hoàn thành bài đầu trong tuần 1 |
| Hành vi tiếp theo | Quay lại học, giữ nhịp học |
| Kết quả sau | Retention tháng 2 và doanh thu quý |

Nếu can thiệp làm tỷ lệ xong bài đầu tăng nhưng retention không cải thiện, team cần xem lại giả thuyết. Có thể bài đầu dễ hoàn thành hơn nhưng chưa giúp người học nhận giá trị đủ để quay lại.

## 13. Những nhầm lẫn cần tránh

| Nhầm lẫn | Cách hiểu đúng |
| --- | --- |
| Mở app nghĩa là activated | Activation phải gắn với mốc giá trị cụ thể |
| Đã activated thì vẫn active | Activated là mốc từng đạt; active phụ thuộc kỳ đo |
| Active nghĩa là core user | Core user cần đạt ngưỡng tần suất trong chu kỳ |
| MAU tăng nghĩa là retention tốt | MAU có thể tăng nhờ người mới dù người cũ rời đi |
| Mọi sản phẩm nên dùng cùng ngưỡng core | Ngưỡng phụ thuộc hành vi, chu kỳ và dữ liệu |
| Metric đo được sớm là leading indicator | Cần có khả năng dự báo được kiểm chứng |
| Hai số đi cùng nhau nghĩa là số này gây ra số kia | Tương quan và nhân quả là hai điều khác nhau |
| Input tăng là thành công | Phải nhìn North Star và kết quả chung |
| North Star luôn là doanh thu | North Star cần phản ánh giá trị người dùng nhận được |
| Doanh thu vượt CAC nghĩa là có lời | Phải xét chi phí và cơ sở giá trị dùng để so sánh |
| Số thu được sau 5 tháng là toàn bộ LTV | Có thể chỉ là giá trị quan sát trong 5 tháng |
| Cùng tên metric thì so sánh được | Cần cùng định nghĩa, cohort, cửa sổ thời gian và cách tính |

## 14. Bản ôn tập nhanh

### Sáu câu hỏi để đọc một sản phẩm

| Câu hỏi | Metric hoặc công cụ phù hợp |
| --- | --- |
| Người dùng có đến không? | Lượt tiếp cận, CTR, chi phí thu hút |
| Có nhận được giá trị đầu tiên không? | Activation Rate, TTV |
| Có quay lại không? | Cohort retention |
| Có dùng đủ thường xuyên không? | DAU/WAU/MAU, core user |
| Team đang cải thiện giá trị nào? | North Star và input metrics |
| Giá trị đó có dẫn tới kết quả kinh doanh không? | Measurement Ladder, doanh thu, LTV/CAC, payback |

### Những câu cần nhớ

- **Câu hỏi trước, metric sau.**
- **Activated = từng đạt mốc giá trị đầu tiên.**
- **Active = có hành động cốt lõi trong kỳ đo.**
- **Core user = đạt ngưỡng sử dụng trong chu kỳ đã chọn.**
- **Retention = một cohort có còn ở lại không.**
- **North Star = giá trị chính cả team muốn cải thiện.**
- **Input metrics = các nhánh team có thể tác động.**
- **Leading = báo trước; lagging = xác nhận kết quả sau.**
- **Một nhánh tăng mà ngọn giảm chưa phải là thắng.**
- **Mỗi liên kết trên thang đo cần có bằng chứng.**

### Trước khi tin một con số

1. Con số trả lời câu hỏi gì?
2. Ai được tính, hành vi nào được tính?
3. Tử số, mẫu số và thời gian là gì?
4. Cohort đã đủ thời gian quan sát chưa?
5. Đây là tín hiệu dự báo hay kết quả đã xảy ra?
6. Nếu metric tăng, giá trị người dùng và kết quả phía sau có cải thiện không?
7. Team sẽ thay đổi quyết định nào dựa vào nó?

---

**Phạm vi tài liệu:** tổng hợp các bài bạn đã cung cấp về funnel, activation, cohort, retention, kinh tế khách hàng, nhóm người dùng, North Star, input metrics và thang đo. Những bài chỉ được giới thiệu ở cuối video — như bài riêng về retention, trade-off, “7 điều” kiểm tra North Star và hợp đồng định nghĩa — chưa được bổ sung thành nội dung bài học khi chưa có phần chi tiết.
