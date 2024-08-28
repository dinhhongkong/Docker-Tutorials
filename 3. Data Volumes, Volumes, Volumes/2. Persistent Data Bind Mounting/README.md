Data bind mounting trong Docker là một phương pháp gắn kết thư mục hoặc tệp từ hệ thống tệp của máy chủ (host) vào bên trong một container. Điều này cho phép container có thể truy cập và sử dụng dữ liệu từ hệ thống tệp của máy chủ, cũng như giúp chia sẻ dữ liệu giữa host và container dễ dàng hơn.

## Đặc điểm của bind mount:
- **Kết nối trực tiếp với hệ thống tệp của máy chủ:**
Bind mount gắn kết một thư mục hoặc tệp từ hệ thống tệp của host vào một đường dẫn cụ thể bên trong container. Điều này có nghĩa là mọi thay đổi được thực hiện trong thư mục hoặc tệp này trên host sẽ ngay lập tức phản ánh trong container, và ngược lại.

- **Tính linh hoạt:** Bind mount cho phép bạn gắn kết bất kỳ thư mục hoặc tệp nào từ host vào container. Bạn có thể sử dụng bind mount để truy cập các tệp cấu hình, dữ liệu đầu vào, hoặc bất kỳ dữ liệu nào khác mà container cần từ hệ thống host.

- **Tác động trực tiếp:** Không giống như volumes (các volumes của Docker được quản lý hoàn toàn bởi Docker), bind mount cho phép container tương tác trực tiếp với hệ thống tệp của host, điều này có thể dẫn đến các vấn đề bảo mật nếu không được quản lý cẩn thận.