# Kubernetes Service
## 1. Cơ chế mạng nội bộ (Pod-to-Pod)







# 2. Services
- **ClusterIP** dùng khi các pod trong cluster cần giao tiếp với nhau
- **NodePort** mở pod cho các node được chỉ định, dùng khi các dịch vụ ngoài internet/ngoài cluster muốn truy cập vào các pod trong cluster. Truy cập thông qua `<Node_IP>:<Port>`.
- **LoadBalancer** che giấu địa chỉ IP nội bộ của Pod, thay vào đó expose domain để truy cập vào Pod.
# 3. Ingress Controller & API Gateway
## 3.1 Vấn đề nếu chỉ dùng LoadBalancer
Mỗi **Service** phải sử dụng 1 LoadBalancer gây ra tốn kém chi phí

# 4. Container Network Interface
**Container Network Interface (CNI)** có các tác dụng:
- Routing giữa các node trong cluster
- Cấp phát IP cho Pod khi được tạo
- Đảm bảo Pod-to-Pod communication
- Đảm bảo Pod-to-Node communication

# 5. Storage
Pod chỉ quan tâm có PVC hay không
Xoá Pod thì PVC và PC không mất
Xoá PVC thì PC mất