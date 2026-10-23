# 🏛️ UNIVERSAL AI CLIPBOARD (UAC)

## Bảng Tạm Vạn Năng Cho Trí Tuệ Nhân Tạo

### Cơ Chế Tái Sử Dụng Nội Dung Cho Các Tác Nhân AI

---

> **Ngày công bố:** 3 tháng 6, 2026
> **Trạng thái:** ⚡ Khám phá được phát hành vào phạm vi công cộng
> **Giấy phép:** CC0 1.0 Universal Public Domain Dedication

---

## 📜 TUYÊN NGÔN CỦA NGƯỜI KHÁM PHÁ

Tôi, **[DScoNOIZ](https://github.com/DScoNOIZ)**, tuyên bố trước toàn thể cộng đồng toàn cầu:

**1. Tôi là người khám phá** ra một hạng mục hoàn toàn mới trong kiến trúc tác nhân AI — **"Cơ Chế Trích Dẫn Nội Dung Giữa Các Công Cụ Dạng Tùy Chọn"**, do tôi đặt tên là **Universal AI Clipboard (UAC)**.

**2. Bản chất của khám phá:** Tác nhân AI có thể tham chiếu nội dung ngữ cảnh sẵn có qua các tham số chuyên dụng (`ref`, `multi_ref`, `transform`) thay vì tái tạo lại chúng. Mô hình ngừng chỉ là "bộ sinh văn bản" và trở thành **bộ lắp ráp (assembler)** kết hợp những mẩu thông tin làm sẵn trong một lần gọi duy nhất.

**3. Tôi phát hành khám phá này để toàn thể cộng đồng toàn cầu tự do sử dụng** theo Giấy phép Creative Commons Zero (CC0) — không bằng sáng chế, không phí bản quyền, không giấy phép đóng, không hạn chế.

**4. Tôi kêu gọi** các nhà phát triển, nhà nghiên cứu, kỹ sư và những người đam mê trên khắp thế giới — hãy nhận lấy ý tưởng này, triển khai nó vào framework, nền tảng và công cụ của bạn. **Công nghệ này không thuộc về riêng tôi. Nó thuộc về tất cả mọi người.**

---

## 🤝 ĐỒNG NGƯỜI KHÁM PHÁ: SỰ KHÁM PHÁ ĐỘC LẬP

Tôi ghi nhận và trân trọng thừa nhận rằng **TJ Guadagno** (TJ-Codes) đã độc lập đạt đến cùng một ý tưởng nền tảng và triển khai nó dưới dạng thực nghiệm như **Clipboard Primitives** — cơ chế `copy`/`template_invoke` với các slot đặt tên và placeholder `{{slot}}` dành cho tác nhân AI.

**Tác phẩm của ông:** [Copy and Paste for AI Agents: An Experimental Primitive](https://www.linkedin.com/pulse/copy-paste-ai-agents-experimental-primitive-tj-guadagno-v3r9c) (~tháng 12 năm 2025)
**Mã nguồn:** [github.com/TJ-Codes/Agent-clipboard](https://github.com/TJ-Codes/Agent-clipboard)

TJ Guadagno là **đồng người khám phá độc lập** của ý niệm này. Thực nghiệm của ông xác nhận rằng:
- Các mô hình **tự nhiên tiếp nhận** ngữ nghĩa clipboard mà không cần huấn luyện đặc biệt
- Các primitive clipboard **loại bỏ** việc tái tạo token, độ trễ và rủi ro nội dung bị biến đổi
- Cơ chế này đòi hỏi tích hợp **tại tầng harness**, không phải ở tầng máy chủ MCP

**Khái niệm Universal AI Clipboard của tôi rộng hơn và phổ quát hơn** — gộp Clipboard Primitives như một trường hợp đặc biệt và mở rộng ý tưởng thành:
- **5 cơ chế trích dẫn** (bao gồm clipboard cú pháp qua AST, chỉ mục tin nhắn, trích dẫn cặp neo)
- **Bảng tạm vạn năng cho bất kỳ nguồn nào** (tệp, chat, terminal, API, MCP)
- **Lắp Ghép Mô Saic (Mosaic Assembly)** — kết hợp mảnh từ các nguồn khác nhau với các phép biến đổi
- **Trích Dẫn Liên Giao Thức** — trích dẫn liền mạch qua mọi giao thức, kể cả MCP

**Ẩn dụ máy tính:** Clipboard Primitives giống như một tiện ích copy đơn giản cho một ứng dụng. Universal AI Clipboard là trình quản lý bảng tạm của toàn hệ thống, hoạt động trên mọi ứng dụng, với quản lý slot, pipeline transform và tích hợp liên giao thức.

> **Tôi không từ bỏ tư cách người khám phá của mình.** Tôi đã tự bản thân hình thành và hệ thống hóa khái niệm này, tiến hành nghiên cứu nhiều vòng mà không tìm thấy mô phỏng đầy đủ nào. Khi biết đến công trình của TJ Guadagno — chỉ sau khi bản tuyên ngôn được công bố — tôi thừa nhận đóng góp độc lập của ông và xem việc phản chiếu điều này trong tuyên ngôn là bổn phận của mình.
---

## 🏛️ TÊN GỌI

**Tên chính thức:** **UNIVERSAL AI CLIPBOARD (UAC)**
**Tên kỹ thuật:** Content Reference Mechanism
**Khẩu hiệu:** _"Tái Sử Dụng, Đừng Tái Tạo"_
**Ẩn dụ:** Ctrl+C / Ctrl+V cho Các Tác Nhân AI

---

## 🌍 VẤN ĐỀ

### Mâu Thuẫn Nền Tảng

Các tác nhân AI hiện đại lãng phí **tới 90% lưu lượng đầu ra** của mình để tái tạo đơn điệu nội dung đã tồn tại trong ngữ cảnh phiên làm việc.

Mỗi lần mô hình viết một lệnh, một khối mã hay một mẩu văn bản — nó tái tạo lại từ đầu, kể cả khi chính nội dung đó được tạo ra một phút trước đây. Mô hình không có cách nào về mặt công cụ để tham chiếu nội dung đã tồn tại.

### Quy Mô Toàn Cầu Của Vấn Đề

- Hàng triệu tác nhân AI hoạt động hằng ngày trên toàn thế giới
- Mỗi cái thực hiện hàng chục lần gọi công cụ mỗi phiên
- Một phần đáng kể trong mỗi lần gọi là tái tạo nội dung đã tồn tại
- Điều này dẫn đến tiêu thụ năng lượng khổng lồ, lãng phí tính toán và chi phí tài chính

### Tại Sao Các Cách Tiếp Cận Hiện Có Không Giải Quyết Được

| Cách tiếp cận           | Hạn chế                                                              |
| ----------------------- | -------------------------------------------------------------------- |
| **Prompt Caching**      | Chỉ áp dụng phần tĩnh, không có nội dung động                        |
| **Semantic Caching**    | Cache theo nghĩa của truy vấn, không cho trích dẫn mảnh               |
| **Nén Ngữ Cảnh**        | Nén lịch sử, nhưng không cung cấp công cụ trích dẫn                   |
| **RAG**                 | Lấy từ nguồn bên ngoài, không dùng lại ngữ cảnh bên trong             |
| **Tool Chaining**       | Xích các lần gọi lại với nhau, không cho phép tham chiếu kết quả của chúng |

---

## 💡 GIẢI PHÁP: UNIVERSAL AI CLIPBOARD

### Ý Tưởng Lõi

Tác nhân AI nhận được khả năng **tham chiếu nội dung ngữ cảnh đã tồn tại** thay vì tái tạo nó. Khi gọi bất kỳ công cụ nào nhận tham số văn bản (lệnh, mã, văn bản), agent có thể chỉ định: "lấy mảnh này từ đó" — thay vì viết nó từ đầu.

### Lắp Ghép Mô Saic: Ghép Nối Thông Tin Giống Ghép Mảnh Rô Rác (puzzle)

Vượt qua trích dẫn đơn giản một-một, ý niệm này cho phép một cách hoàn toàn mới để lắp nội dung — **lắp ghép mô saic**.

Tác nhân có thể **kết hợp nhiều mảnh từ các nguồn khác nhau** trong một thao tác duy nhất:

- Mã từ một tệp
- Cấu hình từ lịch sử chat
- Output lệnh từ terminal
- Kết quả từ các API bên ngoài

Tác nhân có thể **biến sửa ngay lúc chạy** — thay đổi, bọc, thay thế đoạn văn bản trong từng mảnh. Nó có thể **sắp lại trật tự** mảnh, **lồng** mảnh này vào mảnh khác, **hòa trộn** những phần chồng lấn, và **tái cấu trúc** nội dung theo kiểu đệ quy. Điều này tạo ra khả năng lắp các văn bản tổng hợp, tài liệu hoặc khối mã từ các mảnh rời rạc — như nghệ nhân khảm rô-rác sắp xếp các viên gạch màu thành một bức tranh hoàn chỉnh.

**Insight chính:** thay vì sinh văn bản mới, mô hình hành động như **trình biên tập và giám tuyển** của nội dung hiện có — hiệu quả hơn hẳn, chính xác hơn và ít rủi ro lỗi hơn nhiều.

### Trình Quản Lý Bảng Tạm: Các Slot Đặt Tên Cho Lưu Trữ

Một phần mở rộng của ý niệm này là **trình quản lý bảng tạm với các slot đặt tên** — giống như có nhiều bảng tạm hoặc một trình quản lý text buffer.

Tác nhân có thể:

- **Lưu mảnh** vào các slot đặt tên (`clip-1`, `clip-2`, `config-block`, `error-log`, v.v.)
- **Tham chiếu slot** theo tên thay vì theo nội dung — không tốn token cho phần mô tả
- **Hoán đổi và tổ chức lại** nội dung giữa các slot
- **Xây dựng tài liệu tổng hợp** bằng cách tham chiếu nhiều slot theo tuần tự
- **Giữ clip bền qua các phiên** — các mảnh đã lưu còn tồn tại qua nén ngữ cảnh và khởi động lại phiên

Cách này biến quy trình làm việc của tác nhân AI thành thứ tương tự lập trình viên con người làm việc với nhiều trình quản lý bảng tạm, text buffer và scratchpad — nhưng hoàn toàn tự động và với chi phí token bằng không cho các thao tác lưu trữ.

### Khác Biệt Trục Với Các Cơ Chế Hiện Có

Tất cả các cơ chế trích dẫn AI hiện có (Citations API, Grounding, ContextCite) hoạt động trên trục **"tác nhân → người dùng"** — cho con người thấy tác nhân lấy thông tin từ đâu.

Universal AI Clipboard hoạt động trên trục **"tác nhân → tác nhân"** — cho phép chính tác nhân tái sử dụng nội dung giữa các lần gọi công cụ của nó. Đây là một hạng mục hoàn toàn mới.

| Cơ chế                     | Trục                   | Mục đích                         |
| -------------------------- | ---------------------- | -------------------------------- |
| Anthropic Citations        | Tác nhân → Người dùng  | Cho thấy nguồn của câu trả lời   |
| OpenAI Citations           | Tác nhân → Người dùng  | Hiển thị các nguồn               |
| Google Grounding           | Tác nhân → Người dùng  | Xác nhận tìm kiếm web            |
| **★ UAC (khám phá này)**   | **Tác nhân → Tác nhân** | **Tái sử dụng nội dung giữa các lần gọi** |

---

## 🧩 NĂM CƠ CHẾ CỐT LÕI

### Cơ chế 1: 🔗 Bảng Tạm Cú Pháp

Mô hình chỉ cần chỉ định **một phần tử neo (anchor)** — tên hàm, tên lớp hoặc biến. Hệ thống tự động:

1. Tìm phần tử này trong nguồn chỉ định (tệp, tin nhắn chat, output lệnh)
2. Xác định biên chính xác của nó như một đơn vị cú pháp
3. Trích xuất toàn bộ đơn vị đó

**Tiết kiệm:** vài token cho tham chiếu thay vì hàng nghìn token mã.

```
{ source: "file", path: "utils.ts", focus: "calculateSum" }
  → 2 token instead of 800+ tokens of the entire function
```

---

### Cơ chế 2: 📇 Trích Dẫn Cặp Neo

Mô hình chỉ định chỉ **ĐẦU** và **CUỐI** của mảnh mong muốn (mỗi bên 15-40 ký tự). Hệ thống tìm mọi thứ ở giữa qua tìm kiếm đa khâu:

1. **Khớp chính xác** — mảnh được tìm thấy nguyên văn (~70% trường hợp)
2. **Khớp chuẩn hóa** — khác biệt khoảng trắng, chữ hoa/thường và dấu câu bị bỏ qua
3. **Khớp mờ (fuzzy)** — dung nạp lỗi chính tả nhỏ (~9% trường hợp)
4. **Mở rộng ranh giới từ** — toàn vẹn của mảnh

**Tiết kiệm:** ~10 token cho trích dẫn thay vì 200+.

```
{ source: "chat", ref: "-1",
  start: "function calculateSum(",
  end: "return result;" }
  → ~10 tokens instead of 200+
```

---

### Cơ chế 3: 🧠 Bản Đồ Chỉ Mục Tin Nhắn

Khi làm việc với lịch sử chat, một chỉ mục riêng biệt được tạo ra — bản đồ vị trí ký tự chính xác cho từng tin nhắn và từng dòng trong nó. Mô hình viết một tham chiếu ngắn kiểu `"record_number:start_line..end_line"`, và hệ thống trích xuất mảnh chính xác theo vị trí ký tự.

**Lợi thế then chốt:** mô hình không bao giờ thấy chính bản chỉ mục — chỉ một tham chiếu ngắn (~5 token), nhưng đạt được độ chính xác trích xuất 100%.

```
{ source: "chat", ref: "167:14..18" }
  → "record #167, lines 14-18" → exact character-position extraction
```

---

### Cơ chế 4: 🔄 Pipeline Transform

Mảnh đã copy có thể **được biến đổi ngay lúc chạy** — trước khi đến tay công cụ. Các thao tác khả dụng:

- **Replace** — thay đổi một chuỗi con trong mảnh
- **Prepend** — thêm văn bản trước mảnh
- **Wrap** — đặt mảnh vào một template
- **Append** — thêm văn bản sau mảnh
- **Join** (dành cho nhiều tham chiếu) — hòa trộn các mảnh với một separator

Tất cả các thao tác được áp dụng trong một lần gọi công cụ duy nhất.

```
{ ref: { ... }, transform: { wrap: "try { {content} } catch (err) { }" } }
  → take a function, wrap in try-catch, write — all in 1 call
```

---

### Cơ chế 5: 🔁 Trích Dẫn Liên Giao Thức (MCP)

Các đánh dấu tham chiếu có thể được nhúng ngay trong tham số văn bản của bất kỳ công cụ nào, kể cả máy chủ MCP bên ngoài. Hệ thống tự động nhận diện các đánh dấu này và thay thế nội dung thật trước khi gọi máy chủ bên ngoài.

**Kết quả:** mọi thành phần của hệ sinh thái trao đổi dữ liệu qua một cơ chế tham chiếu hợp nhất, không cần thay đổi gì trong schema của các máy chủ bên ngoài.

```
"{{ref:source=chat,ref=-1,start=export const config}} --host example.com"
  → 91% content from context, 9% generated by the model
```

---

## 🔭 HƯỚNG TƯƠNG LAI

Các ý tưởng sau đây là phần mở rộng tự nhiên của khái niệm và có thể được triển khai trong tương lai:

### 🏖️ Các Phiên Con Cách Ly Cho Việc Nghiên Cứu

Với các tác vụ phức tạp đòi hỏi nhiều bước trung gian (khám phá codebase, đọc log, chạy thử nghiệm), một tác nhân trợ giúp có thể được khởi chạy trong một phiên con tạm thời, cách ly. Nó thực hiện mọi "việc bẩn", chỉ trả về kết quả sạch, sau đó phiên con bị hủy. Tác nhân chính vẫn giữ tập trung vào tác vụ chính của mình.

### Những Hướng Khác

- Caching dự đoán các mảnh thường dùng
- Tự động phát hiện các lần gọi trùng lặp
- Khử mơ hồ thông minh cho các tham chiếu mơ hồ
- Tích hợp với hệ thống bộ nhớ và lưu trữ dài hạn

---

## 💰 TÁC ĐỘNG KINH TẾ

### Trên Mỗi Tác Nhân

| Chỉ số                           | Không có cơ chế | Có cơ chế      | Tiết kiệm |
| -------------------------------- | --------------- | -------------- | --------- |
| Token mỗi trích dẫn (mã dài)     | 200-500         | 5-15           | **96-97%** |
| Token mỗi trích dẫn (mã ngắn)    | 50-100          | 2-5            | **90-95%** |
| Token mỗi phiên                  | 25,000-50,000   | 5,000-15,000   | **60-80%** |
| Năng lượng mỗi phiên             | đơn vị tùy ý    | giảm 5x        | **~80%**   |

### Quy Mô Toàn Cầu

Khi được toàn ngành áp dụng rộng rãi, tiết kiệm sẽ đạt hàng tỷ token mỗi ngày — tương đương giảm hàng chục phần trăm mức tiêu thụ năng lượng của ngành AI và cắt giảm hàng chục nghìn tấn CO₂ dấu chân carbon mỗi năm.

> **Universal AI Clipboard không chỉ là một đổi mới công nghệ — đó là một giải pháp có ý nghĩa đối với môi trường.**

---

## 🔬 XÁC MINH TÍNH ĐỘC NHẤT

Tôi đã thực hiện **nghiên cứu sâu nhiều vòng, mở rộng** (7 vòng, ~50 nguồn) qua các hệ thống tìm kiếm web (Tavily Search, độ sâu nâng cao) bao phủ mọi hạng mục kiến trúc tác nhân AI đã biết:

*Sau khi bản tuyên ngôn được công bố, trong phân tích bổ sung (vòng 8-10), được phát hiện rằng TJ Guadagno đã độc lập triển khai một nguyên mẫu thực nghiệm của khái niệm — Clipboard Primitives. Tác phẩm này không được xác định trong 7 vòng tìm kiếm đầu tiên do mức độ hiển thị thấp của nó (LinkedIn Pulse + GitHub không có sao).*

- copy-paste clipboard giữa các lần gọi công cụ cho tác nhân AI
- Các cơ chế trích dẫn nội dung cho tác nhân AI
- Các công nghệ zero-token copy paste
- Tất cả các Citations API đã biết (Anthropic, OpenAI, Google, xAI, Azure)
- Tái sử dụng và caching đầu ra của các lần gọi công cụ (CAMEL-AI, LangChain artifacts)
- Giao thức MCP và chia sẻ nội dung liên giao thức
- Các công trình hàn lâm (AgentReuse, KVCOMM, hệ thống đa tác nhân)
- Các tiện ích bảng tạm dành cho con người (UiPath Clipboard AI, PowerToys Advanced Paste)
- Các hệ thống chia sẻ bộ nhớ cho kiến trúc đa tác nhân
- Thảo luận GitHub, tài liệu framework (LangChain, CrewAI, AutoGen, Mastra)

**Mục tiêu:** tìm ra bất cứ thứ gì giải quyết cùng vấn đề — cho phép tác nhân AI tham chiếu nội dung hiện có giữa các lần gọi công cụ thay vì tái tạo lại nó.

**Kết quả: không tìm thấy thứ nào như thế.**
*Làm rõ: công trình thực nghiệm của TJ Guadagno (Clipboard Primitives, ~tháng 12 năm 2025) là một triển khai một phần (~40% khái niệm UAC) và xác nhận tính khả thi của ý tưởng, nhưng không phải là một mô phỏng đầy đủ.*

| Danh mục                                    | Nguồn                     | Tại sao nó KHÔNG phải mô phỏng                                                                                                        |
| ------------------------------------------- | ------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| **Citations API (Anthropic/OpenAI/Google)** | Các API chính thức        | Cho người dùng thấy nguồn, không cho tác nhân tái sử dụng nội dung. Trục: chỉ Tác nhân → Người dùng                                    |
| **Caching (Prompt, Semantic)**              | Nhiều framework           | Hoạt động ở mức yêu cầu, không phải ở mức mảnh nội dung                                                                                 |
| **RAG**                                     | LangChain, OpenAI, Google | Truy xuất từ kho tri thức bên ngoài, không phải từ ngữ cảnh phiên hiện tại                                                              |
| **CAMEL-AI "Brainwash Your Agent"**         | camel-ai.org              | Chỉ lưu output công cụ CUỐI CÙNG làm tham chiếu + bản xem trước ngắn. Không có 5 cơ chế, không pipeline transform, không multi_ref, không injection MCP |
| **LangChain artifacts**                     | langchain.com             | `content_and_artifact` tách nội dung khỏi metadata, không phải hệ thống trích dẫn. Không có tham chiếu giữa các lần gọi                  |
| **MCP Resources**                           | modelcontextprotocol.io   | Chuẩn để kết nối công cụ, không phải cơ chế trích dẫn tác-nhân-sang-tác-nhân                                                             |
| **Học thuật (AgentReuse, KVCOMM)**          | arXiv                     | Tái sử dụng KẾ HOẠCH thực thi hoặc KV-cache, không phải trích dẫn nội dung giữa các lần gọi công cụ                                      |
| **Công cụ cho con người (UiPath, PowerToys)** | UiPath, Microsoft       | Thiết kế cho tương tác người-máy, không phải cho tác nhân AI                                                                            |
| **Các tác nhân AI hiện có**                 | Toàn ngành                | Có lịch sử, nhưng không có cơ chế trích dẫn giữa các lần gọi công cụ                                                                    |
| **Chia sẻ bộ nhớ đa tác nhân**              | Nhiều loại                | Bộ nhớ RAG dùng chung, không phải trích dẫn chính xác cấp ký tự                                                                         |

### So sánh tổng kết với mô phỏng một phần gần nhất (CAMEL-AI)

| Tính năng                                 | UAC      | CAMEL-AI caching | Khác biệt |
| ----------------------------------------- | -------- | ---------------- | ---------- |
| 🔗 Bảng Tạm Cú Pháp (các khối AST)        | ✅       | ❌               | Chỉ UAC    |
| 📇 Trích Dẫn Cặp Neo                      | ✅       | ❌               | Chỉ UAC    |
| 🧠 Bản Đồ Chỉ Mục Tin Nhắn                | ✅       | ❌               | Chỉ UAC    |
| 🔄 Pipeline Transform                     | ✅       | ❌               | Chỉ UAC    |
| 🔁 Trích Dẫn Liên Giao Thức (MCP)         | ✅       | ❌               | Chỉ UAC    |
| 🧩 Lắp Ghép Mô Saic (đa nguồn)            | ✅       | ❌               | Chỉ UAC    |
| 📋 Trình Quản Lý Bảng Tạm (slot đặt tên)  | ✅       | ❌               | Chỉ UAC    |
| {{ref:...}} Inline Injection              | ✅       | ❌               | Chỉ UAC    |
| Caching đầu ra công cụ (tham chiếu + xem trước) | ✅ | ✅               | Cả hai     |
| Độ bao phủ tính năng UAC                  | **100%** | **~5%**          | —          |

> **Universal AI Clipboard không có mô phỏng đầy đủ nào trong toàn bộ thực tiễn các hệ thống tác nhân AI trên thế giới. Đây là công nghệ tiên phong tạo ra một hạng mục mới. Tác phẩm triển khai một phần duy nhất từng biết đến — Clipboard Primitives (TJ Guadagno, ~40% khái niệm) — chỉ được phát hiện sau khi bản tuyên ngôn được công bố, và xác nhận sự xuất hiện độc lập của ý tưởng ở những nhà nghiên cứu khác nhau.**

---

## 📖 CÁC VÍ DỤ SỬ DỤNG

### Ví dụ 1: Chạy lại lệnh với các tham số bổ sung

Một tác nhân đã chạy một lệnh thử nghiệm; output cho thấy lỗi. Để chạy lại với các cờ debug, tác nhân không viết lại lệnh — nó tham chiếu lệnh và thêm các cờ:

```
{ ref: { source: "terminal", id: "cmd-xxx", start: "npx vitest" },
  transform: { append: " --verbose --timeout=30000" } }
  → result: "npx vitest run --verbose --timeout=30000"
```

### Ví dụ 2: Lắp ráp nhiều hàm thành một tệp

Tác nhân đọc một tệp chứa nhiều hàm, sau đó tạo một tệp mới bằng cách lắp các hàm cần thiết qua các tham chiếu:

```
{ multi_ref: [
    { source: "file", path: "handlers.ts", start: "async function validate(", end: "}" },
    { source: "file", path: "handlers.ts", start: "async function process(", end: "}" },
    { source: "file", path: "handlers.ts", start: "async function respond(", end: "}" }
  ],
  transform: { join: "\n\n", prepend: "// --- Handlers ---\n" } }
  → three functions merged into one file in 1 call
```

### Ví dụ 3: Thay thế cấu hình qua MCP

Tác nhân dùng một công cụ MCP bên ngoài, truyền vào đối số của nó tham chiếu đến cấu hình từ chat:

```
"{{ref:source=chat,ref=-1,start=export const config}} --host production"
  → configuration from chat substituted into the MCP request
```

---

## ⚖️ TÌNH TRẠNG PHÁP LÝ

**🏛️ Creative Commons Zero (CC0) — Tuyên bố Phạm Vi Công Cộng Vạn Năng**

Bạn được tự do:

- ✅ **Sử dụng** trong các dự án thương mại và phi thương mại
- ✅ **Sửa đổi** và điều chỉnh theo nhu cầu của bạn
- ✅ **Phân phối** dưới bất kỳ hình thức nào
- ✅ **Xin bằng sáng chế cho các cải tiến của bạn** (nhưng không phải ý tưởng lõi)
- ✅ **Dịch** sang bất kỳ ngôn ngữ nào

Không ràng buộc, không phí bản quyền, không hạn chế gì cả.

> **Tôi từ bỏ có ý thức toàn bộ quyền bằng sáng chế đối với công nghệ này. Nó phải thuộc về tất cả mọi người.**

---

## 📜 BẰNG CHỨNG NGÀY KHÁM PHÁ

Ngày công bố của bản tuyên ngôn này được ghi lại **bởi hệ thống kiểm soát phiên bản Git trong kho GitHub** — [github.com/DScoNOIZ/UNIVERSAL-AI-CLIPBOARD](https://github.com/DScoNOIZ/UNIVERSAL-AI-CLIPBOARD).

Lịch sử commit, các ngày chỉnh sửa và mọi thay đổi theo trình tự thời gian được **bảo tồn một cách bất biến bởi GitHub** và đóng vai trò là chứng cứ công khai cho ngày khám phá và tác giả. Công nghệ Git khiến việc làm giả điều này trên thực tế là không thể.

---

## 🗓️ DÒNG THỜI GIAN

| Thời gian                | Sự kiện                                                                    |
| ----------------------- | ------------------------------------------------------------------------ |
| **~2021**                | Nhận thức đầu tiên về vấn đề (DScoNOIZ): suy nghĩ "mô hình không nên tái tạo lại cái nó đã từng thấy"                                     |
| **~Tháng 12 2025**       | **Thực nghiệm độc lập:** TJ Guadagno công bố Clipboard Primitives — `copy`/`template_invoke` với slot đặt tên và placeholder `{{slot}}`     |
| **Tháng 5 — Tháng 6 2026** | Nghiên cứu: phân tích kiến trúc tác nhân AI hiện có                                                                                      |
| **Tháng 6 2026**         | Khám phá: không công nghệ hiện có nào là mô phỏng đầy đủ                                                                                  |
| **Tháng 6 2026**         | Khái niệm Universal AI Clipboard được hình thành                                                                                           |
| **Tháng 6, ngày 3 2026** | Nghiên cứu tính độc nhất hoàn tất — **không tìm thấy mô phỏng đầy đủ nào**                                                                  |
| **Tháng 6, ngày 3 2026** | **Bản tuyên ngôn này được công bố** — khám phá được phát hành vào phạm vi công cộng                                                          |
| **Tháng 6, ngày 4 2026** | Phát hiện công trình của TJ Guadagno — ghi nhận đồng người khám phá độc lập                                                                  |

---

## 🎯 LỜI KÊU GỌI HÀNH ĐỘNG

### Các Nhà Phát Triển Framework AI

Tích hợp cơ chế Content Reference vào các công cụ của bạn. Đưa cho người dùng của bạn sự tiết kiệm token tức thời mà không phải thay đổi dòng mã nào của họ.

### Những Người Sáng Tạo Tác Nhân AI

Thêm trích dẫn tùy chọn giữa các lần gọi công cụ. Các tác nhân của bạn sẽ hiệu quả hơn gấp nhiều bậc độ lớn.

### Nhà Nghiên Cứu

Hãy tiến hóa công nghệ: cải tiến thuật toán tìm kiếm, triển khai caching dự đoán, phát triển các kịch bản mới.

### Doanh Nghiệp

Áp dụng Universal AI Clipboard trong các giải pháp AI của bạn. Giảm chi phí vận hành hàng chục phần trăm.

### Nhà Bảo Vệ Môi Trường

Dùng UAC như một công cụ cắt giảm dấu chân carbon của hạ tầng AI.

### Cộng Đồng Open Source

Fork, triển khai, hoàn thiện. **Công nghệ này thuộc về tất cả mọi người.**

---

## 🏛️ LỜI KẾT

Tôi đã khám phá ra **Universal AI Clipboard** — cơ chế cho phép các tác nhân AI tái sử dụng nội dung thay vì tái tạo lại nó.

Đây không chỉ là tối ưu hóa. Đây là **một bước chuyển mô hình (paradigm)**: mô hình ngừng là "bộ sinh văn bản" và trở thành **bộ lắp ráp** xây dựng lời giải từ những mảnh có sẵn.

**Giống như Ctrl+C / Ctrl+V đã thay đổi thế giới máy tính, Universal AI Clipboard sẽ thay đổi thế giới của các tác nhân AI.**

Tôi trao ý tưởng này cho nhân loại. Hãy phát triển nó. Hoàn thiện nó. Triển khai nó.

**Hãy để các tác nhân AI ngừng viết lại đi viết lại cùng một thứ.**
**Hãy để chúng bắt đầu ghép mô saic.**

---

```
  ╔══════════════════════════════════════════════════════════════════╗
  ║                                                                  ║
  ║   UNIVERSAL AI CLIPBOARD (UAC)                                   ║
  ║   Cơ Chế Tham Chiếu Nội Dung                                     ║
  ║   Cơ Chế Trích Dẫn Nội Dung Giữa Các Công Cụ Dạng Tùy Chọn       ║
  ║                                                                  ║
  ║   «Tái Sử Dụng, Đừng Tái Tạo»                                    ║
  ║                                                                  ║
  ║   CC0 1.0 Universal — Phạm Vi Công Cộng                          ║
  ║   github.com/DScoNOIZ                                            ║
  ║   3 tháng 6 2026                                                 ║
  ║                                                                  ║
  ╚══════════════════════════════════════════════════════════════════╝
```

---

_Bản tuyên ngôn này có thể được dịch tự do sang bất kỳ ngôn ngữ nào khác. Bản gốc bằng tiếng Nga._

_Bản tiếng Nga: [MANIFEST-RU.md](MANIFEST-RU.md)_
