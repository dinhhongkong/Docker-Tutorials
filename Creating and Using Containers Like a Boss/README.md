## Quản lý container
Docker container là một đơn vị độc lập để chạy ứng dụng. Bạn có thể tạo, quản lý và theo dõi các container với các lệnh Docker dưới đây.
### `docker container run -d <image>` 
Lệnh này sẽ chạy một container mới trong chế độ nền (detached mode) từ một image được chỉ định. Container sẽ được chạy mà không cần kết nối với terminal, cho phép nó tiếp tục chạy ngay cả khi bạn đóng terminal.

### `docker container stop <container>`
Lệnh này sẽ dừng một container đang chạy. Bạn có thể xác định container bằng ID hoặc tên của nó. Lệnh này gửi tín hiệu SIGTERM tới container để yêu cầu nó dừng lại một cách an toàn.

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


## Shell inside container
Docker cho phép bạn tương tác với các container đang chạy như thể bạn đang làm việc trực tiếp trên một hệ điều hành khác. Dưới đây là các lệnh để mở shell bên trong container.

### `docker container run -it --name <name> <image> bash`

Lệnh này tạo và chạy một container mới từ image được chỉ định, đồng thời mở một phiên shell (`bash`) bên trong container. Các tham số:
- `-it`: Tham số này kết hợp hai tùy chọn: `-i` (interactive) giữ cho tiêu chuẩn đầu vào của container mở ngay cả khi không có kết nối, và `-t` (tty) tạo một terminal giả lập để bạn có thể tương tác.
- `--name <name>`: Tùy chọn này cho phép bạn đặt tên cho container. Điều này giúp bạn dễ dàng quản lý và truy cập container sau này.


### `docker container start -ai <container> `
Lệnh này khởi động lại một container đã dừng và kết nối lại với phiên shell của nó. Các tham số:
- `-a`: Kết nối với đầu vào và đầu ra của container (attach).
- `-i`: Giữ cho đầu vào của container mở, cho phép bạn tiếp tục tương tác với shell.

### `docker container exec -it <container> bash`
Lệnh này cho phép bạn mở một phiên shell mới bên trong một container đang chạy. Điều này rất hữu ích khi bạn muốn kiểm tra hoặc thực hiện các lệnh bên trong một container mà không cần khởi động lại nó. Các tham số:
- `-it`: Tạo một phiên làm việc tương tác với container, giống như trong lệnh `docker container run`.
- `<container>`: Tên hoặc ID của container mà bạn muốn truy cập.
- `bash`: Shell mà bạn muốn mở bên trong container. Bạn có thể thay `bash` bằng bất kỳ shell hoặc chương trình nào khác có sẵn bên trong container.

## Docker network
* Mỗi container kết nối tới một private virtual network gọi là "bridge". Và mặc định cũng là mạng "bridge".
* Mỗi virtual network được định tuyến qua NAT Firewall trên IP máy chủ (host ip)
* Tất cả các container trong virtual network có thể giao tiếp với nhau mà không cần cấu hình -p

### `docker container run -p`

### `docker container port <container>`

### `docker network ls`

### `docker network inspect <network>`

### `docker network create <driver>`

### `docker network connect`

### `docker network disconnect`



