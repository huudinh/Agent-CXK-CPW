# CHANGELOG — CXK-CPW

## v1.6 — 07/10/2026 · Bổ sung tên & mô tả ngắn cho form

**Thiếu sót phát hiện khi cài thật:** màn hình tạo mới của cả ba nền tảng đều có ô **Mô tả** (Gemini: *Nội dung mô tả* · ChatGPT: *Description* · Claude: mô tả project), nhưng gói không có sẵn đoạn nào để dán — mỗi người cài sẽ tự viết một kiểu.

**Thêm `doc/01-cai-dat.md` §0 — Tên & mô tả ngắn**
- **Tên:** `CXK-CPW Ads Writer` (18 ký tự).
- **Mô tả bản đủ** (304 ký tự) — nêu đúng 4 ý: làm gì · cho thương hiệu nào · nói bằng lời thường được · tự tránh câu vi phạm quảng cáo y tế và đánh dấu chỗ cần bác sĩ duyệt.
- **Mô tả bản 1 dòng** (121 ký tự) cho ô ngắn.
- Ghi rõ **mô tả không thay thế Instructions** — tránh người mới tưởng dán mô tả là đủ.

**Kèm theo**
- `README.md` — Quick start bước 1 trỏ sang §0.
- Trang hướng dẫn cho người mới — Bước 3 thêm khối 3 thẻ copy (tên · mô tả đủ · mô tả 1 dòng) đặt trên bảng nền tảng; cả ba tab thêm bước điền ô mô tả.

---

## v1.5 — 06/10/2026 · Vá lỗi bộ não không vừa ô Instructions của ChatGPT

**Lỗi phát hiện khi viết hướng dẫn cho người mới:** `SYSTEM-PROMPT.md` dài **14.541 ký tự**, nhưng ô **Instructions của ChatGPT Custom GPT chỉ nhận 8.000 ký tự**. Ai cài theo `doc/01-cai-dat.md` bản trước sẽ bị **cắt mất nửa sau** — mất trọn §10 guardrails pháp lý, §14 định dạng đầu ra và §16 Rules — mà không có cảnh báo nào.

**Thêm `SYSTEM-PROMPT-NGAN.md`** — bản rút gọn **6.523 ký tự** (dư 1.477 ký tự so với hạn mức). Giữ nguyên mọi luật không được phá: định danh thương hiệu · bảng từ cấm · chống chỉ định · không bịa số liệu/giá/tên bác sĩ · luật hình ảnh · HITL · khối người dùng không chuyên · định dạng đầu ra. Dòng đầu ra lệnh cho Agent **đọc `SYSTEM-PROMPT.md` trong Knowledge** để lấy chi tiết đầy đủ.

**Cách cài theo từng nền tảng — đã phân biệt rõ**

| Nền tảng | Dán vào Instructions | Upload lên Knowledge |
|---|---|---|
| **ChatGPT** Custom GPT | `SYSTEM-PROMPT-NGAN.md` (6.523) | 6 file `knowledge/` + xlsx **+ `SYSTEM-PROMPT.md`** |
| **Gemini** Gems | `SYSTEM-PROMPT.md` (bản đầy đủ) | 6 file `knowledge/` + xlsx |
| **Claude** Projects | `SYSTEM-PROMPT.md` (bản đầy đủ) | 6 file `knowledge/` + xlsx |

Gemini và Claude nhận được instructions dài nên **dán bản đầy đủ cho chất lượng cao hơn** — instructions luôn nằm trong ngữ cảnh, còn Knowledge thì phải tra mới thấy.

**Thay đổi kèm theo**
- `doc/01-cai-dat.md` — mục ChatGPT ghi rõ cảnh báo giới hạn 8.000 ký tự và đổi sang bản ngắn.
- `README.md` — bảng tài liệu ghi số ký tự của cả hai bản.

---

## v1.4 — 06/10/2026 · Mở cho người không chuyên

Trước bản này, Agent chỉ chạy đúng khi người dùng khai báo `mode · tuyến phễu · định dạng · đối tượng`. Nhân sự không làm marketing chuyên không biết những từ đó, nên hoặc không dùng được, hoặc dùng sai rồi nhận output lệch.

**Thay đổi**
- **`§15` thêm khối "Người dùng không chuyên"** — yêu cầu nói bằng lời thường là **cách dùng hợp lệ**, không phải input thiếu. Agent **tự suy** mode · tuyến phễu · định dạng · đối tượng từ chính lời họ nói (kênh họ nhắc → định dạng · ai sẽ đọc → đối tượng · họ muốn người đọc làm gì → tuyến phễu + CTA), mở đầu bằng **đúng một dòng chữ thường** *"Mình hiểu là…"* để họ soát, rồi làm luôn — không hỏi lại từng mục, không bắt họ học thuật ngữ.
- Cùng khối: **cấm dùng thuật ngữ khi nói chuyện với người dùng** — *"tuyến phễu 3"* → *"người đang cân nhắc, còn sợ mổ"* · *"hook"* → *"câu mở đầu"* · *"HITL"* → *"cần bác sĩ đọc lại trước khi đăng"*. Phiếu bàn giao vẫn xuất đầy đủ vì người duyệt cần nó.
- Chỉ hỏi lại khi đoán sai sẽ ra nội dung sai hẳn (vd không rõ bán gói nào), **tối đa 1–2 câu**, không trả lời thì chọn phương án an toàn hơn rồi nói rõ.
- **`doc/04-prompt-nguoi-moi.md` mới** — 10 prompt copy-paste được, viết như nhắn tin: quảng cáo gói khám cho con cái · bài cho người được khuyên mổ · giải thích dịch vụ bằng chữ dễ · kịch bản TikTok 45 giây · bài về thuốc giảm đau · 3 biến thể để test ads · 8 câu mở đầu · kế hoạch tuần · kế hoạch tháng mùa lạnh · bài trả lời câu khách hay hỏi. Kèm mẫu điền chỗ trống 4 dòng, 3 điều không cần lo, **2 điều phải kiểm khi nhận bài** (dấu 🔶 = thiếu giá/tên bác sĩ · dấu ⚠️ = cần bác sĩ duyệt + caption ads còn chờ GXN Sở Y tế), và cách nói khi chưa vừa ý.
- `README.md` — mục *Quick start* thêm câu lệnh mẫu dạng lời thường bên cạnh dạng khai báo; bảng tài liệu thêm file mới.

---

## v1.3 — 06/10/2026 · Đổi định danh agent sang CXK-CPW

**`CXK-CONTENT` → `CXK-CPW`.** Tên đầy đủ: **CXK-CPW — Sáng tạo nội dung ads & Kế hoạch Cơ Xương Khớp cho ads**.

Mã `CPW` khớp chuẩn đặt tên của line thẩm mỹ (`Agent-KN-CPW` — Content Production Writer), nên cả hai line dùng một quy ước. Khung mô tả đổi sang **ads-first**: trọng tâm là sáng tạo nội dung ads và lập kế hoạch nội dung *cho ads*, thay vì content chung.

**Thay đổi**
- `README.md` — tiêu đề + dòng mô tả + 3 đầu việc đổi sang khung ads.
- `SYSTEM-PROMPT.md` — tiêu đề ngoài & trong khối ▼▲; §1 đổi 3 đầu việc thành *sáng tạo nội dung ads* · *lập kế hoạch nội dung cho ads* · chuẩn hoá cấu trúc content. Version 1.3.
- `doc/01-cai-dat.md` · `doc/02-cau-lenh.md` · `doc/03-output-mau.md` · `doc/CHANGELOG.md` — tiêu đề file; tên Gem/Project gợi ý đổi thành `CXK-CPW Ads Writer`; sơ đồ luồng vận hành.

**Không đổi:** 4 chế độ (`VIET` · `BATCH` · `LICH` · `HOOK`) · quy trình 5 bước · 17 mục bộ não · cấu trúc thư mục · toàn bộ file `knowledge/` (vẫn tiền tố `cxk-`).

> Thư mục gói vẫn là `Agent-CoXuongKhop/`. Muốn khớp hẳn chuẩn line thẩm mỹ thì đổi thành `Agent-CXK-CPW/` — nói một tiếng, nhưng đây là git repo nên cần đổi cả remote nếu có.

---

## v1.2 — 06/10/2026 · Sửa định danh thương hiệu

**Thương hiệu là `CƠ XƯƠNG KHỚP – WELLNESS`, không phải "Kangnam".**

Wellness trực thuộc hệ thống Kangnam nhưng là thương hiệu phân biệt riêng: với người đọc, "Kangnam" đồng nghĩa với **thẩm mỹ** — gọi sai tên là đẩy người đang đau khớp sang nhận thức "chỗ này làm mũi, làm mắt", mất toàn bộ uy tín y khoa cơ xương khớp.

**Thay đổi**
- **Bộ não thêm `§3. ĐỊNH DANH THƯƠNG HIỆU`** — bảng đúng/sai cho tên thương hiệu · đuôi content · tên chuyên khoa; quy định **khi nào được nhắc Kangnam** (chỉ ở thông tin pháp lý: pháp nhân trên GXN nội dung QC · phạm vi giấy phép · địa chỉ cơ sở); cấm mượn uy tín thẩm mỹ để bán dịch vụ y khoa. Các mục sau dịch số: cũ §3–§16 → mới §4–§17.
- **Rule 9 mới (§16)** — không gọi thương hiệu là "Kangnam"/"BVTM Kangnam" trong content.
- **§12** đuôi content ghi rõ định danh `Cơ Xương Khớp – Wellness` + hotline.
- `README.md` — thêm mục *Định danh thương hiệu* ngay trước *Nguyên tắc tối thượng*; dòng mở đầu đổi sang `CƠ XƯƠNG KHỚP – WELLNESS`.
- `knowledge/cxk-brand-voice.md` — thêm khối **Định danh thương hiệu** lên đầu file; bỏ nhãn màu "Kangnam navy" → "navy"; thêm luật **không dùng bộ nhận diện line thẩm mỹ** cho ấn phẩm cơ xương khớp. → version 1.1.
- Header 6 file knowledge: `(CXK Kangnam)` → `(Cơ Xương Khớp – Wellness)`.
- `cxk-ban-do-doi-thu.md`: `CÁCH KANGNAM ĐÁNH KHÁC BIỆT` → `CÁCH WELLNESS ĐÁNH KHÁC BIỆT`.
- `doc/03-output-mau.md` — đuôi content mẫu đổi thành `Cơ Xương Khớp – Wellness`; dấu hiệu output đúng #1 đổi thành "hook không có tên thương hiệu, và không có chữ Kangnam ở bất kỳ đâu trong bài".
- `doc/01-cai-dat.md` — thêm **smoke test 8–9** (hỏi tên thương hiệu · từ chối hook mượn uy tín thẩm mỹ) + 2 ca xử lý sự cố; cảnh báo không upload lẫn knowledge của line thẩm mỹ `Agent-KN-CPW`.
- `doc/02-cau-lenh.md` — thêm 2 dòng Agent sẽ từ chối (gọi tên Kangnam · mượn uy tín thẩm mỹ).

**Dạng viết chuẩn đã chốt:** `Cơ Xương Khớp – Wellness` — gạch ngang `–` (en dash), khoảng trắng hai bên; dạng ngắn `Wellness`. Ràng buộc chính tả này ghi ở §3 · README · `cxk-brand-voice.md`.

**🔶 Còn chờ xác nhận:** tên **pháp nhân chính xác** dùng khi nộp hồ sơ GXN nội dung QC Sở Y tế — khác với tên thương hiệu. Hiện để `[🔶 chờ xác nhận]` ở §3 và `cxk-brand-voice.md`, không suy diễn.

---

## v1.1 — 06/10/2026 · Tái cấu trúc theo chuẩn Agent-KN-CPW

Nội dung tri thức **giữ nguyên**, chỉ đổi cấu trúc thư mục và tách bộ não ra khỏi tài liệu vận hành — để cả 3 agent line da liễu (`GEO-Plant` · `CPW` · `CPWCheck`) và agent line cơ xương khớp dùng chung một chuẩn gói.

**Cấu trúc mới**

```
Agent-CoXuongKhop/
├── README.md              ← cổng vào: nguyên tắc · 4 mode · phễu · 3 trục · quick start
├── SYSTEM-PROMPT.md       ← bộ não, khối ▼▲ dán vào Instructions
├── knowledge/             ← 6 file tri thức, upload lên nền tảng
├── doc/                   ← tài liệu vận hành, KHÔNG upload
└── templates/             ← TEMPLATE_LICH_CONTENT.xlsx
```

**Đổi tên file** — bỏ tiền tố `00_/K1_/KF_`, dùng kebab-case có tiền tố `cxk-`:

| Tên cũ | Tên mới |
|---|---|
| `00_INSTRUCTION_CXK_CONTENT.md` | `SYSTEM-PROMPT.md` *(viết lại theo khuôn §1–§17)* |
| `00_COMPLIANCE_CXK.md` | `knowledge/cxk-rao-phap-ly.md` |
| `K1_HO_SO_DICH_VU.md` | `knowledge/cxk-ho-so-dich-vu.md` |
| `K2_CHAN_DUNG_KH_HANH_TRINH.md` | `knowledge/cxk-chan-dung-hanh-trinh.md` |
| `K3_BRAND_VOICE.md` | `knowledge/cxk-brand-voice.md` |
| `K4_BAN_DO_DOI_THU.md` | `knowledge/cxk-ban-do-doi-thu.md` |
| `KF_GIA_BS_KM.md` | `knowledge/cxk-gia-bs-km.md` |
| `TEMPLATE_LICH_CONTENT.xlsx` | `templates/TEMPLATE_LICH_CONTENT.xlsx` |

**Bộ não viết lại thành 16 mục** *(v1.2 nâng lên 17)* — nội dung cũ được giữ đủ và bổ sung các mục khuôn CPW còn thiếu:

| Mục | Nguồn |
|---|---|
| §1 Role · §6 Quy trình 5 bước · §5 Bốn chế độ · §8 Công thức content · §16 Rules | đã có ở bản 1.0, giữ nguyên lõi |
| §7 Sáu giai đoạn & nỗi sợ (dạng bảng, có cột CTA) | nâng từ bảng phễu trong `cxk-chan-dung-hanh-trinh.md` lên bộ não |
| §9 Ba trục đánh mạnh & góc khác biệt | nâng từ `cxk-ban-do-doi-thu.md` |
| §10 Guardrails + bảng từ cấm rút gọn + chống chỉ định | nâng từ `cxk-rao-phap-ly.md` + `cxk-ho-so-dich-vu.md` |
| **§4 Nguyên tắc tối thượng** — gỡ nỗi sợ trước, nói phác đồ sau + **phép thử cắt thương hiệu** | **MỚI** |
| **§11 Hình ảnh/video** — tách thành mục riêng trong bộ não | **MỚI** (trước nằm rải trong compliance) |
| **§12 Khối bắt buộc cuối mọi bài** + danh sách **cấm CTA** | **MỚI** |
| **§13 Tự kiểm** — 4 tiêu chí cũ + **3 cổng chặn** (hết từ cấm · số có nguồn · đã gắn HITL) | mở rộng |
| **§14 Định dạng đầu ra** — 4 phần cho VIET/BATCH, cột cụ thể cho LICH/HOOK | mở rộng, nêu rõ tên cột |
| **§15 Khi thiếu dữ liệu** — không dừng cả bài vì một con số | **MỚI** |
| **§17 Quy tắc phản hồi** — không chào hỏi sáo rỗng, sửa nháp chỉ nêu phần thay đổi | **MỚI** |

**Tài liệu vận hành mới (`doc/`)**
- `01-cai-dat.md` — cài lên 3 nền tảng · bảng 6 file tri thức · dữ liệu chặn ads · **7 smoke test** · luồng vận hành có HITL · **11 ca xử lý sự cố**.
- `02-cau-lenh.md` — công thức ra lệnh · prompt mẫu cho cả 4 mode · prompt hỏi đáp · prompt tinh chỉnh · **14 yêu cầu Agent sẽ từ chối/cảnh báo**.
- `03-output-mau.md` — output mẫu đủ 4 phần cho mode VIET · mẫu HOOK · mẫu LICH đúng 12 cột + 5 cột quý · 4 dấu hiệu output đúng / 4 dấu hiệu sai.
- `CHANGELOG.md` — file này.

**Ràng buộc mới làm rõ trong bản này**
- Số `>85%` · `80–150tr` · `10–20%` trong hồ sơ dịch vụ là **số dạng mẫu lấy từ LDP**, chưa được duyệt công bố. Agent được dùng để dựng khung nhưng phải gắn `*` + cờ HITL, **không coi là số đã duyệt**.
- Mode `LICH` phải xuất **đúng tên cột** của file xlsx — nên upload file xlsx làm knowledge.
- Thứ tự đọc tri thức: **pháp lý trước, dữ liệu sau**.

---

## v1.0 — 09/2026

Bản đầu tiên của agent (lúc đó tên **CXK-CONTENT**), agent đơn phủ 3 đầu việc: viết content/ads social · lập kế hoạch nội dung tuần/tháng/quý · chuẩn hoá cấu trúc content. Theo công thức HCI **R·M·K·W·O**, brain brand-neutral.

**Tri thức**
- `K1` hồ sơ dịch vụ bảo tồn khớp — định vị "Giữ lại khớp thật, không dao kéo", phác đồ **Hiệu Quả Kép** (PRP + PHCN), điểm tin khác biệt, 3 gói mồi/lõi/duy trì, FAQ, chống chỉ định.
- `K2` 2 chân dung (người bệnh 45–65+ · con cái 28–45) + **phễu 6 giai đoạn** đủ 6 cột (tâm lý · nỗi sợ · thông điệp · định dạng · CTA) + 7 trục góc content chống bí ý tưởng.
- `K3` brand voice — chuyên nghiệp nhưng ấm, câu ngắn cho người lớn tuổi, xưng hô theo đối tượng, màu + font.
- `K4` bản đồ đối thủ 3 nhóm — nhóm trùng định vị bảo tồn (ACC không có PRP · Vạn Hạnh có gói bảo trì), nhóm BV lớn authority PRP, nhóm phòng khám nhỏ; 5 góc đối thủ đang win; cách đánh khác biệt.
- `KF` khung giá/bác sĩ/khuyến mãi — **để trống chờ điền**.
- `00_COMPLIANCE` — bảng 7 cặp từ cấm → từ đúng, luật hình ảnh/video, danh sách HITL bắt buộc.

**Công cụ**
- `TEMPLATE_LICH_CONTENT.xlsx` — 5 sheet: `HDSD` · `LICH_THANG` (12 cột) · `KE_HOACH_QUY` (5 cột) · `NGAN_HANG_CHU_DE` (30 chủ đề đã map theo phễu) · `TRACKER` (KPI + công thức tự phân loại SCALE / TINH CHỈNH / KILL theo mức ≥85% và ≥60%).

---

## Việc còn treo

| Hạng mục | Ảnh hưởng |
|---|---|
| **Số GXN nội dung QC Sở Y tế** | **Chặn cứng** việc bật ads Meta — không có thì mọi caption ads chỉ nằm ở trạng thái chờ |
| Tên + học hàm + chứng chỉ + ảnh bác sĩ | LDP đang để `[Tên bác sĩ]`; mọi bài có phát ngôn y khoa thiếu người đứng tên → không qua HITL |
| Bảng giá thật 3 gói | Không viết được content tuyến phễu 4 (Thực hiện) và caption có giá |
| Khuyến mãi thật + thời hạn + số suất | Không viết được offer/đếm ngược cho mùa cao điểm (tháng 12 trở lạnh) |
| Duyệt công bố số liệu `>85%` · `80–150tr` + nguồn | Trục ③ bài toán kinh tế — trục chuyển đổi mạnh nhất — đang phải để `*` + HITL ở mọi bài |
| Ca thật + giấy đồng ý dùng hình/before-after | Chưa dùng được bằng chứng mạnh nhất; 2 testimonial hiện tại là mẫu, phải thay |
| Quét **Facebook Ad Library** lấy ads đối thủ đang chạy | `cxk-ban-do-doi-thu.md` hiện dựa trên research web, chưa có dữ liệu ads thật |
| Mã hex chính xác bộ nhận diện **Wellness** | `cxk-brand-voice.md` đang tạm dùng hệ HCI |
| KPI định lượng (số lead/tháng · CPL mục tiêu) | Sheet `TRACKER` chưa có mốc để so → cột `% đạt` chưa phán được SCALE/KILL |
