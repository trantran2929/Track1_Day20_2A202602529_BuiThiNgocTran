# AI Support Log

**AI đã giúp tôi ở đâu?**

AI hỗ trợ tôi brainstorm các ứng viên cho Core Action như `outfit_selected` và `outfit_worn`, đồng thời giúp tôi phân biệt Core Action với Core Value Event. AI cũng gợi ý một số metric có thể dùng để đo activation, engagement, retention và North Star Metric; đề xuất cách đặt tên event theo dạng `object_action`; và gợi ý acceptance criteria để tránh việc event được ghi quá sớm hoặc bị ghi trùng. Ngoài ra, AI giúp tôi phản biện lại mối quan hệ giữa nature, cadence và retention của sản phẩm.

**AI sai, hời hợt hoặc đề xuất metric sai nature ở đâu?**

Ở một số bước, AI đã đi quá nhanh khi giả định rằng vì người dùng mặc đồ mỗi ngày nên sản phẩm có thể có daily cadence. Giả định này chưa đủ chặt vì mặc quần áo mỗi ngày không đồng nghĩa với việc người dùng cần AI hỗ trợ phối đồ mỗi ngày. AI cũng từng đề xuất một số metric và event trước khi nature của hành vi được làm rõ hoàn toàn, nên có nguy cơ khiến hệ metric bị dẫn bởi dashboard thay vì use case thực tế.

**Tôi đã tự sửa hoặc quyết định lại điều gì?**

Tôi quyết định tách `outfit_selected` thành Core Action và `outfit_worn` thành Core Value Event, vì việc chọn một outfit chưa chắc đồng nghĩa với việc người dùng thực sự mặc outfit đó. Tôi cũng không giữ giả định daily cadence một cách máy móc mà chuyển sang nhìn hành vi theo từng `outfit opportunity`, tức mỗi lần người dùng thực sự có nhu cầu chọn đồ trước khi ra ngoài. Tôi loại `outfit_rejected` khỏi bộ core events vì event này chưa map trực tiếp về metric chính trong bài. Các quyết định cuối cùng về core action, cadence, retention và metric hypothesis được tôi tự review lại dựa trên logic của use case.
