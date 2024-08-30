## Docker Swarm

### Swarm là gì?
Docker Swarm là một công cụ điều phối (orchestration) của Docker, cho phép bạn quản lý và triển khai các container trên một cluster gồm nhiều máy chủ (nodes). Swarm biến nhiều Docker hosts thành một môi trường duy nhất, làm cho việc triển khai các dịch vụ (services) trở nên dễ dàng và có thể mở rộng (scale) hơn. Docker Swarm cũng cung cấp tính năng cân bằng tải (load balancing) tự động, đảm bảo các container hoạt động hiệu quả và ổn định.

### Các thành phần của Docker Swarm

1. **Node**:
   - **Manager Node**: Đây là node chịu trách nhiệm quản lý toàn bộ cluster Swarm. Manager node điều phối các dịch vụ, quản lý trạng thái của các worker node, và thực hiện các thay đổi cấu hình trên Swarm. Một Swarm có thể có nhiều manager nodes để đảm bảo tính dự phòng (high availability).
   - **Worker Node**: Worker nodes chịu trách nhiệm chạy các container của các dịch vụ. Worker nodes nhận các nhiệm vụ (tasks) từ manager node và thực thi chúng. Worker nodes không có quyền quản lý cluster.

2. **Service**:
   - Một service trong Docker Swarm là một định nghĩa về các container cần được triển khai, bao gồm số lượng replicas, image nào sẽ được sử dụng, cổng mạng cần mở, và các tham số khác. Docker Swarm sẽ tự động điều phối việc triển khai và quản lý các container dựa trên định nghĩa này.

3. **Task**:
   - Một task là một instance cụ thể của một container đang chạy như một phần của một service. Mỗi task được gán cho một worker node, và node đó chịu trách nhiệm thực thi task này. Nếu một node gặp sự cố, Docker Swarm sẽ tự động di chuyển các tasks sang các nodes khác để đảm bảo dịch vụ không bị gián đoạn.

4. **Overlay Network**:
   - Docker Swarm sử dụng overlay network để cho phép các containers trên các nodes khác nhau trong Swarm có thể giao tiếp với nhau một cách an toàn và hiệu quả. Overlay network kết nối các nodes trong một mạng ảo (virtual network) được quản lý bởi Docker.

5. **Ingress Load Balancer**:
   - Ingress load balancer là một tính năng của Docker Swarm giúp cân bằng tải giữa các replicas của một service. Nó tự động phân phối yêu cầu từ người dùng tới các container đang chạy trên các nodes khác nhau, đảm bảo tính cân bằng và tối ưu hóa tài nguyên.

6. **Swarm Manager Election**:
   - Trong một Swarm có nhiều manager nodes, Docker Swarm sử dụng một cơ chế bầu cử (election) để chọn ra một leader manager node. Nếu leader manager node hiện tại gặp sự cố, một manager node khác sẽ được bầu làm leader mới để đảm bảo Swarm tiếp tục hoạt động mà không bị gián đoạn.

### Khi nào nên sử dụng Docker Swarm?
Docker Swarm lý tưởng cho các tình huống mà bạn cần quản lý nhiều containers trên nhiều hosts, đặc biệt là khi bạn muốn triển khai các dịch vụ ở quy mô lớn và đảm bảo tính sẵn sàng cao. Swarm cung cấp một giải pháp nhẹ nhàng và dễ triển khai so với các công cụ điều phối phức tạp khác như Kubernetes.

## Các câu lệnh

### `docker swarm init`
Câu lệnh `docker swarm init` được sử dụng để khởi tạo một Docker Swarm, biến máy hiện tại trở thành node quản lý (manager node) của cluster Swarm. Sau khi khởi tạo, bạn sẽ nhận được một token để thêm các node khác (worker nodes) vào cluster. Swarm là một tính năng của Docker dùng để quản lý cluster các container, cho phép bạn triển khai các dịch vụ ở quy mô lớn.

### `docker node ls`
Câu lệnh `docker node ls` liệt kê tất cả các node hiện có trong cluster Swarm. Điều này bao gồm cả các node quản lý (manager nodes) và các node làm việc (worker nodes). Câu lệnh này chỉ có thể được thực hiện từ một node quản lý. Thông tin hiển thị bao gồm ID, hostname, vai trò (role), trạng thái (status), và trạng thái hiện tại của mỗi node.

### `docker service create`
Câu lệnh `docker service create` được sử dụng để tạo và triển khai một dịch vụ mới trong Docker Swarm. Bạn cần chỉ định image của container và các tham số khác như số lượng replicas, cổng mạng, và volume nếu cần thiết. Sau khi tạo, dịch vụ sẽ tự động quản lý các container dựa trên số lượng replicas mà bạn yêu cầu.

### `docker service update <id hoặc tên> --replicas <số>`
Câu lệnh `docker service update <id hoặc tên> --replicas <số>` dùng để cập nhật số lượng replicas (bản sao) của một dịch vụ đã tồn tại trong Docker Swarm. Bằng cách chỉ định số lượng replicas mới, Docker sẽ tự động scale dịch vụ lên hoặc xuống để đáp ứng đúng số lượng bạn đã chỉ định.

### `docker service ps <id hoặc tên>`
Câu lệnh `docker service ps <id hoặc tên>` hiển thị danh sách các container (tasks) đang chạy hoặc đã từng chạy cho một dịch vụ cụ thể trong Docker Swarm. Thông tin bao gồm ID của task, tên node, trạng thái, và thời gian khởi tạo. Câu lệnh này giúp bạn theo dõi trạng thái của các container liên quan đến một dịch vụ cụ thể.

### `docker service ps <id hoặc tên>`

