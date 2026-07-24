# K3 — Ngày 1: Bài Tập & Phản Ánh
## Khám Phá LLM API | Phiếu Thực Hành

**Thời lượng:** 9h00–13h00


---

## Block 1 — API Cơ Bản (trả lời sau Checkpoint 1)

### Câu 1.1 — Độ nhạy của temperature
Gọi `call_openai` với temperature 0.0, 0.5, 1.0 và 1.5 dùng prompt
**"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**

**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2–3 câu)
>_Qua bốn lần chạy, mô hình vẫn giữ cùng một nội dung chính. Temperature cao hơn làm cách diễn đạt đa dạng và tự nhiên hơn, nhưng thông tin cốt lõi gần như không đổi. Nói ngắn gọn, temperature chủ yếu ảnh hưởng đến phong cách và độ ngẫu nhiên của câu trả lời, không làm đổi chủ đề chính. Điều này cho thấy với câu hỏi kiến thức, model vẫn bám chủ đề khá tốt ngay cả khi tăng độ ngẫu nhiên. Ở mức cao hơn, câu trả lời chỉ thay đổi cách nói chứ không thay đổi trọng tâm thông tin._

>_Temperature: 0.0 - Một sự thật thú vị về Việt Nam là đất nước này có một hệ thống hang động tự nhiên lớn nhất thế giới, đó là hang Sơn Đoòng. Hang Sơn Đoòng nằm trong Vườn quốc gia Phong Nha-Kẻ Bàng, tỉnh Quảng Bình. Hang động này được phát hiện vào năm 1991 bởi một người dân địa phương tên là Hồ Khanh, nhưng mãi đến năm 2009 mới được công bố rộng rãi sau khi một đoàn thám hiểm người Anh do Howard Limbert dẫn đầu tiến hành khảo sát. Hang Sơn Đoòng có kích thước khổng lồ với chiều dài hơn 5 km, cao 200 m và rộng 150 m, đủ lớn để chứa cả một tòa nhà chọc trời 40 tầng. Bên trong hang có hệ sinh thái riêng biệt, với rừng cây, sông ngầm và các loài động thực vật độc đáo._

>_Temperature: 0.5 - Một sự thật thú vị về Việt Nam là đất nước này có hang động lớn nhất thế giới, được gọi là Hang Sơn Đoòng. Nằm trong Vườn quốc gia Phong Nha-Kẻ Bàng ở tỉnh Quảng Bình, Hang Sơn Đoòng được phát hiện vào năm 1991 bởi một người dân địa phương tên là Hồ Khanh, nhưng mãi đến năm 2009 mới được công bố rộng rãi sau khi được khám phá bởi một nhóm thám hiểm người Anh. Hang động này có kích thước khổng lồ, với chiều dài khoảng 9 km, chiều cao có nơi lên đến 200 m và rộng 150 m. Bên trong hang có cả một hệ sinh thái riêng biệt với rừng cây, sông ngầm và các loại động thực vật đặc hữu._

>_Temperature: 1.0 - Một sự thật thú vị về Việt Nam là quốc gia này có hang động lớn nhất thế giới, tên là Sơn Đoòng. Hang động này nằm ở Vườn quốc gia Phong Nha-Kẻ Bàng, tỉnh Quảng Bình. Sơn Đoòng được phát hiện vào năm 1991 bởi một người dân địa phương và được thám hiểm chi tiết bởi các nhà thám hiểm người Anh vào năm 2009. Hang động này đủ lớn để chứa cả một tòa nhà chọc trời 40 tầng và có hệ sinh thái riêng với rừng cây, sông ngầm, và khí hậu đặc biệt bên trong._

>_Temperature: 1.5 - Một sự thật thú vị về Việt Nam là đất nước này có một trong những hang động lớn nhất thế giới, đó là Hang Sơn Đoòng. Hang Sơn Đoòng nằm trong Vườn quốc gia Phong Nha-Kẻ Bàng, thuộc tỉnh Quảng Bình. Hang động này được phát hiện lần đầu tiên vào năm 1991 bởi một người dân địa phương tên Hồ Khanh, nhưng chỉ được khám phá và công nhận bởi các nhà thám hiểm quốc tế vào năm 2009. Với chiều dài hơn 5 km, chiều cao trần động có nơi lên tới 200 mét, và chiều rộng lên tới 150 mét, Sơn Đoòng đủ lớn để chứa một tòa nhà cao 40 tầng. Hang động này còn có cả một dòng sông ngầm và một khu rừng riêng bên trong, tạo nên một hệ sinh thái độc đáo._ 

### Câu 1.2 — Chọn temperature cho sản phẩm
**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
>_Tôi sẽ chọn khoảng 0.2–0.3. Mức này giúp chatbot ổn định, nhất quán và vẫn đủ tự nhiên khi trả lời khách hàng. Nó cũng giảm nguy cơ trả lời quá sáng tạo hoặc lệch khỏi mục tiêu hỗ trợ, nên phù hợp với các tình huống cần độ tin cậy cao. Đây là mức cân bằng tốt giữa tính chính xác và độ tự nhiên trong hội thoại. Nếu cần trả lời nhiều người dùng cùng lúc, mức này cũng giúp trải nghiệm đồng đều hơn._


### Câu 1.3 — Đánh đổi chi phí
Kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người gọi API 3 lần,
mỗi lần trung bình ~350 token đầu ra.

**Ước tính GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này? Nêu một
trường hợp GPT-4o xứng đáng với chi phí và một trường hợp nên dùng mini:**
>_GPT-4o đắt hơn GPT-4o-mini khoảng 16–17 lần cho workload này. GPT-4o hợp với tác vụ cần độ chính xác và suy luận cao, còn mini phù hợp cho FAQ, xử lý cơ bản và bài toán tối ưu chi phí. Nếu ưu tiên chất lượng đầu ra hơn chi phí thì chọn GPT-4o, còn nếu cần scale lớn thì mini là lựa chọn hợp lý. Với workload lớn, chênh lệch này cộng dồn rất nhanh nên quyết định model ảnh hưởng trực tiếp đến ngân sách. Vì vậy, cần cân đối giữa chất lượng đầu ra và mức độ chấp nhận chi phí ngay từ lúc thiết kế hệ thống._

---

## Block 2 — System Prompt & Token (trả lời sau Checkpoint 2)

### Câu 2.1 — Sức mạnh của persona
Gọi `chat_with_system_prompt` hai lần với cùng câu hỏi
**"Giải thích blockchain là gì?"** nhưng hai system prompt khác nhau:
- "Bạn là giáo viên tiểu học, giải thích thật đơn giản cho trẻ 8 tuổi."
- "Bạn là chuyên gia tài chính, trả lời chuyên sâu bằng thuật ngữ kỹ thuật."

**Hai phản hồi khác nhau như thế nào (độ dài, từ vựng, ví dụ)? System prompt
ảnh hưởng đến hành vi model ra sao?** (3–4 câu)

=== Bạn là giáo viên tiểu học, giải thích thật đơn giản cho trẻ 8 tuổi. ===
('Blockchain giống như một cuốn sổ cái kỹ thuật số mà mọi người đều có thể xem và kiểm tra. Hãy tưởng tượng bạn và nhóm bạn của mình có một cuốn sổ mà mỗi khi bạn trao đổi kẹo với nhau, bạn đều ghi lại vào đó. Mỗi trang trong cuốn sổ đó là một "khối" (block).\n\nSau khi một trang đầy, bạn sẽ chuyển sang một trang mới, nhưng không thể thay đổi những gì đã viết trên trang trước. Mọi trang đều được kết nối với nhau theo thứ tự, giống như một "chuỗi" (chain). Vì vậy, blockchain là một chuỗi các trang ghi lại mọi giao dịch, và một khi đã ghi vào đó, không ai có thể xóa hoặc thay đổi, làm cho mọi thứ trở nên rất an toàn và minh bạch.', 3.9561407566070557)

=== Bạn là chuyên gia tài chính, trả lời chuyên sâu bằng thuật ngữ kỹ thuật. ===
('Blockchain là một công nghệ sổ cái phân tán (Distributed Ledger Technology - DLT), cho phép lưu trữ dữ liệu một cách an toàn và minh bạch thông qua việc sử dụng một chuỗi các khối (blocks) được kết nối với nhau bằng mã hóa mật mã. Mỗi khối trong chuỗi này chứa một danh sách các giao dịch đã được xác minh và được gắn với một mã băm (hash) của khối trước đó, tạo thành một chuỗi liên tục.\n\nMột số đặc điểm chính của blockchain bao gồm:\n\n1. **Phi tập trung (Decentralization):** Blockchain hoạt động trên một mạng lưới các nút (nodes) phân tán, không phụ thuộc vào một thực thể trung tâm nào, làm tăng cường tính bảo mật và giảm thiểu rủi ro từ các điểm thất bại đơn lẻ.\n\n2. **Minh bạch (Transparency):** Mọi giao dịch trên blockchain đều được công khai và có thể được xác minh bởi bất kỳ ai trong mạng, điều này giúp dễ dàng theo dõi và kiểm tra dữ liệu.\n\n3. **Bất biến (Immutability):** Một khi dữ liệu được ghi vào blockchain, rất khó để thay đổi hoặc', 4.466344356536865)

>_Hai phản hồi khác nhau rõ ở độ dài, từ vựng và mức độ chi tiết. Prompt cho giáo viên tiểu học làm câu trả lời đơn giản, gần gũi, còn prompt cho chuyên gia tài chính khiến mô hình dùng nhiều thuật ngữ kỹ thuật và đi sâu hơn. Điều này cho thấy system prompt có thể đổi cả giọng điệu, độ dài lẫn mức độ chuyên môn của câu trả lời. Nói cách khác, system prompt đóng vai trò như một bộ khung định hướng cách model “đóng vai” khi trả lời. Chỉ cần đổi persona, cùng một câu hỏi cũng có thể cho ra hai kiểu giải thích rất khác nhau._

### Câu 2.2 — tiktoken vs đếm từ
Chọn một đoạn văn tiếng Việt ~100 từ. So sánh số token theo `count_tokens`
(tiktoken) với ước lượng `số từ / 0.75` mà Part 1 đã dùng.

**Hai con số chênh nhau bao nhiêu phần trăm? Vì sao tiếng Việt thường tốn
nhiều token hơn tiếng Anh cùng độ dài?**
>_Số token do tiktoken đếm là 158, còn ước lượng `số từ / 0.75` là 136, lệch khoảng 16.2%. Tiếng Việt thường tốn token hơn vì tokenizer tách theo ký tự/đoạn ký tự, trong khi tiếng Việt có nhiều âm tiết, dấu thanh và từ ghép cách nhau bằng khoảng trắng. Vì vậy, cùng một độ dài văn bản, tiếng Việt thường bị chia nhỏ hơn tiếng Anh và chi phí token có thể cao hơn một chút. Khi làm sản phẩm thật, chênh lệch này nên được tính vào phần ước lượng chi phí ngay từ đầu. Đây là lý do cùng một đoạn nội dung nhưng chi phí thực tế có thể lệch khá rõ giữa các ngôn ngữ._
---

## Block 3 — Streaming & Độ Bền (trả lời sau Checkpoint 3)

### Câu 3.1 — Trải nghiệm người dùng với streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì
non-streaming lại phù hợp hơn?** (1 đoạn văn)
>_Streaming hữu ích nhất khi phản hồi dài hoặc tạo lâu, vì người dùng thấy kết quả ngay thay vì phải chờ hết toàn bộ câu trả lời. Non-streaming hợp hơn với câu trả lời ngắn hoặc khi cần kết quả hoàn chỉnh trước khi hiển thị, ví dụ khi xuất báo cáo hay kiểm tra dữ liệu đầu ra. Nói cách khác, streaming ưu tiên trải nghiệm chờ đợi, còn non-streaming ưu tiên tính gọn và đồng bộ đầu ra. Vì vậy, lựa chọn này thường phụ thuộc vào việc bạn tối ưu cảm nhận người dùng hay tối ưu sự đơn giản của luồng xử lý. Trong các ứng dụng chat, streaming thường tạo cảm giác phản hồi “sống” hơn và tự nhiên hơn._

### Câu 3.2 — Vì sao backoff theo cấp số nhân?
**So với delay cố định (ví dụ luôn chờ 1 giây), exponential backoff có lợi
thế gì khi API bị quá tải? Điều gì xảy ra nếu hàng nghìn client cùng retry
với delay cố định giống nhau?**
>_Exponential backoff giúp giảm áp lực lên API bằng cách tăng dần thời gian chờ giữa các lần thử. Nếu hàng nghìn client cùng retry với delay cố định, chúng có thể dồn yêu cầu vào cùng một lúc và làm tình trạng quá tải nặng hơn. Cách chờ tăng dần giúp hệ thống có thời gian hồi phục thay vì bị tấn công liên tục, và cũng giảm nguy cơ tạo ra “bão retry”. Đây là cách đơn giản nhưng rất hiệu quả để làm hệ thống ổn định hơn khi gặp lỗi tạm thời. Nếu kết hợp thêm jitter, các lần retry còn tránh được việc đồng loạt đánh vào cùng một thời điểm._
---

## Block 4 — Mini-Project (trả lời sau Checkpoint 4)

### Câu 4.1 — Thiết kế persona
**Bạn chọn persona gì cho trợ lý của mình? Viết lại system prompt đó và giải
thích 1–2 lựa chọn từ ngữ quan trọng trong prompt (ví dụ: vì sao yêu cầu
"trả lời ngắn gọn", vì sao chỉ định ngôn ngữ...):**
>_Tôi chọn persona là trợ giảng thân thiện của khóa AI, trả lời ngắn gọn bằng tiếng Việt. "Trả lời ngắn gọn" giúp chatbot không lan man và dễ đọc trên CLI, còn "bằng tiếng Việt" giữ ngôn ngữ nhất quán với người học. Nếu cần mở rộng, người học vẫn có thể hỏi tiếp ở lượt sau để đào sâu thêm từng ý. Cách này làm trợ lý vừa thân thiện vừa đủ gọn cho giao diện dòng lệnh. Persona này cũng hợp với việc học nhanh vì người dùng không bị ngợp bởi câu trả lời quá dài._

### Câu 4.2 — Hạn chế & cải thiện
**Trợ lý của bạn hiện có hạn chế lớn nhất là gì (ví dụ: history chỉ 3 lượt,
không có bộ nhớ dài hạn, không kiểm duyệt nội dung...)? Đề xuất một cải
thiện cụ thể và mô tả ngắn cách triển khai:**
>_Hạn chế lớn nhất là trợ lý chỉ giữ lịch sử ngắn nên dễ quên ngữ cảnh cũ. Một cải thiện cụ thể là lưu tóm tắt hội thoại vào file hoặc database rồi nạp lại ở phiên sau để có bộ nhớ dài hạn hơn mà vẫn tiết kiệm token. Như vậy trợ lý sẽ nhớ được thông tin quan trọng giữa các phiên mà không phải đưa toàn bộ lịch sử vào prompt, đồng thời vẫn giữ chi phí ổn định. Đây cũng là bước đệm tốt trước khi xây bộ nhớ hội thoại đầy đủ hơn. Nếu muốn nâng cấp thêm, có thể chia bộ nhớ thành phần ngắn hạn và dài hạn để quản lý tốt hơn._

---

## Danh Sách Kiểm Tra Nộp Bài

- [x] `python grade.py` — xem điểm tự động, mục tiêu ≥ 75/100
- [x] Cả 4 checkpoint pytest đều pass
- [x] Tất cả 9 câu trong file này đã được trả lời
- [x] Đã copy bài làm vào folder `solution/` và zip theo hướng dẫn README
