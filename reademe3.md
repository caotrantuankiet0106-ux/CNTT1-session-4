# Báo cáo Giải pháp Kỹ thuật Prompting Nâng cao (Logic & Chuỗi)
**Môn học:** Kỹ Năng Prompting với AI (Session 04)  
**Bài tập:** Bài tập thực hành tổng hợp

---

## 1. Bối cảnh bài toán thực tế
Xây dựng một giải pháp tự động hóa toàn diện nhằm xử lý dữ liệu đầu vào phức tạp thông qua việc tích hợp các kỹ thuật nâng cao: **Chain-of-Thought (CoT)**, **Prompt Chaining (Chuỗi Prompt)**, và **Cơ chế xử lý đứt gãy ngữ cảnh**. Hệ thống cần đảm bảo chạy tuần tự khép kín, tối ưu hóa token và chống sập hệ thống (crash) khi gặp dữ liệu dị biệt.

---

## 2. Thiết kế giải pháp Prompt Chaining (Chuỗi tuần tự khép kín)

Giải pháp được chia thành 3 bước nối tiếp nhau (Pipeline), trong đó đầu ra của bước trước là đầu vào của bước tiếp theo:

* **Bước 1 (Phân tích Logic & Làm sạch dữ liệu - CoT):** Nhận diện dữ liệu đầu vào, áp dụng suy luận từng bước để chuẩn hóa thông tin và loại bỏ dữ liệu dị biệt (anomalies).
* **Bước 2 (Xử lý tác vụ chính - Prompt Chaining):** Thực thi yêu cầu cốt lõi dựa trên dữ liệu đã được làm sạch từ Bước 1.
* **Bước 3 (Kiểm tra định dạng & Chống đứt gãy):** Rà soát lại toàn bộ kết quả, ép buộc tuân thủ ràng buộc định dạng đầu ra và kích hoạt lệnh khôi phục ngữ cảnh nếu luồng phản hồi bị ngắt quãng.

---

## 3. Prompt thực thi các bước (System & User Prompts)

### Bước 1: Prompt phân tích & Làm sạch (CoT)
```text
[SYSTEM]
Bạn là một kỹ sư tiền xử lý dữ liệu AI. Hãy phân tích dữ liệu đầu vào [RAW_DATA] theo phương pháp Chain-of-Thought. 
Nhiệm vụ:
1. Suy luận từng bước để phát hiện các dị biệt (dữ liệu thiếu, sai định dạng, ký tự lạ).
2. Nếu phát hiện dị biệt, áp dụng cơ chế dự phòng (fallback value) thay vì làm gián đoạn hệ thống.
3. Xuất ra một JSON sạch chứa dữ liệu đã chuẩn hóa.

[USER]
Dữ liệu đầu vào cần xử lý: [RAW_DATA]