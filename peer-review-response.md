# Peer Review Response

## Thông tin nhóm
- Thành viên 1: Nguyễn Hữu Mạnh
- Thành viên 2: Bùi Anh Tuấn

## Thành viên 1 góp ý cho thành viên 2
Nguyễn Hữu Mạnh góp ý cho Bùi Anh Tuấn rằng phần Sender cần in log rõ hơn để dễ đối chiếu với Receiver, đặc biệt là thông tin gửi packet, độ dài ciphertext và thông báo gửi thành công. Ngoài ra, phần tài liệu cần tránh để sót placeholder và nên mô tả rõ hơn vai trò của key, IV và packet header.

## Thành viên 2 góp ý cho thành viên 1
Bùi Anh Tuấn góp ý cho Nguyễn Hữu Mạnh rằng phần Receiver cần kiểm tra kỹ việc đọc đúng số byte từ socket để tránh lỗi khi packet bị thiếu dữ liệu. Phần giải mã cũng cần xử lý lỗi rõ ràng hơn trong các trường hợp ciphertext bị chỉnh sửa hoặc dùng sai key.

## Nhóm đã sửa gì sau góp ý
Sau peer review, nhóm đã rà soát lại README.md để bổ sung đầy đủ thông tin hai thành viên, phân công công việc và vai trò demo. Nhóm cũng kiểm tra lại các file report-1page.md, threat-model-1page.md và peer-review-response.md để xóa toàn bộ placeholder. Ngoài ra, nhóm bổ sung/kiểm tra các test case quan trọng như tamper negative test và wrong key negative test, đồng thời lưu log chạy thật vào thư mục logs/ để làm minh chứng nộp bài.
