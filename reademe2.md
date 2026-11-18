# Báo cáo Bài tập về nhà: Khắc phục lỗi khai báo biến số trong prompt mẫu

## 1. Bối cảnh nghiệp vụ
Để tự động hóa viết email hoặc dịch thuật cho nhiều người, chúng ta thiết kế các prompt mẫu có chứa biến số để thay thế thông tin động vào hàng loạt.

## 2. Vấn đề hiện tại (Tại sao lại lỗi?)
Khai báo các biến số lộn xộn (lúc dùng ngoặc vuông, lúc dùng ngoặc nhọn) làm hệ thống tự động hóa hoặc AI bị nhầm lẫn, không nhận diện chính xác các trường dữ liệu (field) để thực hiện thao tác thay thế dữ liệu.

---

## 3. Hiện trường giả (Prompt lỗi)
> **Prompt cũ:** Hãy viết một bài chia sẻ về Kỹ thuật Prompting Nâng cao (Logic & Chuỗi) bằng ngôn ngữ [language]. Dành cho đối tượng {audience}.

---

## 4. Yêu cầu đầu ra chi tiết

### Bước 1: Phân tích lỗi
Cách đặt biến lộn xộn `[language]` (dùng ngoặc vuông) và `{audience}` (dùng ngoặc nhọn) gây ra các vấn đề nghiêm trọng trong tự động hóa:
1. **Xung đột cú pháp (Syntax Conflict):** Các công cụ tự động hóa hoặc script (như Python, Zapier, Make) thường dựa vào một ký tự phân tách duy nhất (ví dụ: chỉ `{}` hoặc chỉ `[]`) để quét và bóc tách biến. Sự pha trộn khiến thuật toán tìm kiếm biến bị sót hoặc báo lỗi biên dịch.
2. **AI nhận diện sai ngữ cảnh:** Mô hình ngôn ngữ có thể coi một biến là chuỗi văn bản tĩnh bình thường thay vì là một placeholder (thẻ giữ chỗ) động cần được điền thông tin thực tế.
3. **Giảm tính đồng bộ và khó bảo trì:** Khi scale hệ thống lên hàng chục biến số, việc không quy chuẩn cách đặt tên và ký hiệu sẽ làm code hoặc template nhanh chóng trở nên rối rắm, khó quản lý.

### Bước 2: Đồng bộ biến số và Kết quả chạy thử

* **Prompt đã đồng bộ chuẩn:**
> Hãy viết một bài chia sẻ về Kỹ thuật Prompting Nâng cao (Logic & Chuỗi) bằng ngôn ngữ [NGÔN_NGỮ]. Dành cho đối tượng [ĐỐI_TƯỢNG].

* **Kết quả chạy thử sau khi điền dữ liệu thực tế (Ví dụ: `[NGÔN_NGỮ]` = Tiếng Việt, `[ĐỐI_TƯỢNG]` = Sinh viên công nghệ):**
> Hãy viết một bài chia sẻ về Kỹ thuật Prompting Nâng cao (Logic & Chuỗi) bằng ngôn ngữ Tiếng Việt. Dành cho đối tượng Sinh viên công nghệ.