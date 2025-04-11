
# Cloud Provider Subnet and IP Address Comparison

This document provides a detailed comparison of subnet-related behavior across the three major cloud providers: **AWS**, **Azure**, and **Google Cloud Platform (GCP)**.

## 📊 Feature Comparison Table

| Feature                         | AWS                            | Azure                                | GCP                            |
|---------------------------------|---------------------------------|---------------------------------------|--------------------------------|
| Reserved IPs per Subnet         | 5                               | 5                                     | 4                              |
| Subnet Range Reserved           | .0, .1, .2, .3, .255            | .0, .1, .2, .3, .255                  | .0, .1, .2, .255               |
| Default Max Subnets per VPC/VNet| 200                             | ~1000                                 | 500                            |
| Default Subnet Size Range       | /28 to /16                      | /29 to /8                             | /29 to /8                      |
| Supports Subnet Expansion       | ❌ (must recreate)              | ✅ (with certain limitations)         | ❌ (must recreate)             |
| Custom Route Tables per Subnet  | ✅                              | ✅                                     | ✅                             |
| Private Subnet Support          | ✅                              | ✅                                     | ✅                             |
| Service Endpoint Support        | ✅ (Interface & Gateway)       | ✅ (Service Endpoints & Private Link) | ✅ (Private Google Access)     |
| NAT Gateway Support             | ✅                              | ✅                                     | ✅                             |
| Subnet-level Network ACLs       | ✅ (Network ACLs)              | ❌ (uses NSGs)                         | ❌ (uses Firewall Rules)       |

## 🔍 Notes

- **AWS and Azure** both reserve 5 IPs per subnet, including network/broadcast and internal infrastructure IPs.
- **GCP** reserves 4 IPs, slightly less, as it doesn't reserve a future-use address like AWS.
- Subnet size and limits are critical when planning VPC/VNet growth—Azure is the most flexible by default.
- Subnet expansion is only natively supported in Azure, with AWS and GCP requiring recreation of the subnet.
- ACL enforcement differs: AWS uses **Network ACLs**, while Azure and GCP rely on **NSGs** or **Firewall Rules**.

> Always consult your cloud provider’s latest documentation before deploying in production, as quotas and features may change.

---

Generated for cloud architecture knowledge sharing.
