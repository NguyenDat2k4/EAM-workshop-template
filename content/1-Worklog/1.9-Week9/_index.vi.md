---
title: "Worklog Tuần 9"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.9. </b> "
---
Thời gian thực tập trong tuần này tập trung vào việc thiết kế kiến trúc triển khai hệ thống trên AWS, hoàn thiện tài liệu thiết kế kiến trúc và chuẩn bị đầy đủ các điều kiện cần thiết cho quá trình triển khai thực tế của dự án **EAM Workspace**.

### Mục tiêu tuần 9:
* Thiết kế kiến trúc triển khai hệ thống trên AWS.
* Hoàn thiện tài liệu thiết kế kiến trúc.
* Chuẩn bị triển khai thực tế.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| **Thứ 6** | - Phân tích yêu cầu triển khai dự án **EAM Workspace**.<br>- Phác thảo sơ đồ kiến trúc tổng thể (AWS Architecture Diagram) cho hệ thống.<br>+ Chuẩn bị các tài liệu thiết kế liên quan. | 12/06/2026 | 12/06/2026 | Project source code, Team discussion |
| **Thứ 7** | - Thiết kế luồng truy cập chi tiết từ người dùng cuối.<br>- Phân tích luồng qua Frontend (AWS Amplify), Application Load Balancer, Elastic Beanstalk và Amazon RDS.<br>+ Ghi nhận luồng xử lý gói tin và kết nối dữ liệu. | 13/06/2026 | 13/06/2026 | Project source code, Team discussion |
| **Chủ nhật** | - Thiết kế mô hình hạ tầng mạng logic cho hệ thống.<br>- Phân chia dải mạng gồm VPC, Public Subnet (cho ELB, NAT), Private Subnet (cho ứng dụng, DB), Internet Gateway và NAT Gateway.<br>+ Đảm bảo tính bảo mật và phân vùng hạ tầng hợp lý. | 14/06/2026 | 14/06/2026 | Project source code, Team discussion |
| **Thứ 2** | - Thiết kế tích hợp các dịch vụ lưu trữ đối tượng và gửi thư thông báo.<br>- Bổ sung dịch vụ Amazon S3 và Amazon SES vào thiết kế hạ tầng.<br>+ Lên phương án cấu hình và tích hợp mã nguồn. | 15/06/2026 | 15/06/2026 | Project source code, Team discussion |
| **Thứ 3** | - Thiết kế và bổ sung các giải pháp giám sát log, kiểm toán hạ tầng và quản lý cấu hình bảo mật.<br>- Tích hợp CloudWatch Logs, CloudTrail, Secrets Manager và Parameter Store.<br>+ Xây dựng quy chuẩn quản lý biến môi trường an toàn. | 16/06/2026 | 16/06/2026 | Project source code, Team discussion |
| **Thứ 4** | - Rà soát lại toàn bộ kiến trúc hạ tầng đã thiết kế.<br>- Đánh giá khả năng mở rộng (Scalability), tính sẵn sàng cao (High Availability) và bảo mật thông tin.<br>+ Chỉnh sửa các điểm chưa tối ưu trong bản vẽ kỹ thuật. | 17/06/2026 | 17/06/2026 | Project source code, Team discussion |
| **Thứ 5** | - Hoàn thiện sơ đồ kiến trúc và tổng hợp tài liệu mô tả kiến trúc triển khai.<br>- Đánh giá và chuẩn bị các tài nguyên cần thiết cho tuần triển khai hạ tầng thực tế.<br>+ Lập kế hoạch công việc cho tuần sau. | 18/06/2026 | 18/06/2026 | Project source code, Team discussion |

### Kết quả đạt được tuần 9:
* Hoàn thành sơ đồ kiến trúc triển khai AWS (AWS Architecture Diagram) cho hệ thống **EAM Workspace**.
* Hoàn thiện mô hình mạng và luồng triển khai chi tiết cho ứng dụng.
* Xác định đầy đủ các dịch vụ AWS cần sử dụng trong dự án bao gồm: AWS Amplify, Elastic Beanstalk, Application Load Balancer, Amazon RDS, Amazon S3, Amazon SES, CloudWatch, CloudTrail, Secrets Manager và Parameter Store.

### Kế hoạch tuần tiếp theo:
* Bắt đầu triển khai hạ tầng mạng (VPC, Subnet, Route Table, IGW, NAT Gateway) trên AWS.
* Thiết lập các dịch vụ AWS liên quan và chuẩn bị môi trường deploy ứng dụng.
* Thực hiện deploy thử nghiệm các cấu phần Frontend và Backend trên môi trường AWS thực tế.


