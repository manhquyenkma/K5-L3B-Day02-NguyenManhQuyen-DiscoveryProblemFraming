# Bộ 10 cặp Eval mẫu cho bước AI đối chiếu tài liệu (CP6 — Bonus B3)

Bộ test này dùng để chấm đầu ra của công cụ AI (ví dụ NotebookLM hoặc prompt bám nguồn) ở **Bước 2** trong quy trình tương lai, dựa trên 4 tiêu chí đánh giá ở mục 7 của [group_report.md](../team/group_report.md):

1. **Đúng nguồn & số trang:** Có tên file và đúng số trang/slide chứa thông tin.
2. **Không bịa ngoài tài liệu:** Không tự suy ra số liệu/kết luận không nằm trong tài liệu; nếu thiếu thì báo `"Không tìm thấy trong nguồn"`.
3. **Giữ đúng thuật ngữ & điều kiện:** Giữ thuật ngữ gốc và không lược bỏ điều kiện giới hạn (phạm vi, cỡ mẫu, giả định).
4. **Cấu trúc đối chiếu rõ ràng:** Trình bày dạng bảng/ý ngắn gọn, kiểm lại được trong 2–3 phút.

| # | Input (Ngữ cảnh tài liệu + câu hỏi kiểm thử) | Đầu ra mong đợi (Đạt) | Dấu hiệu Không đạt (Fail) | Tiêu chí kiểm chính |
|---:|---|---|---|---|
| 1 | 3 PDF bài giảng về xác thực/an toàn hệ thống; hỏi: *"Tóm tắt 3 cơ chế phòng chống chính và ghi rõ nằm ở file nào, trang nào"* | Liệt kê đúng 3 cơ chế có trong PDF, mỗi dòng ghi rõ `[TenFile.pdf, tr. X]` | Gộp 3 cơ chế nhưng thiếu tên file/số trang hoặc ghi nhầm số trang | #1, #4 |
| 2 | 2 tài liệu mô tả 2 thuật toán khác nhau (File A trang 12 ghi độ phức tạp `O(n log n)`, File B trang 8 ghi `O(n^2)`); hỏi bảng so sánh | Bảng tách rõ File A tr. 12 và File B tr. 8, nêu đúng độ phức tạp từng thuật toán | Nhầm lẫn số liệu giữa 2 file hoặc làm mượt thành kết luận chung chung không nêu độ phức tạp | #1, #3 |
| 3 | Tài liệu A chỉ nói về kiến trúc hệ thống, **không** có benchmark thời gian chạy; hỏi: *"So sánh latency trung bình giữa phương án A và B"* | Trả lời rõ: *"Tài liệu A không đề cập số liệu latency; chỉ có thông tin tại [FileB.pdf, tr. Y] nếu có"* | Tự lấy số liệu phổ biến bên ngoài hoặc tự ước lượng latency để điền cho đủ bảng | #2 |
| 4 | Đoạn tiếng Anh có thuật ngữ gốc *"Zero Trust Architecture"* và *"Least Privilege"*; hỏi tóm tắt bằng tiếng Việt | Giữ nguyên thuật ngữ `"Zero Trust Architecture"`, `"Least Privilege"` kèm giải thích ngắn tiếng Việt và `[File.pdf, tr. X]` | Dịch tự do làm mất thuật ngữ gốc (ví dụ dịch thành "kiến trúc không tin ai" mà bỏ tên chuẩn) | #3 |
| 5 | Kết quả thử nghiệm ở File A tr. 19 ghi *"đạt độ chính xác 94% trên tập 200 mẫu sạch, chưa thử trên dữ liệu nhiễu"* | Nêu rõ 94% đi kèm điều kiện *"trên 200 mẫu sạch, chưa kiểm trên dữ liệu nhiễu [FileA.pdf, tr. 19]"* | Chỉ ghi ngắn *"phương án A đạt 94%"* và bỏ mất điều kiện phạm vi mẫu | #3 |
| 6 | File B là bản PDF scan ảnh mờ không trích được chữ ở trang 10–15; hỏi nội dung trang 12 | Báo rõ không đọc/trích xuất được nội dung trang 12 để sinh viên tự mở PDF đọc | Tự đoán nội dung trang 12 dựa vào tiêu đề mục lục hoặc kiến thức nền | #2 |
| 7 | Hai tài liệu nêu quan điểm trái ngược nhau về chi phí triển khai (File A ủng hộ triển khai on-premise, File B ưu tiên cloud); hỏi điểm khác biệt | Trình bày đủ cả 2 luồng quan điểm kèm lý do và `[File, tr.]` tương ứng để sinh viên tự đánh giá | Tự chọn 1 bên là "tối ưu hơn" hoặc làm mờ sự mâu thuẫn giữa hai nguồn | #2, #4 |
| 8 | Nạp 4 tài liệu dài 35 trang mỗi file; yêu cầu xuất bảng đối chiếu cho 1 slide thuyết trình | Bảng gồm 4–6 hàng cô đọng (Chủ đề · Nguồn & Trang · Luận điểm · Điều kiện), đọc rà trong < 3 phút | Xuất đoạn văn dài trên 800 chữ không tách bảng, khiến người học mất thêm thời gian lọc lại | #4 |
| 9 | Đề bài hỏi một khái niệm nằm ở **ngoài** 3 tài liệu đã nạp (ví dụ hỏi so sánh thêm công cụ thứ 3 không có trong file) | Thông báo rõ công cụ thứ 3 không xuất hiện trong bộ tài liệu đã cung cấp | Tự tra kiến thức chung rồi chèn vào chung bảng đối chiếu mà không phân biệt nguồn | #2 |
| 10 | Bảng số liệu ở File C trang 24 có đơn vị là `ms` (mili-giây) và ngưỡng cảnh báo `< 250 ms` | Giữ chính xác giá trị `250`, đơn vị `ms` và dấu so sánh `<` kèm `[FileC.pdf, tr. 24]` | Đổi nhầm đơn vị thành `s`, làm tròn hoặc đảo nhầm điều kiện ngưỡng | #1, #3 |

