# COMP5047 – Task 2: Analysis and Specify Software Quality Requirements 
**Subsystem:** USU Operation System  
**Functional Requirement:** FR-USU-1: Management of Unions  

---

## Introduction

A quality requirement is a non-functional requirement that constrains how software should meet its functional requirements or how it should be developed (Pressman & Maxim).
This document defines the software quality requirements for FR-USU-1: Management of Unions in the University Student Unions system. FR-USU-1 includes key functions such as approving union membership, updating union registration data, and terminating memberships. These actions involve sensitive organisational and personal data, decision-making authority, and nationwide usage, making clear quality requirements essential to ensure the system is secure, performant, reliable, and scalable.
Each quality requirement specifies measurable and testable criteria, including a metric, unit of measurement, target value, and precision. The target value defines the desired level of performance, making the requirement falsifiable and objectively verifiable. Precision specifies the granularity of measurement, ensuring consistent and repeatable testing. This approach guarantees that all requirements are clear, unambiguous, and verifiable, enabling systematic evaluation of the system’s performance, reliability, security, and scalability (Kazman; ISO/IEC 25010).

<details>
<summary>2. Functional Requirement Overview</summary>

**FR-USU-1: Management of Unions** includes:  
**(a) approval of USU membership applications** submitted by university-specific student unions (FR-UO-5 explains the details for the data required for an application to the USU membership).
   - name of event
   - theme of event
   - connection to other events
   - name of organisers and there roles
   - date and time of event
   - venue of event
   - optional plan of the evnet
   - participation constraints: if it's required to register and/or buy a ticket in advance or on site
   - scope: if it is nationwide, regional or specific university students
   - promotion scope: where and who it will be promoted to
   - promotion materials: photos, video streams, text descriptions, posters, URL

approval of union membership means:

1. union's registration data will be stored in the system and used for communication with the union and its student members
2. union officers as recorded in the registration data will get access to the system as Union Officers
3. union’s account become active = students at the university will be able to register to the system as student member users and obtain access to the system
4. events organised by union are promoted on USU system
5. union can participate in nation-wide events organised by USU

**(b) Approval of updates of USU registration data**

- system should provide a facility to the USU to review and approve the request of changes to its data

**(c) Approval of termination of USU membership**

- system should provide a facility to USU staff to review and approve request of termination of USU membership submitted by university specific student union
- receiving this request implies the union's account becomes inactive =
1. no new student members of the uni will be registered to the system
2. no update of union's events and other info will be stopped
3. union's participation of USU events are not allowed
- approval of termination implies
1. union's account remains inactive for 1 month
2. after 1 month = data of the union removed from the system. Union officers' account removed from system with all data deleted. Student members of the union removed from system with all data deleted.


**Goal:** Ensure USU staff can securely, efficiently, and reliably manage union accounts and associated data, supporting nationwide operations.


</details>

---

## 3. Quality Requirements

# Scenario 1: Login and Authentication/ Privilege Access 

| Quality Attribute | Requirement Statement | Metric | Unit | Precision | Target Value | How to Measure / Test |
|------------------|---------------------------------|--------|------|-----------|--------------|---------------------|
| Security | All USU officers must login with unique username/password (min 12 chars) + MFA, invalid attempts denied, account locks after 3 failed attempts for 20 mins. | Unauthorised access attempts | Attempts | 1 | 0 successful | Attempt login with invalid credentials, verify lockout occurs, check audit log |
| Performance | Login response time must be fast to avoid delays. | Response time | Seconds | 0.1 | ≤ 2 | Automated timing of login requests under normal and peak times |
| Reliability | System must correctly authenticate users on every attempt. | Authentication success rate | % | 0.1 | 100 | Test valid credentials multiple times, confirm system always authenticates correctly |
| Scalability | System must support concurrent logins from all USU officers. | Max concurrent logins | Users | 1 | ≥ 500 | Load testing with 500+ concurrent login attempts |
                                                         

Security in this context means preventing unauthorised users from accessing sensitive union data and system functions. Performance refers to how quickly the system responds to login requests. Reliability means the authentication process must work correctly every time without failure, and scalability means the system must support many officers logging in concurrently without degradation.
This scenario ensures that only authorised USU officers access FR-USU-1 functions. Security measures such as multi-factor authentication (MFA), strong password policies, session management, and audit logging create a layered defence against unauthorised access, brute-force attacks, and insider threats, ensuring compliance with GDPR. Reliability ensures the system remains available and functional at all times, while performance and scalability requirements guarantee smooth operation even under peak load. All aspects are measurable and testable, e.g. login response time can be timed, authentication success can be tracked, and concurrent logins can be stress-tested.

# Scenario 2: Approval of Membership (FR-USU-1a)

| Quality Attribute | Requirement Statement | Metric | Unit | Precision | Target Value | How Measured / Tested |
|------------------|---------------------------------|--------|------|-----------|--------------|---------------------|
| Security | Only authenticated USU officers can approve membership; logs maintained. | Unauthorised access attempts | Attempts | 1 | 0 | Attempt approval with non-officer account, check logs for completeness |
| Performance | Approval processing time must be fast. | Approval processing time | Seconds | 0.1 | ≤ 5 | Measure time from submission to system confirmation |
| Reliability | Approved memberships must be stored and accessible immediately. | Correct approvals | Count | 1 | 100% | Approve sample memberships, verify correct data storage and retrieval |
| Scalability | System must handle approval of up to 1000 memberships/hour. | Memberships processed/hour | Count | 1 | ≥ 1000 | Simulate bulk approvals under load, verify system handles expected volume |

Security in this context means only authorised USU officers can approve new unions, and all actions are fully traceable through audit logs. Performance refers to the speed at which membership approvals are processed, ensuring timely response even under heavy load. Reliability means that approved membership data is stored correctly and consistently without errors, guaranteeing correct account activation and role assignments. Scalability ensures the system can handle a high volume of membership approvals simultaneously, particularly during busy periods such as the start of the semester.
The approval process ensures that only verified unions participate in USU activities. Measures such as encryption and audit logging maintain confidentiality, integrity, and auditability, supporting accountability and compliance with data protection regulations (GDPR). All quality attributes are measurable and testable: approval processing time can be timed, correct storage of membership data can be verified, and system performance under peak load can be stress-tested to confirm scalability. 

# Scenario 3: Approval of Updates to USU Registration Data (FR-USU-1b)

| Quality Attribute | Requirement Statement | Metric | Unit | Precision | Target Value | How Measured / Tested |
|------------------|---------------------------------|--------|------|-----------|--------------|---------------------|
| Security | Only USU officers can approve updates, all updates logged. | Unauthorised updates | Count | 1 | 0 | Attempt update with non-officer account, verify logs capture all actions |
| Performance | Update approval must propagate changes quickly. | Update propagation time | Seconds | 0.1 | ≤ 5 | Measure time from approval to data visible in system |
| Reliability | Approved updates must reflect correctly without errors. | Accuracy of updates | % | 0.1 | 100 | Verify updated data against intended changes in test database |
| Scalability | System must support 500 unions updating concurrently. | Concurrent updates handled | Count | 1 | ≥ 500 | Simulate 500 concurrent updates, confirm system stability |

Security in this context means only authorised USU officers can approve updates, and all changes are fully auditable through detailed logs. Performance refers to the speed at which approved updates propagate and become visible in the system, ensuring timely access to accurate information. Reliability means that updated data must be stored correctly and consistently without errors, preserving the integrity of union registration records. Scalability ensures the system can handle multiple unions submitting updates concurrently without degradation in performance.
Scenario 3 ensures that union registration data remains accurate, secure, and up to date. Encryption protects confidentiality, and logging enables traceability and accountability, supporting compliance with data protection regulations (GDPR). All quality attributes are measurable and testable: update propagation time can be timed, data accuracy verified against intended changes, and system performance under concurrent updates can be stress-tested to confirm scalability.

# Scenario 4: Approval of Termination of Membership (FR-USU-1c)

| Quality Attribute | Requirement Statement | Metric | Unit | Precision | Target Value | How Measured / Tested |
|------------------|---------------------------------|--------|------|-----------|--------------|---------------------|
| Security | Only USU officers can approve terminations, accounts locked, logs maintained. | Unauthorised terminations | Count | 1 | 0 | Attempt termination with non-officer account, check audit logs |
| Performance | Termination requests processed promptly. | Termination processing time | Seconds | 0.1 | ≤ 10 | Measure time from request approval to account deactivation |
| Reliability | Terminated accounts deactivated, data retained 1 month then deleted. | Deactivation & deletion success | % | 0.1 | 100 | Verify deactivated accounts cannot log in, check data deletion after 1 month |
| Scalability | System must handle 1000 concurrent terminations. | Concurrent terminations handled | Count | 1 | ≥ 1000 | Simulate 1000 termination requests concurrently, confirm system stability |

Security in this context means only authorised USU officers can approve terminations, and all termination actions are logged for traceability and accountability. Performance refers to the speed at which termination requests are processed and accounts deactivated, ensuring timely removal of inactive unions. Reliability means that terminated accounts are consistently disabled, retained securely for one month, and permanently deleted thereafter, preserving data integrity and compliance with GDPR. Scalability ensures the system can handle large volumes of terminations simultaneously without failure or performance degradation.
Scenario 4 guarantees that inactive unions are removed safely and securely. Temporary retention allows potential reactivation, while permanent deletion protects privacy and sensitive data. All quality attributes are measurable and testable: termination processing time can be timed, deactivation and deletion verified, and system behaviour under concurrent terminations stress-tested to confirm scalability. Logging provides a verifiable audit trail to support security and accountability.

  

