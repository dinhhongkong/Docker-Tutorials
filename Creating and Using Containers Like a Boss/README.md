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

### `docker container run -p <host_port>:<container_port> <image>`
Lệnh này chạy một container mới và ánh xạ (mapping) cổng từ máy chủ (host) sang container. Các tham số:
- `-p <host_port>:<container_port>`: Tham số này ánh xạ cổng của máy chủ (`host_port`) đến một cổng tương ứng trong container (`container_port`). Điều này cho phép bạn truy cập dịch vụ chạy bên trong container thông qua máy chủ của bạn.
- `<image>`: Image mà bạn muốn chạy. 

Ví dụ: `docker container run -p 8080:80 nginx` sẽ chạy một container từ image `nginx` và ánh xạ cổng 8080 của máy chủ đến cổng 80 của container.

### `docker container port <container>`
Lệnh này hiển thị danh sách các cổng đang được ánh xạ từ container đến máy chủ. Điều này rất hữu ích khi bạn muốn kiểm tra xem cổng nào của container đã được ánh xạ ra bên ngoài.

Ví dụ: `docker container port my_container` sẽ hiển thị các cổng đang được ánh xạ cho container có tên là `my_container`.

### `docker network ls`
Lệnh này liệt kê tất cả các mạng hiện có trong Docker. Docker tự động tạo một số mạng mặc định (như `bridge`, `none`, và `host`), nhưng bạn cũng có thể tạo thêm các mạng tùy chỉnh. Lệnh này giúp bạn xem danh sách các mạng đó.

### `docker network inspect <network>`
Lệnh này hiển thị thông tin chi tiết về một mạng cụ thể dưới dạng JSON. Thông tin bao gồm các container đang kết nối với mạng, cấu hình của mạng, và các tùy chọn khác.

Ví dụ: `docker network inspect bridge` sẽ hiển thị chi tiết về mạng `bridge` mặc định.

### `docker network create <driver> <network_name>`
Lệnh này tạo một mạng mới trong Docker với loại driver được chỉ định. Các tham số:
- `<driver>`: Loại driver cho mạng (ví dụ: `bridge`, `overlay`). `bridge` là driver mặc định.
- `<network_name>`: Tên của mạng mà bạn muốn tạo.

Ví dụ: `docker network create bridge my_network` sẽ tạo một mạng `bridge` với tên là `my_network`.

### `docker network connect <network> <container>`
Lệnh này kết nối một container đang chạy vào một mạng Docker cụ thể. Điều này cho phép container giao tiếp với các container khác trong cùng một mạng.

Ví dụ: `docker network connect my_network my_container` sẽ kết nối `my_container` vào mạng `my_network`.

### `docker network disconnect <network> <container>`
Lệnh này ngắt kết nối một container khỏi một mạng Docker cụ thể. Container sau đó sẽ không thể giao tiếp với các container khác trên mạng đó.

Ví dụ: `docker network disconnect my_network my_container` sẽ ngắt kết nối `my_container` khỏi mạng `my_network`.


