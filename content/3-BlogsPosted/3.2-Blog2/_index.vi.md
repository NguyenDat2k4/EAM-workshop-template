---
title: "Kiến trúc Amazon EKS Auto Mode và Istio Ambient Mesh"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---


Xin chào mọi người AWS Study Group VN! Trong quá trình tìm hiểu về Kubernetes, mình phát hiện có bài viết AWS giới thiệu cách kết hợp Amazon EKS Auto Mode và Istio Ambient Mesh. Hai công nghệ này “hợp sức” giúp giảm đáng kể operational overhead trong khi vẫn tăng cường bảo mật service-to-service một cách tự động.

Khi hệ thống microservices phát triển từ vài services lên hàng trăm services, hai vấn đề lớn xuất hiện: quản lý infrastructure (node provisioning, patching, scaling) và bảo mật giao tiếp giữa các services. EKS Auto Mode + Istio Ambient Mesh chính là giải pháp “Better Together” để giải quyết cả hai vấn đề này.

### 1. Amazon EKS Auto Mode
Đây là chế độ tự động hóa mạnh mẽ của EKS, giúp AWS quản lý gần như toàn bộ compute layer:
* Tự động provisioning, scaling, patching node bằng Karpenter (phiên bản tùy chỉnh).
* Sử dụng hệ điều hành Bottlerocket – minimal, immutable, bảo mật cao.
* Các thành phần hệ thống (VPC CNI, kube-proxy, EBS CSI, CoreDNS, Load Balancer Controller…) được AWS quản lý như system process, không cần deploy add-on thủ công.
* Loại bỏ nhu cầu SSH vào node, giảm bề mặt tấn công.

### 2. Istio Ambient Mesh
Đây là kiến trúc sidecarless của Istio, giúp áp dụng service mesh mà không cần inject sidecar proxy vào từng pod:
* **ztunnel (per-node proxy):** Xử lý Layer 3/4 – tự động mTLS, L4 authorization, TCP telemetry.
* **Istio-cni:** Chained CNI plugin để redirect traffic qua ztunnel.
* **Waypoint Proxy (tùy chọn):** Xử lý Layer 7 (HTTP routing, retries, L7 authorization, circuit breaking…) khi cần.

![EKS Auto Mode + Istio Ambient Mesh](/images/3-BlogsPosted/eks_auto_mode_istio_ambient.png)

### Kết luận:
Sự kết hợp giữa Amazon EKS Auto Mode và Istio Ambient Mesh mang lại một Kubernetes environment hiện đại: tự động hóa mạnh ở tầng compute và bảo mật linh hoạt ở tầng service mesh mà không làm phức tạp hóa ứng dụng. Đây là hướng đi rất đáng cân nhắc cho các team đang xây dựng nền tảng microservices trên AWS.

**Nguồn tham khảo:**
<https://aws.amazon.com/blogs/containers/better-together-amazon-eks-auto-mode-and-istio-ambient-mesh/>

---

### Minh chứng đã đăng
- **Đường dẫn bài viết Facebook:** <https://www.facebook.com/groups/awsstudygroupfcj/permalink/2193364788095148/>

![AWS Study Group VN Post](/images/3-BlogsPosted/blog2_facebook_post.png)