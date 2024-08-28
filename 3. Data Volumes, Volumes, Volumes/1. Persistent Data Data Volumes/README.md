Trong Docker, data volumes (hay còn gọi là volumes) là một cơ chế được sử dụng để lưu trữ dữ liệu bền vững và tách biệt khỏi vòng đời của các container. Điều này có nghĩa là dữ liệu được lưu trữ trong volumes sẽ không bị mất khi container bị xóa hoặc khi container được khởi động lại.

Một số đặc điểm của data volumes trong Docker:
- Tính bền vững: Dữ liệu được lưu trữ trong volumes sẽ tồn tại độc lập với container, giúp bảo toàn dữ liệu ngay cả khi container bị xóa.

- Chia sẻ dữ liệu giữa các container: Các container có thể chia sẻ cùng một volume, cho phép chúng truy cập và cập nhật cùng một tập dữ liệu.

- Quản lý dễ dàng: Volumes có thể được tạo, gán, và quản lý thông qua các lệnh Docker, và cũng có thể được lưu trữ trên các ổ đĩa cục bộ hoặc trên các dịch vụ lưu trữ từ xa.

- Hiệu suất: Docker volumes thường cung cấp hiệu suất tốt hơn so với việc lưu trữ dữ liệu trong hệ thống tệp của container.

### `docker run -v my_named_volume:/path/in/container my_image`

Lệnh này được dùng Khi khởi tạo một container, lúc này có thể tạo và gắn một volume

Trong đó:

- /my/volume là đường dẫn của volume trên máy chủ (host).
- /data là đường dẫn trong container nơi dữ liệu sẽ được lưu trữ.