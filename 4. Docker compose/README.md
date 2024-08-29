### `docker compose up`
Câu lệnh `docker compose up` sẽ khởi động tất cả các container được định nghĩa trong file `docker-compose.yml`. Nếu chưa có container nào tồn tại, Docker sẽ tạo mới container từ các image được chỉ định. Khi sử dụng lệnh này, các log từ các container sẽ được hiển thị trực tiếp trên terminal. Nếu muốn dừng các container này, bạn chỉ cần nhấn `Ctrl + C`.

### `docker compose up -d`

Câu lệnh `docker compose up -d` tương tự như `docker compose up`, nhưng với tham số `-d` (detached mode), các container sẽ được khởi động dưới nền. Điều này có nghĩa là sau khi các container được khởi động, terminal sẽ trở về trạng thái sẵn sàng để bạn thực hiện các câu lệnh khác mà không cần phải mở một cửa sổ terminal khác. Để kiểm tra trạng thái các container, bạn có thể sử dụng lệnh `docker compose ps`.

### `docker compose down`
Câu lệnh `docker compose down` sẽ dừng và xóa tất cả các container, network, và các volumes được tạo ra bởi `docker compose up`. Lệnh này hữu ích khi bạn muốn dừng toàn bộ các container liên quan và xóa bỏ mọi thứ để khởi động lại từ đầu với một trạng thái mới. Bạn có thể sử dụng thêm các tùy chọn như `--volumes` để xóa luôn cả các volumes liên quan.
