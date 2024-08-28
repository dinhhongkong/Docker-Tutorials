# Quản lý container
Docker container là một đơn vị độc lập để chạy ứng dụng. Bạn có thể tạo, quản lý và theo dõi các container với các lệnh Docker dưới đây.
### `docker container run -d <image>` 
Lệnh này sẽ chạy một container mới trong chế độ nền (detached mode) từ một image được chỉ định. Container sẽ được chạy mà không cần kết nối với terminal, cho phép nó tiếp tục chạy ngay cả khi bạn đóng terminal.

### `docker container stop <container>`
Lệnh này sẽ dừng một container đang chạy. Bạn có thể xác định container bằng ID hoặc tên của nó. Lệnh này gửi tín hiệu SIGTERM tới container để yêu cầu nó dừng lại một cách an toàn.

### `docker start <container_id_or_name>`
Lệnh này để khởi động một container khi đã xác định được ID hoặc tên của container

### `docker container rm <container>`
Lệnh này sẽ xóa (remove) một container đã dừng. Điều này giúp bạn dọn dẹp các container không còn sử dụng nữa. Nếu container đang chạy, bạn cần phải dừng nó trước khi xóa.

### `docker container ls`
Lệnh này liệt kê tất cả các container đang chạy. Nó cung cấp thông tin về ID container, tên, trạng thái, và nhiều chi tiết khác. Nếu bạn chỉ muốn xem các container đang hoạt động, đây là lệnh bạn cần.

### `docker container ls -a`
Lệnh này liệt kê tất cả các container, bao gồm cả những container đã dừng. Điều này giúp bạn xem toàn bộ lịch sử container trên hệ thống của mình.

### `docker container top <container>`
Lệnh này hiển thị thông tin về các tiến trình đang chạy bên trong một container. Nó giống như lệnh `top` trong hệ điều hành Linux, nhưng dành cho một container cụ thể.

### `docker container inspect <container>`
Lệnh này hiển thị chi tiết cấu hình của một container dưới dạng JSON. Nó cung cấp rất nhiều thông tin chi tiết, bao gồm cả các biến môi trường, cổng mở, và các tùy chọn cấu hình khác của container.

### `docker container stats <container>`
Lệnh này hiển thị thống kê về hiệu suất của container, bao gồm CPU, bộ nhớ, I/O mạng và ổ đĩa. Điều này rất hữu ích để giám sát hoạt động và hiệu suất của container.
