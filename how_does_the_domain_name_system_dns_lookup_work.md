# Domain Name System (DNS) lookup hoạt động như thế nào ?

`DNS dịch sang tiếng việt là *Hệ Thống Tên Miền* `

## Tổng quát
- DNS đóng vài trò như một cuốn danh bạ. Nó chuyển đổi tên miền mà con người (human-readable) có thể đọc (google.com) thành địa chỉ IP mà máy (machine-readable) có thể đọc được (142.251.46.238).

- Để đạt được khả năng mở rộng (scalability) tốt hơn, các máy chủ DNS được tổ chức theo cấu trúc cây phân cấp (hierarchical tree structure).

![alt text](./images/how-does-the-domain-name-system-dns-lookup-work.jpg?raw=true "Cách DNS xử lý IP")

## Có 3 cấp độ cơ bản của DNS servers
1. Root name server (.). Nó lưu trữ các địa chỉ IP của tên miền cấp cao nhất (Top Level Domain (TLD) name servers). Có 13 tên gốc máy chủ hợp lý trên toàn cầu

2. TLD name server. Nó lưu trữ địa chỉ IP của Authoritative Name Server . Có một số loại tên TLD. Ví dụ: TLD chung (generic) (.com, .org), TLD mã quốc gia (.us), TLD test (.test).

3. Authoritative name server. It provides actual answers to the DNS query. You can register authoritative name servers with domain name registrar such as GoDaddy, Namecheap, etc. 
3. Authoritative name server. Nó cung cấp các câu trả lời đến truy vấn DNS. Bạn có thể đăng kí Authoritative Name Server mới các nhà đăng kí tên miền chẳng hạn như là Mat Bao, PA Viet Nam, ...

*Authoritative Name Server: Là điểm dừng cuối cùng cho truy vấn DNS và có bản ghi DNS cho các truy vấn, yêu cầu*

## Sở đồ bên dưới minh họa cách DNS lookup hoạt động
1. Nhập google.com vào trình duyệt (browser), và trình duyệt gửi tên miền đến DNS resolver (bộ phân giải DNS)

2. DNS resolver truy vấn đến một DNS root name server

3. Máy chủ gốc phản hồi địa chỉ của một TLD DNS server đến DNS resolver. Trong trường hợp này, nó là .com

4. Sau đó DNS resolver tạo một yêu cầu đến .com TLD.

5. Máy chủ TLD phản hồi với địa chỉ IP của DNS, google.com (Authoritative Name Server)

6. DNS resolver gửi một câu truy vấn đến DNS.

7. Địa chỉ IP cho google.com được trả về cho DNS resolver từ nameserver.

8. DNS resolver phản hồi đến trình duyệt web với địa chỉ IP (142.251.46.238) của tên miền được yêu cầu ban đầu

DNS lookups trung bình mất từ khoảng 20-120 milliseconds để hoàn thành (theo YSlow).

Source: https://blog.bytebytego.com/p/how-does-the-domain-name-system-dns