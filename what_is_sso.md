# SSO là gì?
Trong bản tin này, chúng ta sẽ nói về những điều sau:

- SSO là gì (Single Sign-On)?

- IaaS/PaaS/SaaS là gì?

## SSO là gì (Single Sign-On)?

Một người bạn gần đây đã trải qua trải nghiệm khó chịu khi bị đăng xuất ra một số trang web mà họ sử dụng hàng ngày. Đây là sự kiện quen thuộc với hàng triệu người dùng web, và nó là quy trình tẻ nhạt để khắc phục. Nó có thể liên quan đến việc cố nhớ những mật khẩu đã quên từ lâu, hoặc nhập tên của những có thú cưng thời thơ ấu để trả lời câu hỏi bảo mật. SSO xóa sự bất tiện này và làm cho cuộc sống online tốt hơn. Nhưng nó hoạt động thế nào?

Về cơ bản, Single Sing-On (SSO) là một sơ xác thực. Nó cho phép một user đăng nhập vào các hệ thống nhác nhau bằng một single ID.

Sơ đồ bên dưới minh họa cách hoạt động của SSO.

![alt text](./images/how-does-sso-work.jpg?raw=true "Cách hoạt động của SSO")

Step 1: Người dùng truy cập Gmail, hoặc bất cứ dịch vụ email. Gmail thấy rắng người chưa đăng nhập và do đó chuyển hướng họ đến máy chủ xác thực SSO, máy chủ này cũng nhận thấy người dùng chưa đăng nhâp. Vì vậy người dùng được chuyển hướng đến trang đăng nhập SSO, ở đây họ nhập thông tin đăng nhập của mình

Steps 2-3: Máy chủ xác thức SSO xác thực thông tin đăng nhập, tạo ra một phiên đăng nhập chung cho người dùng và tạo một token

Steps 4-7: Gmail xác thực token tại máy chủ xác thực SSO. Máy chủ xác thực đăng kí hệ thống gmail và trả kề hợp lệ, Gmail trả resource protected về cho người dùng

Step 8: Từ Gmail, người dùng điều hướng đến một trang web mà Google sở hữu, ví dụ YouTube

Steps 9-10: YouTube  thấy rằng người dùng chưa đăng nhập và sau đó yêu cầu xác thưc. Máy chủ xác thực SSO thấy người đã đăng nhập và trả về token

Steps 11-14: YouTube xác thực token trong máy chủ xác thực SSO. Máy chủ xác thực đăng kí hệ thống YouTube và trả về kết quả hợp lệ, YouTube trả resource protected về cho người dùng

Quá trình hoàn tất và người dùng lấy lại quyền truy cập vào tài khoản của họ.

Kế tiếp:

- Câu 1: Bạn có implemented SSO trong dự án của bạn không? Phần khó nhất là gì?

- Câu 2: Phương thức đăng nhập yêu thích của bạn là gì và tại sao?

## IaaS/PaaS/SaaS là gì?

![alt text](./images/what-is-iaas-paas-saas.jpg?raw=true "IaaS/PaaS/SaaS là gì")


Sơ đồ bên dưới minh họa sự khác biệt giữa IaaS (Infrastructure-as-a-Service), PaaS (Platform-as-a-Service), and SaaS (Software-as-a-Service).

Đối với ứng dụng non-cloud, chúng ta sở hứu và quản lý tất cả phần cứng và phần mềm. Chúng ta nói ứng dụng on-premises.

Với cloud computing, Các nhà cung cấp cloud service cung cấp ba loại mô hình cho chúng ta sử dụng: IaaS, PaaS, and SaaS.

IaaS nhà cấp cho chúng ta quyền truy cập vào cơ sở hạ tầng của nhà cung cấp cloud chẳng hặn như servers, storage, networking, Chúng ta trả tiền cho dịch vụ cơ sở hạ tầng và cài đặt, quản lý phần mềm hỗ trợ trên nó cho ứng dụng của chúng ta 

PaaS đi xa hơn. Nó cung cấp một nền tảng với nhiều middleware, frameworks và tools để xây dựng ứng dụng của chúng ta. Chúng ta chỉ tập trung vào phát triển ứng dụng và data.

SaaS cho phép ứng dụng chạy trên cloud. Chúng ta trả phí hàng tháng hoặc hàng năm để sử dụng sản phẩm SaaS.

Kế tiếp: Bạn đã sử dụng IaaS/PaaS/SaaS? Làm thế nào để bạn quyết định sử dụng kiến ​​trúc nào?