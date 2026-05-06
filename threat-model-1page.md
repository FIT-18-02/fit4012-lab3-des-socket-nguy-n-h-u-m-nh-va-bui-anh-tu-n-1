_# Threat Model - Lab 3

## Thông tin nhóm
- Thành viên 1: TODO_STUDENT
- Thành viên 2: TODO_STUDENT

## Assets
Nguyễn Hữu Mạnh: 

Dữ liệu bản rõ (Plaintext): Nội dung tin nhắn gốc mà Sender muốn gửi tới Receiver.

Khóa DES (Symmetric Key): Khóa dùng để mã hóa và giải mã dữ liệu.

Tính toàn vẹn của gói tin: Đảm bảo dữ liệu không bị thay đổi trên đường truyền.

## Attacker model
Nguyễn Hữu Mạnh: 

Đối tượng: Kẻ tấn công trung gian (Man-in-the-Middle - MitM) nằm trong cùng mạng nội bộ hoặc có quyền truy cập vào các nút mạng giữa Sender và Receiver.

Khả năng: - Có thể nghe lén (Sniffing) toàn bộ lưu lượng TCP thô.

Có thể can thiệp, chỉnh sửa hoặc giả mạo gói tin (Tampering) trước khi nó tới đích.

## Threats
Nguyễn Hữu Mạnh : 

Lộ lọt khóa và dữ liệu (Information Leakage): Do hệ thống gửi trực tiếp Key và IV dưới dạng không mã hóa ngay trong Header của gói tin TCP, kẻ tấn công chỉ cần bắt gói tin là có thể giải mã được toàn bộ nội dung.

Tấn công thay đổi dữ liệu (Message Tampering): Vì hệ thống không có cơ chế kiểm tra tính toàn vẹn (như HMAC hay Digital Signature), kẻ tấn công có thể thay đổi một vài byte trong ciphertext, khiến Receiver giải mã ra nội dung sai lệch mà không hề hay biết.

Tấn công phát lại (Replay Attack): Kẻ tấn công bắt gói tin hợp lệ và gửi lại nhiều lần cho Receiver, gây nhiễu hoặc khiến hệ thống thực hiện lại các lệnh cũ.

## Mitigations
TODO_STUDENT: Nêu ít nhất 3 biện pháp giảm thiểu tương ứng.

## Residual risks
TODO_STUDENT: Nêu ít nhất 1 rủi ro còn lại._
