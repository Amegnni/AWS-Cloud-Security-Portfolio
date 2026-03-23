# S3 Data Protection & Disaster Recovery Lab

## Objective

The goal of this project was to understand how AWS S3 protects data and supports disaster recovery through versioning, object lock, and replication concepts.

---

## Services Used

- AWS S3
- AWS CLI
- S3 Bucket Policies
- S3 Replication (conceptual)
- Multi-Region Access Points (conceptual)

---

## Security Concepts Demonstrated

- Data durability and recovery
- Versioning and delete markers
- Object Lock (Governance vs Compliance)
- Retention periods and immutability
- Bucket policy enforcement (explicit deny)
- Disaster recovery through replication
- Multi-region architecture (high-level)
- Cross-account isolation (conceptual)

---

## What I Implemented

### 1. Versioning

- Enabled versioning on an S3 bucket  
- Uploaded and modified objects to observe version history  
- Learned that deleting an object creates a delete marker instead of removing data  

---

### 2. Object Lock

- Applied object lock with a retention period  
- Observed how objects cannot be deleted or modified during retention  
- Understood the difference between:
  - Governance mode (can be bypassed with permission)
  - Compliance mode (cannot be bypassed)  

---

### 3. Bucket Policy Enforcement

- Tested access behavior with and without bucket policies  
- Observed that explicit deny overrides all other permissions  
- Confirmed that removing a bucket policy immediately changes access behavior  

---

### 4. Data Protection Behavior

- Observed how:
  - delete markers hide objects instead of deleting them  
  - object versions remain preserved  
  - retention policies prevent deletion  

---

### 5. Disaster Recovery (Conceptual)

- Learned how S3 replication copies data across buckets and regions  
- Understood the role of Multi-Region Access Points for failover  
- Explored the idea of cross-account replication for stronger isolation and security  

---

## Key Observations

- S3 does not immediately delete data when versioning is enabled  
- Object Lock enforces immutability, preventing deletion even for administrators  
- Bucket policies act as a final security layer through explicit deny  
- Disaster recovery requires both replication and proper access design  
- Security in AWS is layered across identity, resource policies, and data controls  

---

## Challenges Encountered

- Unable to delete objects due to active retention period  
- Encountered AccessDenied errors caused by bucket policy restrictions  
- Learned how delete markers and object versions affect cleanup operations  

---

## What I Learned

This project helped me understand that cloud security is not only about controlling access, but also about protecting the integrity and availability of data.

By combining versioning, object lock, and bucket policies, AWS creates a system where data cannot be easily lost or tampered with. I also learned how disaster recovery is designed using replication and multi-region concepts to ensure resilience.

---

## Status

Module 5 (Cross-Account Replication) was not fully implemented due to requiring a second AWS account, but the architecture and concepts were studied and understood.

---

## Resume-Ready Summary

Implemented S3 data protection mechanisms using versioning, object lock, and bucket policies, and explored disaster recovery design through replication and multi-region architecture concepts to understand how AWS ensures data durability, security, and resilience.
