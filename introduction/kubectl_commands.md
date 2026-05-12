# Common `kubectl` Commands
## 1. Namespaces
**Namespaces** là cơ chế dùng để chia logical cluster thành nhiều không gian riêng biệt. Giúp tổ chức resource, tránh conflict, phân quyền, quản lý dễ dàng. Có thể tưởng tượng Namespace giống như folder trong filesystem.
```
Cluster
 ├── namespace: dev
 │      ├── Pod A
 │      ├── Service A
 │      └── Deployment A
 │
 └── namespace: prod
        ├── Pod B
        ├── Service B
        └── Deployment B
```
Mặc định khi chạy
```bash
kubectl get pods
```
thì Kubernetes mặc định tìm trong namespace `default`. Để tìm trong namespace khác thì cần thêm flag `--namespace=<namespace_name>`
```bash
kubectl --namespace=mystuff get pods
```
## 2. Viewing Kubernetes API Objects
Trong **Kubernetes**, mọi thứ (Pod, Deployment, Namespace,...) đều là API Objects và được truy cập thông qua REST API. Mỗi object sẽ có URL riêng. 
`kubectl` thực chất không quản lý cluster trực tiếp mà là một HTTP client, thực hiện HTTP request xuống `kube-apiserver`.
```bash
kubectl get pods
kubectl get services
kubectl get deployments
kubectl get pods my-pod
```
## 3. Creating, Updating and Destroying Kubernetes Objects
Có thể sử dụng YAML hoặc JSON files để tạo, update hoặc delete object trên Kubernetes. 
Giả sử có simple object lưu trong `obj.yaml`, sử dụng lệnh sau để tạo object trên Kubernetes:
```bash
kubectl apply -f obj.yaml
```
`apply` sẽ so sánh trạng thái hiện tại trong cluster với trạng thái trong file YAML, nếu khác nhau sẽ update object, nếu giống hệt sẽ không làm gì cả.
Nếu muốn xoá object, sử dụng lệnh sau:
```
kubectl delete -f obj.yaml
kubectl delete <resource-name> <obj-name>
```