

### `docker build -t <tag name>` hoặc `docker image build -t <tag name>` 

Dùng để xây dựng một image từ một Dockerfile và gán cho nó một tag. Hãy xem chi tiết:

- docker build .: Xây dựng image từ Dockerfile trong thư mục hiện tại. Image sẽ không có tên, nhưng bạn sẽ nhận được ID của image.

- docker build -t my-username/my-image: Xây dựng image từ Dockerfile và gán cho nó tag my-username/my-image. Bạn có thể thay đổi my-username và my-image thành tên của bạn và tên image mong muốn.