---
title: "Amazon EKS Auto Mode and Istio Ambient Mesh Integration"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---
# Integrating Amazon EKS Auto Mode and Istio Ambient Mesh Architecture

Hello everyone in AWS Study Group VN! While researching Kubernetes, I came across an AWS article introducing the combination of Amazon EKS Auto Mode and Istio Ambient Mesh. These two technologies work together to significantly reduce operational overhead while automatically strengthening service-to-service security.

As a microservices system grows from a few services to hundreds of services, two major issues arise: managing infrastructure (node provisioning, patching, scaling) and securing communications between services. EKS Auto Mode + Istio Ambient Mesh is the "Better Together" solution to solve both issues.

### 1. Amazon EKS Auto Mode
This is a powerful automation mode for EKS, where AWS manages almost the entire compute layer:
* Automatic provisioning, scaling, and patching of nodes using Karpenter (a customized version).
* Powered by the Bottlerocket operating system – minimal, immutable, and highly secure.
* System components (VPC CNI, kube-proxy, EBS CSI, CoreDNS, Load Balancer Controller, etc.) are managed by AWS as system processes, removing the need for manual add-on deployments.
* Eliminates the need to SSH into nodes, reducing the attack surface.

### 2. Istio Ambient Mesh
This is the sidecarless architecture of Istio, allowing you to apply a service mesh without injecting sidecar proxies into every pod:
* **ztunnel (per-node proxy):** Handles Layer 3/4 – automatic mTLS, L4 authorization, and TCP telemetry.
* **Istio-cni:** A chained CNI plugin that redirects traffic through the ztunnel.
* **Waypoint Proxy (optional):** Handles Layer 7 functions (HTTP routing, retries, L7 authorization, circuit breaking, etc.) when needed.

![EKS Auto Mode + Istio Ambient Mesh](/images/3-BlogsPosted/eks_auto_mode_istio_ambient.png)

### Conclusion:
The combination of Amazon EKS Auto Mode and Istio Ambient Mesh delivers a modern Kubernetes environment: robust compute automation coupled with flexible service mesh security without complicating application code. This is a highly recommended direction for teams building microservices platforms on AWS.

**Reference Source:**
<https://aws.amazon.com/blogs/containers/better-together-amazon-eks-auto-mode-and-istio-ambient-mesh/>