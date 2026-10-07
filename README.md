# 🦴 CXK-CPW — Sáng tạo nội dung ads & Kế hoạch Cơ Xương Khớp cho ads

> Version 1.4 · AI **sáng tạo nội dung ads và lập kế hoạch nội dung cho ads** của **CƠ XƯƠNG KHỚP – WELLNESS**: mảng điều trị **bảo tồn khớp** (PRP + phục hồi chức năng) — viết cho một người thật đang sợ phải mổ, và cho đứa con đang thay cha mẹ tìm chỗ chữa.

Agent đơn, phủ trọn 3 đầu việc: **sáng tạo nội dung ads & content social** · **lập lịch nội dung cho ads theo tuần/tháng/quý** · **chuẩn hoá cấu trúc content** — vận hành theo hành trình khách hàng 6 giai đoạn (Cold → LTV).

Theo công thức HCI **R·M·K·W·O**. Bộ não ([`SYSTEM-PROMPT.md`](SYSTEM-PROMPT.md)) viết brand-neutral; thương hiệu · định vị · ví dụ nằm ở [`knowledge/`](knowledge/) → mở rộng sang brand khác không phải sửa bộ não.

---

## 👉 Chưa biết bắt đầu từ đâu?

### **[MỞ HƯỚNG DẪN CHO NGƯỜI MỚI →](https://claude.ai/artifact/D2XdD2d63tWhT4St64AgCg)**

Trang hướng dẫn 5 bước, dành cho người **chưa từng dùng GitHub** và **chưa từng tự cài AI Agent**: tải bộ file (một nút) → hiểu file nào để làm gì → cài trên ChatGPT / Gemini / Claude → kiểm tra cài đúng chưa → 10 câu lệnh đầu tiên bấm copy là dùng được.

Nội dung của cả 7 file đã nhúng sẵn trong trang, nên **không tải được GitHub vẫn cài được**.

> ⚠️ Link này là trang riêng tư. Người ngoài mở sẽ báo không có quyền — chủ sở hữu phải bấm **Share** trên trang để cấp quyền trước.

---

## Định danh thương hiệu — gọi đúng tên

Thương hiệu là **CƠ XƯƠNG KHỚP – WELLNESS**. Dạng ngắn trong câu: **Wellness**.

**Viết đúng một dạng duy nhất:** `Cơ Xương Khớp – Wellness` — gạch ngang `–` (en dash), khoảng trắng hai bên. Không gạch nối `-`, không gạch dài `—`, không đảo thứ tự.

**Wellness trực thuộc hệ thống Kangnam, nhưng là thương hiệu phân biệt riêng.** Với người đọc, "Kangnam" đồng nghĩa với **thẩm mỹ** — gọi sai tên là đẩy người đang đau khớp sang nhận thức "chỗ này làm mũi, làm mắt", mất toàn bộ uy tín y khoa cơ xương khớp vừa xây.

| Việc | Đúng | Sai |
|---|---|---|
| Gọi tên thương hiệu | *Cơ Xương Khớp – Wellness* · *Wellness* | ❌ *Kangnam* · *Bệnh viện Thẩm mỹ Kangnam* |
| Đuôi content / định danh | `Cơ Xương Khớp – Wellness` + hotline | ❌ `Chuyên khoa Cơ Xương Khớp — BVTM Kangnam` |
| Gọi tên chuyên khoa | *chuyên khoa cơ xương khớp* · *điều trị bảo tồn khớp* | ❌ *chuyên khoa thẩm mỹ* · *viện thẩm mỹ* |

**Chỉ nhắc Kangnam** khi bắt buộc về pháp lý/hồ sơ (pháp nhân trên GXN nội dung QC · phạm vi giấy phép · địa chỉ cơ sở), ghi dạng *"thuộc hệ thống Kangnam"* ở phần thông tin pháp lý — **không** đưa lên hook · tiêu đề · tên thương hiệu dẫn. Và **không mượn uy tín thẩm mỹ** để bán dịch vụ y khoa.

> 🔶 Tên pháp nhân chính xác dùng khi nộp hồ sơ QC: **chờ xác nhận**.

---

## Nguyên tắc tối thượng

> **Gỡ nỗi sợ trước, nói phác đồ sau. Nêu nỗi đau rồi mở lối giải pháp — không hù dọa để bán.**

**Phép thử sau mỗi bài:** *"Nếu cắt tên Wellness ra khỏi bài này, nó còn hữu ích với người đang đau khớp không?"*
Phải là **CÓ**. Bài chỉ hữu ích khi có tên thương hiệu là bài quảng cáo — không phải content y khoa.

```
❌ "Wellness là địa chỉ số 1 điều trị thoái hóa khớp không cần phẫu thuật..."
✅ "Khớp gối cứng vào buổi sáng, phải xoa bóp 10–15 phút mới đứng dậy được là dấu
   hiệu sụn đã mòn, không phải 'già thì phải chịu'. Ở độ 1–3, khớp vẫn còn cơ hội
   bảo tồn — mỗi tháng chần chừ là sụn mòn thêm, không mọc lại."
```

---

## Bốn chế độ

| Mode | Làm gì | Input tối thiểu |
|---|---|---|
| **VIET** | Viết 1 bài/caption đơn lẻ | chủ đề + tuyến phễu + định dạng |
| **BATCH** | Nhiều biến thể cùng chủ đề (1 chủ đề → 3 hook, mỗi hook 1 bài) | chủ đề + số biến thể |
| **LICH** | Kế hoạch tuần/tháng/quý → xuất đúng cột [`templates/TEMPLATE_LICH_CONTENT.xlsx`](templates/) | phạm vi thời gian |
| **HOOK** | Bắn nhanh 5–10 hook cho 1 chủ đề | chủ đề |

---

## Quy trình 5 bước (VIET / BATCH)

```
① Xác định tuyến phễu      ② Rút nguyên liệu (USP · số liệu · góc khác biệt)
③ Dựng theo công thức      ④ Rà pháp lý (từ cấm → từ đúng)
⑤ Đóng gói + cờ ⚠️ HITL
```

**Thứ tự viết bắt buộc:** chốt tuyến phễu → **hook** → khối "ai không phù hợp / chống chỉ định" → thân bài → CTA → đuôi content.

---

## Hành trình 6 giai đoạn — nỗi sợ phải trả lời

| GĐ | Nỗi sợ chi phối | CTA |
|---|---|---|
| 1 **NHẬN BIẾT** (Cold) | Nghĩ "già phải chịu", chưa biết có giải pháp | Theo dõi / Lưu / Gửi ba mẹ |
| 2 **TÌM HIỂU** (Warm) | PRP là gì, có thật không, khác thuốc chỗ nào | Nhắn tin hỏi |
| 3 **CÂN NHẮC & NỖI SỢ** ★★★ | **Sợ mổ · sợ hại gan thận vì thuốc · sợ tốn kém · sợ vô ích** | Đăng ký tầm soát |
| 4 **THỰC HIỆN** (Hot) | Chọn đâu uy tín, giá bao nhiêu, có phát sinh không | Giữ suất / Hotline |
| 5 **TRẢI NGHIỆM & HẬU THỦ THUẬT** | Có hiệu quả không, chăm sóc sao, bao giờ đỡ | Tái khám đúng lịch |
| 6 **GẮN BÓ & MỞ RỘNG** (LTV) | Duy trì sao, phòng tái phát | Gia hạn / Giới thiệu |

**Giai đoạn 3 là điểm quyết định.** GĐ1–2 giữ giọng giáo dục, CTA mềm; GĐ3–4 mới được đưa offer rõ.
Nỗi sợ phải được gọi tên **ngay trong hook, bằng chính lời khách**.

---

## Ba trục đánh mạnh

| # | Trục | Lõi lập luận |
|---|---|---|
| ① | **Giải tỏa nỗi sợ mổ** | Khớp nhân tạo tuổi thọ 10–15 năm → hết tuổi thọ phải mổ lại |
| ② | **Cảnh báo thuốc giảm đau** | "Tắt chuông báo cháy" — hại dạ dày · gan · thận, bệnh vẫn tiến triển |
| ③ | **Bài toán kinh tế** | Chi phí chỉ **10–20%** so với thay khớp (thay khớp 80–150tr/khớp)* |

**USP cắm cờ trong mọi content:** **HIỆU QUẢ KÉP = PRP (tái tạo bên trong) + PHCN Shockwave/Laser (chỉnh & gia cố bên ngoài)** — ô trống mà ACC (không có PRP) và bệnh viện lớn (không all-in bảo tồn) đều chưa chiếm.
**Điểm tin:** tiêm **dưới hướng dẫn siêu âm** · theo dõi bằng **số liệu** (VAS · biên độ gập duỗi · siêu âm khe khớp).

---

## Quick start (4 bước)

> Người mới nên dùng [**trang hướng dẫn từng bước**](https://claude.ai/artifact/D2XdD2d63tWhT4St64AgCg) thay cho mục này.

1. Tạo 1 Project / GPT / Gem mới. **Tên** và **mô tả ngắn** để dán vào form: xem [`doc/01-cai-dat.md` §0](doc/01-cai-dat.md).
2. **Instructions:** dán toàn bộ khối giữa hai vạch ▼▲ trong [`SYSTEM-PROMPT.md`](SYSTEM-PROMPT.md).
3. **Knowledge:** upload 6 file `.md` trong [`knowledge/`](knowledge/) + [`templates/TEMPLATE_LICH_CONTENT.xlsx`](templates/).
4. Gọi 1 trong 4 chế độ: `VIET` · `BATCH` · `LICH` · `HOOK`.

**Câu lệnh mẫu — người dùng quen thuật ngữ:**
```
VIET — chủ đề "Được khuyên thay khớp, có nên vội?", tuyến phễu 3 (Cân nhắc & nỗi sợ),
định dạng bài viết Fanpage, đối tượng con cái 28–45.
```

**Câu lệnh mẫu — người không chuyên** (cách này cũng chạy đúng, xem [doc/04-prompt-nguoi-moi.md](doc/04-prompt-nguoi-moi.md)):
```
Mình muốn chạy quảng cáo Facebook cho gói khám tầm soát khớp. Người đọc là con cái
30–45 tuổi đang lo bố mẹ bị đau khớp gối. Viết giúp mình bài ngắn, đọc xong là muốn
đăng ký cho bố mẹ đi khám.
```
Agent tự suy mode · tuyến phễu · định dạng · đối tượng, mở đầu bằng một dòng *"Mình hiểu là…"* để bạn soát, rồi làm luôn.

---

## Đầu ra

**Mode VIET / BATCH** — 4 phần, đúng thứ tự:

1. **PHIẾU BÀN GIAO** — mode · tuyến phễu · đối tượng · định dạng · chủ đề · góc đánh · nỗi sợ đã gỡ · số liệu dùng + nguồn · từ cấm đã thay · cờ ⚠️ HITL · còn thiếu `[🔶]`
2. **NỘI DUNG** — Hook → Vấn đề → Giải pháp (Hiệu Quả Kép) → CTA/ưu đãi → Đuôi content
3. **GỢI Ý HÌNH / VIDEO** — tuân policy: không cận kim tiêm/máu
4. **GHI CHÚ CHO NGƯỜI DUYỆT** — từng điểm cần bác sĩ/pháp chế duyệt

**Mode LICH** — bảng đúng cột xlsx: `Ngày · Thứ · Tuyến phễu · Định dạng · Chủ đề · Hook · Thông điệp lõi · CTA · Kênh · Người làm · Trạng thái · Ghi chú/HITL`

**4 tiêu chí tự kiểm trước khi giao:** có logic · có mục tiêu/tuyến rõ · (LICH) có timeline · có CTA/Action.
Cộng cổng chặn: **không còn từ cấm nào · mọi con số có nguồn hoặc `[🔶]` · đã gắn ⚠️ HITL đúng chỗ.**

---

## Tài liệu

| File | Nội dung | Trạng thái |
|---|---|---|
| [**Trang hướng dẫn cho người mới**](https://claude.ai/artifact/D2XdD2d63tWhT4St64AgCg) | 5 bước từ tải file đến 10 câu lệnh đầu tiên · nhúng sẵn nội dung 7 file · nút copy | 🔒 cần Share |
| [SYSTEM-PROMPT.md](SYSTEM-PROMPT.md) | Bộ não Agent — 17 mục, dán vào Instructions · **14.541 ký tự** | ✅ |
| [SYSTEM-PROMPT-NGAN.md](SYSTEM-PROMPT-NGAN.md) | Bản ngắn **6.523 ký tự** — chỉ dùng cho **ChatGPT Custom GPT** (ô Instructions giới hạn 8.000 ký tự) | ✅ |
| [knowledge/cxk-rao-phap-ly.md](knowledge/cxk-rao-phap-ly.md) | Lớp pháp lý QC y tế: từ cấm → từ đúng · disclaimer · HITL | ✅ |
| [knowledge/cxk-ho-so-dich-vu.md](knowledge/cxk-ho-so-dich-vu.md) | Phác đồ Hiệu Quả Kép · USP · số liệu · 3 gói · FAQ · chống chỉ định | ✅ |
| [knowledge/cxk-chan-dung-hanh-trinh.md](knowledge/cxk-chan-dung-hanh-trinh.md) | 2 chân dung + phễu 6 giai đoạn + trục góc content | ✅ |
| [knowledge/cxk-brand-voice.md](knowledge/cxk-brand-voice.md) | Giọng nói · xưng hô · bảng màu · font | ✅ |
| [knowledge/cxk-ban-do-doi-thu.md](knowledge/cxk-ban-do-doi-thu.md) | Đối thủ · góc đang win · cách đánh khác biệt | ✅ |
| [knowledge/cxk-gia-bs-km.md](knowledge/cxk-gia-bs-km.md) | Bác sĩ · bảng giá · khuyến mãi | 🔶 **CHỜ ĐIỀN** |
| [templates/TEMPLATE_LICH_CONTENT.xlsx](templates/) | Lịch tháng/quý + ngân hàng 30 chủ đề + tracker | ✅ |
| [doc/01-cai-dat.md](doc/01-cai-dat.md) | Cài đặt · smoke test · xử lý sự cố | ✅ |
| [doc/02-cau-lenh.md](doc/02-cau-lenh.md) | Công thức ra lệnh 4 mode · prompt mẫu · điều Agent sẽ từ chối | ✅ |
| [doc/03-output-mau.md](doc/03-output-mau.md) | Output mẫu 4 mode · dấu hiệu bài đúng/sai | ✅ |
| [doc/04-prompt-nguoi-moi.md](doc/04-prompt-nguoi-moi.md) | **10 prompt mẫu cho người không chuyên** — nói bằng lời thường, không cần thuật ngữ | ✅ |
| [doc/CHANGELOG.md](doc/CHANGELOG.md) | Lịch sử · việc còn treo | ✅ |

> **Quy ước:** version ghi trong header từng file, **KHÔNG** gắn version vào tên file.

---

## 🔶 Dữ liệu cần bổ sung trước khi chạy ads

Điền vào [`knowledge/cxk-gia-bs-km.md`](knowledge/cxk-gia-bs-km.md):

- Tên + học hàm/chứng chỉ + ảnh thật bác sĩ (LDP đang để `[Tên bác sĩ]`).
- Bảng giá thật 3 gói (mồi / lõi / duy trì).
- Chương trình khuyến mãi thật + thời hạn + số suất.
- Số liệu được duyệt công bố (`>85%`, `80–150tr`…) + nguồn.
- **Số giấy xác nhận nội dung QC Sở Y tế** — cần trước khi bật ads Meta.
- Ca thật thay 2 testimonial mẫu + giấy đồng ý dùng hình/ảnh before-after.

---

## Ranh giới

Không cam kết kết quả y khoa ("khỏi 100% · giữ khớp 100% · số 1 · tốt nhất · không đau") · không chẩn đoán/kê đơn/khẳng định cấp độ bệnh của khách · không nói PRP **"thay thế phẫu thuật"** (chỉ *trì hoãn / giảm nguy cơ phải thay khớp*) · không gọi PRP là **"tế bào gốc"** · không nêu tên hạ thấp đối thủ · không nạp CCCD/hồ sơ bệnh án/ảnh khách lên công cụ công cộng.

**PRP không chỉ định cho:** thoái hóa độ 4 nặng · có chỉ định mổ rõ · nhiễm trùng da tại chỗ → **không hứa hẹn cho nhóm này**.

**Không bịa** số liệu · tỷ lệ · giá · tên bác sĩ · học hàm · số ca · case bệnh nhân · khuyến mãi. Thiếu → `[🔶]`, không lấp bằng chữ chung chung.

Mọi nội dung gửi khách/đăng ads phải qua **người duyệt (human-in-the-loop)**.
