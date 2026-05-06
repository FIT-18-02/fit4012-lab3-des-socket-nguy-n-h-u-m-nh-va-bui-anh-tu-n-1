# Report 1 page - Lab 3

## Thông tin nhóm
- Thành viên 1: Nguyễn Hữu Mạnh
- Thành viên 2: TODO_STUDENT 2

## Mục tiêu
Mục tiêu của bài lab là xây dựng và hiểu rõ quy trình giao tiếp giữa hai thực thể Sender và Receiver qua giao thức TCP Socket trong môi trường mạng. Qua đó, sinh viên nắm vững cách áp dụng thuật toán mã hóa đối xứng DES ở chế độ CBC, cơ chế Padding PKCS#7 và cách đóng gói dữ liệu (Packet Header) để truyền tải thông tin an toàn. Bài lab cũng nhằm giúp sinh viên làm quen với việc đánh giá các lỗ hổng bảo mật thông qua mô hình Threat Model và thực thi kiểm thử phần mềm tự động.

## Phân công thực hiện
Nguyễn Hữu Mạnh: Phụ trách xây dựng logic lõi trong des_socket_utils.py (Mã hóa, giải mã, PKCS#7) và triển khai tiến trình sender.py.

Thành viên 2 ([Tên bạn đồng hành]): Phụ trách triển khai receiver.py, thiết lập hệ thống kiểm thử tự động trong thư mục tests/ và thu thập minh chứng tại logs/.

Làm chung: Thiết lập cấu trúc gói tin (Packet structure), xây dựng tài liệu threat-model-1page.md và thực hiện Peer-review.
## Cách làm
Sender: Sử dụng thư viện Crypto.Random để tạo Key và IV 8-byte ngẫu nhiên. Sau đó, bản tin được mã hóa bằng DES-CBC, đóng gói cùng Header (chứa Key, IV, độ dài ciphertext) và gửi qua TCP Socket.

Receiver: Thiết lập một Server Socket lắng nghe kết nối. Khi nhận dữ liệu, Receiver bóc tách Header dựa trên độ dài cố định, sau đó sử dụng đúng Key và IV nhận được để giải mã bản tin gốc.

Mã hóa DES-CBC: Sử dụng thư viện pycryptodome, đảm bảo dữ liệu luôn được Pad theo chuẩn PKCS#7 trước khi mã hóa để phù hợp với kích thước khối 64-bit của DES.

Kiểm thử: Sử dụng pytest để thực hiện các ca kiểm thử đơn vị (Unit test) và kiểm thử tích hợp, bao gồm cả các kịch bản tiêu cực (nhập sai khóa, sửa đổi bản mã).
## Kết quả
Kết nối: Hệ thống chạy ổn định trên môi trường local và giữa các máy trong mạng nội bộ.

Log minh chứng: Các file trong thư mục logs/ đã ghi nhận đầy đủ quá trình Sender tạo Key/IV và Receiver giải mã thành công bản tin "Xin chao FIT4012".

Ca kiểm thử quan trọng: Hoàn thành tốt ca kiểm thử Tamper Negative Test, chứng minh rằng nếu bản mã bị thay đổi dù chỉ 1 byte trên đường truyền, quá trình giải mã sẽ thất bại hoặc cho ra kết quả sai lệch hoàn toàn.
## Kết luận
Bài học kỹ thuật: Hiểu rõ tầm quan trọng của việc xử lý dữ liệu nhị phân qua Socket và cách quản lý trạng thái kết nối TCP. Nắm vững cơ chế hoạt động của chế độ CBC và vai trò của IV trong việc chống lại tấn công phân tích mẫu.

Bài học bảo mật: Nhận diện được lỗ hổng chết người khi truyền khóa (Key) trực tiếp trên cùng kênh tin với dữ liệu. Bài học rút ra là trong thực tế cần sử dụng các giao thức trao đổi khóa an toàn như Diffie-Hellman hoặc bọc toàn bộ ứng dụng trong lớp bảo mật TLS/SSL để đảm bảo an toàn thông tin.