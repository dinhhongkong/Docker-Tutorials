# Shell inside container
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