_# Threat Model - Lab 3

## Thông tin nhóm
- Thành viên 1: Nguyễn Hữu Mạnh
- Thành viên 2: Bùi Anh Tuấn

## Assets
Plaintext: Nội dung tin nhắn gốc cần bảo mật.

DES Key: Khóa đối xứng dùng để mã hóa/giải mã.

Tính toàn vẹn: Sự nguyên vẹn của dữ liệu trên đường truyền.

## Attacker model

Đối tượng: Kẻ tấn công trung gian (Man-in-the-Middle - MitM) nằm trong cùng mạng nội bộ hoặc có quyền truy cập vào các nút mạng giữa Sender và Receiver.

Khả năng: - Có thể nghe lén (Sniffing) toàn bộ lưu lượng TCP thô.

Có thể can thiệp, chỉnh sửa hoặc giả mạo gói tin (Tampering) trước khi nó tới đích.

## Threats
Lộ lọt thông tin: Key/IV gửi công khai trong Header khiến kẻ tấn công dễ dàng giải mã bản tin.

Giả mạo dữ liệu: Thiếu cơ chế kiểm tra tính toàn vẹn (HMAC) khiến bản tin có thể bị sửa đổi mà không bị phát hiện.

Tấn công phát lại (Replay): Kẻ tấn công gửi lại gói tin hợp lệ cũ để gây nhiễu hệ thống.
## Mitigations
Trao đổi khóa an toàn: Sử dụng Diffie-Hellman hoặc mã hóa bất đối xứng để bảo vệ khóa.

Xác thực thông điệp: Thêm mã HMAC để đảm bảo dữ liệu không bị chỉnh sửa.

Mã hóa lớp vận chuyển: Triển khai TLS/SSL để bảo mật toàn bộ luồng dữ liệu TCP.
## Residual risks
Điểm yếu của DES: Độ dài khóa 56-bit quá ngắn, có thể bị phá vỡ bằng tấn công vét cạn (Brute-force) với phần cứng hiện đại. Nên nâng cấp lên AES-256.
