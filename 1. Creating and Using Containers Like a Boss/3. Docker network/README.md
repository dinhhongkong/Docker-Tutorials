# Docker network
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


