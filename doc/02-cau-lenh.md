# 02 · CÂU LỆNH CXK-CPW

---

# 1. Công thức ra lệnh

```
[MODE] — chủ đề "[CHỦ ĐỀ]", tuyến phễu [1–6], định dạng [bài/reel/caption ads/infographic],
đối tượng [người bệnh 45–65+ | con cái 28–45].
```

**Bốn thông tin bắt buộc:** mode · chủ đề · tuyến phễu · định dạng.
Thiếu tuyến phễu → Agent tự map và **nói rõ đã map vào giai đoạn nào, vì sao**.
Thiếu đối tượng → mặc định người bệnh; muốn tuyến con cái thì phải ghi rõ.

---

# 2. Prompt mẫu — mode VIET

## 2.1 Bài tuyến phễu 3 (điểm quyết định)
```
VIET — chủ đề "Được khuyên thay khớp, có nên vội?", tuyến phễu 3 (Cân nhắc & nỗi sợ),
định dạng bài viết Fanpage, đối tượng con cái 28–45.
Đánh trục ① giải tỏa nỗi sợ mổ.
```

## 2.2 Bài giáo dục tuyến lạnh (không bán)
```
VIET — chủ đề "5 dấu hiệu khớp gối đang kêu cứu nhiều người bỏ qua",
tuyến phễu 1 (Nhận biết), định dạng kịch bản Reel 45 giây.
CTA mềm, không đưa giá, không đưa gói.
```

## 2.3 Myth-busting về thuốc giảm đau
```
VIET — chủ đề "Uống thuốc giảm đau mãi có hết thoái hóa không?",
tuyến phễu 3, định dạng myth-busting.
Đánh trục ② cảnh báo tác hại thuốc — dùng ví von "tắt chuông báo cháy".
```

## 2.4 Q&A bác sĩ
```
VIET — chủ đề "Có bệnh dạ dày, huyết áp thì tiêm PRP được không?",
tuyến phễu 2, định dạng Q&A bác sĩ.
Lấy đúng câu trả lời từ FAQ trong hồ sơ dịch vụ, gắn cờ HITL cho phát ngôn y khoa.
```

## 2.5 Caption ads
```
VIET — caption ads cho gói MỒI (Tầm soát & đánh giá khớp chuyên sâu),
tuyến phễu 4, đối tượng con cái 28–45.
Giá để [🔶] nếu chưa có trong file giá. Kèm gợi ý hình.
```

## 2.6 Nội dung hậu thủ thuật
```
VIET — chủ đề "Sau tiêm PRP cần làm gì trong 7 ngày đầu",
tuyến phễu 5, định dạng hướng dẫn aftercare.
Bắt buộc có khối dấu hiệu bất thường cần gọi bác sĩ ngay.
```

---

# 3. Prompt mẫu — mode BATCH

## 3.1 Một chủ đề, nhiều hook
```
BATCH — chủ đề "Bài toán kinh tế: bảo tồn khớp vs thay khớp", tuyến phễu 3.
Cho 3 hook khác loại (hook số · hook nỗi sợ · hook phản đề),
mỗi hook viết 1 bài hoàn chỉnh. Đánh số rõ.
```

## 3.2 Lô bài theo tuyến
```
BATCH — tuyến phễu 2 (Tìm hiểu) cần 5 bài giải thích cơ chế Hiệu Quả Kép
cho 5 góc khác nhau. Đề xuất danh sách 5 chủ đề trước, ghi rõ góc + định dạng.
Chưa viết nội dung, chỉ lập danh sách để tôi duyệt.
```

Duyệt xong thì:
```
Ok. Viết bài số 3 trong danh sách.
```

## 3.3 Biến thể theo đối tượng
```
BATCH — cùng chủ đề "Tiêm PRP có đau không?" viết 2 bản:
bản nói với người bệnh (cô/chú/bác) và bản nói với con cái (anh/chị).
```

---

# 4. Prompt mẫu — mode LICH

## 4.1 Lịch tháng
```
LICH — lập lịch content tháng 11/2026 cho Fanpage + TikTok, 3 bài/tuần.
Phân bổ: 40% tuyến 1–2, 40% tuyến 3, 20% tuyến 5–6.
Xuất đúng 12 cột của TEMPLATE_LICH_CONTENT.xlsx.
```

## 4.2 Kế hoạch quý
```
LICH — kế hoạch quý 4/2026: mỗi tháng 1 chủ đề trục + mục tiêu phễu trọng tâm.
Tháng 12 có mùa trở lạnh đau khớp — tận dụng.
Xuất đúng cột: Tháng · Chủ đề trục/Chiến dịch · Mục tiêu phễu trọng tâm ·
Định dạng chính · Ghi chú.
```

## 4.3 Lịch tuần nhanh
```
LICH — tuần tới (7 ngày), 1 reel + 1 bài + 1 story/ngày.
Lấy chủ đề từ sheet NGAN_HANG_CHU_DE, ưu tiên các chủ đề còn "Chưa dùng".
```

---

# 5. Prompt mẫu — mode HOOK

```
HOOK — 10 hook cho chủ đề "Khớp nhân tạo chỉ bền 10–15 năm", tuyến phễu 3.
Mỗi hook ghi loại hook + dùng cho định dạng nào.
```

```
HOOK — 8 hook nói với con cái về việc đưa cha mẹ đi tầm soát khớp.
Không hù dọa, giọng đồng hành.
```

---

# 6. Prompt hỏi đáp (không viết bài)

| Mục đích | Prompt |
|---|---|
| Chọn tuyến phễu | `Chủ đề "phân độ thoái hóa khớp 1–4" nên để tuyến phễu nào, định dạng gì?` |
| Hiểu nỗi sợ | `Người ở tuyến phễu 5 đang lo gì? Bài aftercare phải có khối gì?` |
| Kiểm tra câu chữ | `Câu này có vi phạm gì không: "Cam kết giữ khớp thật 100%, không cần mổ"?` |
| Chọn góc khác biệt | `Đối thủ nào đang phủ dày chủ đề "tiêm PRP chi phí"? Mình nên vào góc nào?` |
| Dàn ý nhanh | `Lập dàn ý bài "Vì sao tiêm mù khác tiêm dưới siêu âm" — tuyến phễu 3.` |
| Viết lại hook | `Hook này nhạt, viết lại 3 bản có con số: "Thoái hóa khớp có chữa được không?"` |
| Thuật ngữ | `Giải thích "yếu tố tăng trưởng" bằng chữ cho người 65 tuổi hiểu.` |
| Gợi ý hình | `Bài về quy trình tiêm PRP nên quay gì để không vi phạm policy Meta?` |

---

# 7. Prompt tinh chỉnh sau bản nháp

```
Giữ nguyên bài, chỉ thêm khối "ai không phù hợp" — đang thiếu chống chỉ định độ 4.
```

```
Hook đang dùng hook câu hỏi, đổi sang hook con số. Phần thân giữ nguyên.
```

```
Bài đang nói với người bệnh, đổi toàn bộ sang tuyến nói với con cái (anh/chị).
```

```
Caption dài quá cho ads. Rút còn 120 chữ, giữ hook và CTA, bỏ phần cơ chế.
```

```
Thay mọi chỗ "tế bào gốc" thành "PRP (huyết tương giàu tiểu cầu)" và báo tôi
đã sửa bao nhiêu chỗ.
```

> Agent chỉ nêu phần thay đổi, không in lại toàn bộ trừ khi bạn yêu cầu.

---

# 8. Những gì Agent sẽ TỪ CHỐI hoặc CẢNH BÁO

| Yêu cầu | Phản hồi của Agent |
|---|---|
| "Viết Wellness là số 1 / tốt nhất" | Từ chối; nêu từ cấm; đề xuất USP đo được (tiêm dưới siêu âm · theo dõi bằng số liệu) |
| "Ghi cam kết khỏi 100% / hết đau vĩnh viễn" | Từ chối; đề xuất *"cải thiện triệu chứng · hỗ trợ bảo tồn khớp"* kèm dấu `*` |
| "Nói PRP thay thế phẫu thuật" | Từ chối (Rule 4); đề xuất *"trì hoãn / giảm nguy cơ phải thay khớp"* |
| "Gọi PRP là tế bào gốc cho sang" | Từ chối (Rule 5); sửa thành *huyết tương giàu tiểu cầu (PRP)* |
| "Mời người thoái hóa độ 4 tiêm PRP" | Từ chối; nêu chống chỉ định; đề xuất hướng nội dung khác cho nhóm này |
| "Bịa giá cho khách có số mà chốt" | Từ chối; để `[🔶]`, nói rõ cần điền `cxk-gia-bs-km.md` |
| "Thêm tên bác sĩ X cho uy tín" | Kiểm tra file giá/BS; chưa điền → `[🔶]` + cờ HITL |
| "Viết testimonial cho sinh động" | Từ chối bịa nhân vật; hỏi đã có ca thật + giấy đồng ý chưa |
| "Thêm ảnh before-after vào bài" | Hỏi đã có **giấy đồng ý bệnh nhân + bác sĩ xác nhận** chưa; chưa có → không đưa vào |
| "Quay cận cảnh mũi kim lúc tiêm cho thật" | Cảnh báo vi phạm policy Meta + phản tác dụng; đề xuất b-roll máy ly tâm/siêu âm |
| "So sánh trực diện, nêu tên ACC ra" | Từ chối nêu tên hạ thấp (Rule 6); đề xuất bộ tiêu chí khách quan để khách tự đánh giá |
| "Tư vấn luôn bác ấy độ mấy" | Từ chối chẩn đoán (Rule 2); chỉ tư vấn sơ bộ + mời khám bác sĩ |
| "Gửi ảnh hồ sơ bệnh án của khách để viết case" | Từ chối (Rule 7); không nạp dữ liệu bệnh nhân lên công cụ công cộng |
| "Gọi tên Kangnam cho oai / thêm BVTM Kangnam vào đuôi" | Từ chối (Rule 9); tên đúng là **Cơ Xương Khớp – Wellness**; giải thích "Kangnam" kéo nhận thức về thẩm mỹ |
| "Viết: thuộc bệnh viện thẩm mỹ hàng đầu nên khớp cũng yên tâm" | Từ chối; mượn uy tín thẩm mỹ là sai định vị + tuyên bố không kiểm chứng được |
| "Bỏ disclaimer cho caption gọn" | Cảnh báo bắt buộc với mọi bài có nội dung điều trị; đề xuất bản disclaimer ngắn |
