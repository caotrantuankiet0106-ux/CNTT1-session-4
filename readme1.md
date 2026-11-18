# Báo cáo Bài tập về nhà: Sửa đổi prompt thiếu cấu trúc ràng buộc định dạng

## 1. Bối cảnh nghiệp vụ
Khi học về Kỹ thuật Prompting Nâng cao (Logic & Chuỗi), chúng ta cần AI trả về kết quả ngắn gọn để dán nhanh vào báo cáo hoặc tài liệu học tập.

## 2. Vấn đề hiện tại (Tại sao lại lỗi?)
Prompt cũ viết quá ngắn làm AI sinh ra hàng loạt câu chào hỏi xã giao dông dài, giải thích lòng vòng không cần thiết, gây mất thời gian biên tập.

---

## 3. Hiện trường giả (Prompt lỗi)
> **Prompt cũ:** Hãy giải thích ngắn gọn các nội dung của Chain-of-Thought, Prompt Chaining, xử lý đứt gãy.

---

## 4. Yêu cầu đầu ra chi tiết

### Bước 1: Phân tích lỗi
Trong câu trả lời của prompt cũ, AI thường sinh ra 3 phần văn bản thừa thãi sau:
1. **Lời chào dẫn mở đầu:** Các câu xã giao như *"Chào bạn! Dưới đây là phần giải thích..."* làm mất thời gian cắt bỏ.
2. **Nội dung diễn giải lan man:** Do từ khóa "ngắn gọn" mang tính chủ quan, AI hay viết dài dòng hoặc đưa thêm các ví dụ minh họa không cần thiết.
3. **Lời kết xã giao:** Các câu như *"Hy vọng thông tin này hữu ích..."* gây nhiễu dữ liệu đầu ra khi cần dán nhanh vào tài liệu.

### Bước 2: Viết prompt tối ưu
> **Prompt tối ưu:**
> Giải thích định nghĩa và mục đích sử dụng của 3 kỹ thuật sau: Chain-of-Thought (CoT), Prompt Chaining, và Xử lý đứt gãy ngữ cảnh.
> 
> **Yêu cầu định dạng:**
> - Trình bày bằng danh sách gạch đầu dòng (bullet points), mỗi kỹ thuật tối đa 2 câu.
> - Đi thẳng vào nội dung chính ngay từ dòng đầu tiên.
> - **TUYỆT ĐỐI KHÔNG** viết lời chào, câu dẫn mở đầu, ví dụ minh họa hay lời kết xã giao.

### Bước 3: Kết quả phản hồi thực tế từ AI (Sạch chữ thừa)
* **Chain-of-Thought (CoT):** Kỹ thuật yêu cầu AI suy luận và trình bày từng bước trung gian trước khi đưa ra đáp án cuối cùng. Mục đích là giúp mô hình giải quyết chính xác các bài toán logic phức tạp và giảm thiểu ảo giác.
* **Prompt Chaining:** Kỹ thuật chia nhỏ một tác vụ lớn thành chuỗi các prompt nối tiếp nhau, trong đó đầu ra bước trước là đầu vào bước sau. Mục đích là kiểm soát chất lượng từng giai đoạn và xử lý luồng công việc hiệu quả.
* **Xử lý đứt gãy ngữ cảnh:** Kỹ thuật sử dụng câu lệnh điều hướng để duy trì mạch thông tin khi hội thoại quá dài hoặc bị ngắt quãng. Mục đích là đảm bảo tính nhất quán và ngăn AI quên các ràng buộc ban đầu.