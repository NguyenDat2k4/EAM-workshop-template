---
title: "Amazon EKS Supports Control Plane Egress Routing Through VPC"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

Hello everyone in AWS Study Group VN! While exploring Containers on AWS, I discovered that Amazon EKS now officially supports **Customer-routed control plane egress**. This feature allows routing outbound traffic from the Kubernetes Control Plane through your own VPC instead of the default path managed by EKS.

Previously, when the Kubernetes API Server made outbound calls (e.g., calling an Admission Webhook, querying an OIDC Identity Provider, or calling an Aggregate API Server), all of this traffic would go through the EKS-managed network path. For organizations in regulated sectors like finance, healthcare, or government, it was very difficult to apply unified security policies, firewalls, VPC routing, and logging.

With **Customer-routed control plane egress**, AWS allows routing this "customer-controllable" traffic out via Elastic Network Interfaces (ENIs) located right inside your VPC. This enables you to:
* Apply Security Groups to control the traffic.
* Route traffic through AWS Network Firewall.
* Use VPC Endpoints or PrivateLink.
* Monitor traffic using VPC Flow Logs.
* Connect to on-premises systems via AWS Direct Connect.

![EKS Control Plane Egress](/images/3-BlogsPosted/eks_control_plane_egress.png)

### Conclusion:
The Customer-routed control plane egress feature is a major step forward, making EKS more suitable for enterprises with strict security requirements. Now, you can apply a unified network policy for both the Data Plane and the Control Plane. This is highly valuable knowledge for anyone working with Kubernetes and Security on AWS.

**Reference Source:**
<https://aws.amazon.com/blogs/containers/amazon-eks-now-supports-control-plane-egress-through-your-vpc/>