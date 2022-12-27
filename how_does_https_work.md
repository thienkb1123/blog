# How does HTTPS work?

Trong bản tin này, chúng ta sẽ nói về những điều sau:
- Cách HTTPS hoạt động

- Cách lưu trữ mật khẩu một cách an toàn trong database và cách xác thực mật khẩu

## Cách hoạt động của HTTPS?

- Hypertext Transfer Protocol Secure (HTTPS) là một phần mở rộng của Hypertext Transfer Protocol (HTTP). HTTPS truyền dữ liệu đã mã hóa sử dụng Transport Layer Security (TLS). Nếu dữ liệu bị hacked thì hacker chỉ lấy được dữ liệu ở dạng binary code.


![alt text](./images/how-does-https-work.png?raw=true "Cách hoạt động HTTPS")

## Dữ liệu được mã hóa và giải mã như thế nào ?

- Step 1 - Client (browser) và server thiết lập một TCP connection

- Step 2 - Client gửi một "client hello" đến server. Message chứa tập hợp các thuật toán mã hóa cần thiết (cipher suites) và phiên bản TLS mới nhất nó có thể hỗ trợ. Server phản hồi với "server hello" để browser biết liệu rằng nó có thể hỗ trợ các thuật toán và phiên bản TLS

*Sau đó server gửi chứng nhận SSL đến clients. Chứng nhận chứa public key, hostname. expiry dates ... Client xác thực chứng nhận*

- Step 3 Sau khi xác thức chứng nhận SSL, client tạo một session key và mã hóa nó bằng public key. Máy chủ nhận session key được mã hóa và giải mã nó bằng private key

- Step 4- Bây giờ thì cả client và server đều giữ session key giống nhau (symmetric encryption). Dữ liệu đã mã hóa truyền trong một kênh hai chiều an toàn (a secure bi-directional channel)

*Tại sao HTTPS chuyển đổi đến symmetric encryption trong suốt quá trình truyền dữ liệu. Có hai lý do chính *

1. Security: Asymmetric encryption chỉ đi một chiều. Có nghĩa là nếu server cố gửi dữ liệu được mã hóa về cho client, bất kì ai cũng có thể giải mã dữ liệu việc sử dụng public key

2. Server resources: Asymmetric encryption thêm quá nhiều tính toán không hữu ích. Nó không phù hợp cho việc truyền dữ liệu trong một phiên dài

## Cách lưu mật khẩu an toàn trong database và cách xác thực mật khẩu?

Hãy cùng xem.

![alt text](./images/how-to-store-passwords-db.png?raw=true "How to store passwords safely in the database")

Things Not to do
Những điều không nên làm

- Lưu mật khẩu bằng văn bản thô thì nó không phải là một ý tưởng hay bởi vì bất cứ ai với truy cập nội bộ đều có thể thấy chúng

- Lưu mật bằng cách hash trực tiếp là không đủ bởi vì nó bị lược bỏ đối với các cuộc tấn công được tính toán trước. Như là raindow tables.

- Để giảm thiểu các cuộc tấn công được tính toán trước. Chúng ta salt mật khẩu

Salt là gì

Theo hướng dẫn OWASP "a salt là một chuỗi duy nhất, được tạo ngẫu nhiên để thêm vào mỗi mật khẩu như là một phần của quá trình hash"

Cách lưu trữ mật khẩu và salt?

1. Salt không có ý nghĩa là secret và nó có thể được lưu bằng văn bản thô trong database. Nó được dùng để đảm bảo kết quả hash của mỗi mật khẩu là duy nhất

2. Mật khẩu có thể được lưu trong database bằng sử dụng định dạng: hash(password + salt)

Làm thế nào để kiểm tra mật khẩu

Để xác thực mật khẩu, có thể theo quy trình sau:

1. Client nhập mật khẩu

2. System lấy satl tương ừng từ database.

3. System nối thêm salt đến mật khẩu và hash nó. Hãy gọi giá trị được hash là H1.

4. System so sánh H1 và H2, nơi H2 là hash được lưu trữ trong database, Nếu chúng giống nhau thì mật khẩu hợp lệ

Source: https://blog.bytebytego.com/p/how-does-https-work-episode-6