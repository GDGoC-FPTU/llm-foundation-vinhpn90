# Ngày 1 — Bài Tập & Phản Ánh
## Nền Tảng LLM API | Phiếu Thực Hành

**Thời lượng:** 1:30 giờ  
**Cấu trúc:** Lập trình cốt lõi (60 phút) → Bài tập mở rộng (30 phút)

---

## Phần 1 — Lập Trình Cốt Lõi (0:00–1:00)

Chạy các ví dụ trong Google Colab tại: https://colab.research.google.com/drive/172zCiXpLr1FEXMRCAbmZoqTrKiSkUERm?usp=sharing

Triển khai tất cả TODO trong `template.py`. Chạy `pytest tests/` để kiểm tra tiến độ.

**Điểm kiểm tra:** Sau khi hoàn thành 4 nhiệm vụ, chạy:
```bash
python template.py
```
Bạn sẽ thấy output so sánh phản hồi của GPT-4o và GPT-4o-mini.

---

## Phần 2 — Bài Tập Mở Rộng (1:00–1:30)

### Bài tập 2.1 — Độ Nhạy Của Temperature
Gọi `call_openai` với các giá trị temperature 0.0, 0.5, 1.0 và 1.5 sử dụng prompt **"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**

**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2–3 câu)
> Khi temperature thấp như 0.0, phản hồi thường ổn định, trực tiếp và ít biến thể hơn. Khi tăng lên 0.5, 1.0 và 1.5, câu trả lời có xu hướng đa dạng, sáng tạo hơn nhưng cũng dễ dài dòng hoặc kém nhất quán hơn.

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Tôi sẽ đặt khoảng 0.2–0.4 để chatbot trả lời nhất quán, đúng chính sách và ít bịa hơn. Chatbot hỗ trợ khách hàng cần độ tin cậy và tính dự đoán cao hơn sự sáng tạo.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> Workload có 10.000 × 3 × 350 = 10.500.000 token mỗi ngày. Với bảng giá trong `template.py`, GPT-4o đắt hơn GPT-4o-mini khoảng 33,3 lần vì cả giá input và output của GPT-4o đều gấp khoảng 33,3 lần GPT-4o-mini.

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> GPT-4o xứng đáng khi cần suy luận phức tạp, phân tích tài liệu quan trọng, hoặc phản hồi có ảnh hưởng lớn đến quyết định kinh doanh. GPT-4o-mini phù hợp hơn cho tác vụ khối lượng lớn, rủi ro thấp như phân loại câu hỏi, tóm tắt ngắn, gợi ý câu trả lời nháp hoặc chatbot FAQ.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> Streaming quan trọng nhất khi phản hồi dài hoặc người dùng cần cảm giác hệ thống đang xử lý ngay, ví dụ chatbot, trợ lý viết nội dung, hoặc công cụ giải thích từng bước. Non-streaming phù hợp hơn khi cần kết quả hoàn chỉnh trước khi hiển thị, chẳng hạn API backend, phân loại dữ liệu, trích xuất JSON, kiểm duyệt nội dung hoặc các tác vụ mà giao diện chỉ cần nhận một kết quả cuối cùng.


## Danh Sách Kiểm Tra Nộp Bài
- [ ] Tất cả tests pass: `pytest tests/ -v`
- [ ] `call_openai` đã triển khai và kiểm thử
- [ ] `call_openai_mini` đã triển khai và kiểm thử
- [ ] `compare_models` đã triển khai và kiểm thử
- [ ] `streaming_chatbot` đã triển khai và kiểm thử
- [ ] `retry_with_backoff` đã triển khai và kiểm thử
- [ ] `batch_compare` đã triển khai và kiểm thử
- [ ] `format_comparison_table` đã triển khai và kiểm thử
- [ ] `exercises.md` đã điền đầy đủ
- [ ] Sao chép bài làm vào folder `solution` và đặt tên theo quy định 
