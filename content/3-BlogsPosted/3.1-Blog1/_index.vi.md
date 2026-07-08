---
title: "Amazon EKS hỗ trợ định tuyến Egress qua VPC"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

Xin chào mọi người AWS Study Group VN! Trong quá trình tìm hiểu về Containers trên AWS, mình phát hiện ra Amazon EKS chính thức hỗ trợ **Customer-routed control plane egress**. Đây là tính năng giúp route lưu lượng outbound của Kubernetes Control Plane đi qua VPC của chính mình thay vì đi qua đường truyền mặc định do EKS quản lý.

Trước đây, khi Kubernetes API Server gọi ra ngoài (ví dụ: gọi Admission Webhook, truy vấn OIDC Identity Provider, hay gọi Aggregate API Server), toàn bộ lưu lượng này sẽ đi qua EKS-managed path. Ở các tổ chức trong lĩnh vực tài chính, y tế, chính phủ hoặc môi trường regulated rất khó áp dụng chính sách bảo mật, firewall, VPC routing và logging thống nhất.

Với **Customer-routed control plane egress**, AWS cho phép đưa phần traffic “customer-controllable” này ra ngoài qua Elastic Network Interface (ENI) nằm ngay trong VPC. Từ đó có thể:
* Áp dụng Security Groups để kiểm soát lưu lượng.
* Định tuyến qua AWS Network Firewall.
* Sử dụng VPC Endpoints hoặc PrivateLink.
* Theo dõi bằng VPC Flow Logs.
* Kết nối hệ thống on-premises thông qua AWS Direct Connect.

![EKS Control Plane Egress](/images/3-BlogsPosted/eks_control_plane_egress.png)

### Kết luận:
Tính năng Customer-routed control plane egress là một bước tiến lớn giúp EKS phù hợp hơn với các doanh nghiệp yêu cầu bảo mật nghiêm ngặt. Giờ đây, bạn có thể áp dụng chính sách mạng thống nhất cho cả Data Plane lẫn Control Plane. Đây là kiến thức rất giá trị cho những ai đang làm về Kubernetes và Security trên AWS.

**Nguồn tham khảo:**
<https://aws.amazon.com/blogs/containers/amazon-eks-now-supports-control-plane-egress-through-your-vpc/>