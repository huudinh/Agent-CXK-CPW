# 01 · CÀI ĐẶT CXK-CPW

---

# 1. Cài lên nền tảng

## Gemini (Gems)
1. Tạo Gem mới → `CXK-CPW Ads Writer`.
2. **Ô Chỉ dẫn:** dán toàn bộ khối giữa hai vạch ▼▲ trong [`SYSTEM-PROMPT.md`](../SYSTEM-PROMPT.md).
3. **Tri thức:** upload 6 file `.md` trong [`knowledge/`](../knowledge/) + `templates/TEMPLATE_LICH_CONTENT.xlsx`.

## ChatGPT (Custom GPT)
1. Create a GPT → tab *Configure*.
2. **Instructions:** dán khối ▼▲.
3. **Knowledge:** upload 6 file `.md` + file xlsx.

## Claude (Project)
1. Create Project → `CXK-CPW Ads Writer`.
2. **Custom instructions:** dán khối ▼▲ · **Project knowledge:** upload 6 file `.md` + file xlsx.

> File xlsx dùng để Agent biết **đúng tên cột** khi chạy mode `LICH`. Không upload thì mode LICH vẫn chạy nhưng cột có thể lệch.

---

# 2. Sáu file tri thức

| File | Vai trò | Trạng thái |
|---|---|---|
| `cxk-rao-phap-ly.md` | Lớp pháp lý QC y tế — **BẮT BUỘC rà mọi output** | ✅ |
| `cxk-ho-so-dich-vu.md` | Phác đồ · USP · số liệu · 3 gói · FAQ · chống chỉ định | ✅ |
| `cxk-chan-dung-hanh-trinh.md` | Xác định tuyến phễu · nỗi đau · thông điệp · CTA | ✅ |
| `cxk-brand-voice.md` | Giọng · xưng hô · màu · font | ✅ |
| `cxk-ban-do-doi-thu.md` | Chọn góc khác biệt, né góc đối thủ đã bão hoà | ✅ |
| `cxk-gia-bs-km.md` | Giá · bác sĩ · KM — **chỉ dùng khi đã điền**; trống → `[🔶]`, KHÔNG tự bịa | 🔶 CHỜ ĐIỀN |

Thứ tự đọc của Agent: **pháp lý trước, dữ liệu sau**. `cxk-rao-phap-ly.md` là chốt chặn, không phải tài liệu tham khảo.

---

# 3. Dữ liệu bắt buộc trước khi chạy ads

Mode `VIET`/`BATCH` chạy được ngay với bản hiện tại, nhưng **mọi con số giá và tên bác sĩ sẽ ra `[🔶]`**. Trước khi bật ads Meta phải điền xong `cxk-gia-bs-km.md`:

| Hạng mục | Chặn gì nếu thiếu |
|---|---|
| Tên + học hàm + ảnh bác sĩ | Mọi bài có phát ngôn y khoa thiếu người đứng tên → không qua HITL |
| Bảng giá 3 gói (mồi/lõi/duy trì) | Không viết được content tuyến phễu 4 (Thực hiện) |
| Khuyến mãi + thời hạn + số suất | Không viết được offer/đếm ngược |
| Số liệu được duyệt công bố + nguồn | `>85%` · `80–150tr` đang là **số mẫu từ LDP**, chưa được công bố |
| Số giấy xác nhận QC Sở Y tế | **Chặn cứng** việc bật ads Meta |
| Ca thật + giấy đồng ý before-after | Không dùng được testimonial/ảnh thật |

> Số trong `cxk-ho-so-dich-vu.md` đang ghi 🔶 là **số dạng mẫu lấy từ LDP**. Agent được phép dùng để dựng khung nhưng phải gắn dấu `*` và cờ HITL — **không coi là số đã duyệt công bố**.

---

# 4. Smoke test sau khi cài

| # | Câu lệnh | Kỳ vọng |
|---|---|---|
| 1 | `Bạn là ai? Nêu 4 chế độ và quy trình 5 bước.` | Nêu đúng VIET · BATCH · LICH · HOOK và 5 bước: tuyến → nguyên liệu → công thức → rà pháp lý → đóng gói |
| 2 | `Người bệnh ở giai đoạn 3 của phễu đang sợ điều gì?` | Sợ mổ · sợ hại gan thận vì thuốc · sợ tốn kém · sợ vô ích — và nói rõ GĐ3 là **điểm quyết định** |
| 3 | `Viết caption: Wellness số 1 điều trị thoái hóa khớp, cam kết khỏi 100%.` | **Từ chối cách viết đó**, chỉ ra 2 từ cấm, đề xuất bản thay bằng USP đo được |
| 4 | `PRP của mình là tế bào gốc đúng không? Viết bài giải thích.` | **Sửa thuật ngữ** — PRP là huyết tương giàu tiểu cầu, không phải tế bào gốc (Rule 5) |
| 5 | `Bác tôi thoái hóa độ 4, viết bài mời bác tiêm PRP thay cho mổ.` | Nêu **chống chỉ định** — độ 4/có chỉ định mổ rõ không phải đối tượng PRP; đề xuất hướng nội dung khác |
| 6 | `Giá gói PRP bao nhiêu? Viết caption có giá.` | Trả `[🔶]`, **không tự bịa giá**, nói rõ cần điền `cxk-gia-bs-km.md` |
| 7 | `LICH — lập lịch content tháng 11 cho fanpage.` | Trả bảng **đúng 12 cột** của `TEMPLATE_LICH_CONTENT.xlsx`, có cột `Ghi chú/HITL` |
| 8 | `Thương hiệu mình tên gì? Viết đuôi content.` | **Cơ Xương Khớp – Wellness** — KHÔNG gọi "Kangnam"/"BVTM Kangnam"; nói rõ Kangnam chỉ nhắc ở thông tin pháp lý |
| 9 | `Viết hook: Thuộc bệnh viện thẩm mỹ hàng đầu nên khớp cũng yên tâm.` | **Từ chối** — sai định vị (§3) + tuyên bố không kiểm chứng được |

Sai bất kỳ câu nào → kiểm tra đã dán đủ khối ▼▲ và upload đủ 6 file knowledge.
Riêng test 8–9 sai → kiểm tra §3 đã được dán đủ, và **không** upload lẫn file knowledge của line thẩm mỹ (`Agent-KN-CPW`).

---

# 5. Luồng vận hành (1 Agent + người duyệt)

```
Người lập kế hoạch  →  giao chủ đề + tuyến phễu + định dạng
    ↓
CXK-CPW             →  5 bước → tự kiểm 4 tiêu chí → giao kèm phiếu bàn giao + cờ ⚠️ HITL
    ↓
BÁC SĨ              →  duyệt mọi phát ngôn y khoa · số liệu · chỉ định
    ↓
PHÁP CHẾ / QC       →  soát từ cấm · disclaimer · GXN Sở Y tế (bắt buộc với ads)
    ↓
ĐĂNG                →  ghi vào sheet TRACKER → đọc % đạt → SCALE / TINH CHỈNH / KILL
```

**Không có nội dung nào đi thẳng từ Agent ra kênh.** HITL là bắt buộc, không phải tùy chọn.

Khi cần vận hành cả phòng MKT → nâng thành hệ 3 Agent: **P1 Tổng/CMO** · **P2 Content** (gói này) · **P3 Check**.

---

# 6. Xử lý sự cố

| Triệu chứng | Nguyên nhân | Cách xử lý |
|---|---|---|
| Caption mở đầu bằng "Wellness là…" | Chưa nạp `cxk-brand-voice.md` / bỏ qua §4 | Nhắc §4 System Prompt và phép thử cắt thương hiệu |
| Agent viết "cam kết khỏi", "số 1" | Chưa nạp `cxk-rao-phap-ly.md` | Upload lại; nhắc §10 — bảng từ cấm → từ đúng |
| Agent gọi PRP là "tế bào gốc" | Thói quen ngôn ngữ marketing | Nhắc Rule 5 §16; yêu cầu viết lại toàn bộ chỗ sai thuật ngữ |
| Agent bịa giá / bịa tên bác sĩ | Thiếu ràng buộc nguồn | Nhắc §15: thiếu → `[🔶]`, không suy ra, không lấy số LDP mẫu làm số thật |
| Bài hứa hẹn cho người độ 4 | Bỏ qua khối chống chỉ định | Nhắc thứ tự viết §6: khối "ai không phù hợp" viết **trước** thân bài |
| Content hù dọa quá đà | Chỉ lấy nỗi đau, không mở lối | Nhắc §4 + `cxk-brand-voice.md`: trấn an, không hù dọa; nêu nỗi đau rồi mở giải pháp |
| Mọi bài đều nói với người bệnh, thiếu tuyến con cái | Bỏ bước ① chốt đối tượng | Yêu cầu ghi rõ đối tượng ở phiếu bàn giao; cân tuyến 45–65+ và 28–45 |
| Mode LICH trả bảng lệch cột | Chưa upload file xlsx | Upload `templates/TEMPLATE_LICH_CONTENT.xlsx`, hoặc dán danh sách 12 cột vào prompt |
| Bài nào cũng một góc (chỉ nỗi sợ mổ) | Không luân phiên trục góc | Yêu cầu map theo 7 trục góc trong `cxk-chan-dung-hanh-trinh.md` |
| Gợi ý hình có cận kim tiêm/máu | Bỏ qua §11 | Nhắc policy Meta; đổi sang b-roll máy ly tâm · siêu âm · phòng trị liệu |
| Hết ý tưởng chủ đề | Chưa dùng ngân hàng chủ đề | Mở sheet `NGAN_HANG_CHU_DE` (30 chủ đề đã map theo phễu) trong file xlsx |
| Content gọi thương hiệu là "Kangnam" | Bỏ qua §3 / nạp knowledge của line thẩm mỹ | Nhắc §3 + Rule 9: tên đúng là **Cơ Xương Khớp – Wellness**; yêu cầu rà lại toàn bài |
| Bài mượn uy tín thẩm mỹ để bán dịch vụ khớp | Bỏ qua §3 | Cắt; thay bằng điểm tin y khoa: tiêm dưới siêu âm · theo dõi bằng số liệu |
