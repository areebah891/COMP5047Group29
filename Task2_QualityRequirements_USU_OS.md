# COMP5047 – Task 2: Analysis and Specify Software Quality Requirements 
**Subsystem:** USU Operation System  
**Functional Requirement:** FR-USU-1: Management of Unions  

---

## 1. Introduction

This task defines the quality requirements for the USU Operation System (a web-based application to run ondesktop or tablet computer for USU officers to manage the USU federation of student unions and realise
its functions) for the **functional requirement FR-USU-1: Management of Unions**.  
The quality requirements explained are Security & Privacy, Performance, Reliability, and Scalability.

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

### 3.1 Security and Privacy Protection

- Separation of data between tenants 
- Protection from security attacks

The goal is protect sensitive data (of the union,officers and students) and ensure only authorised USU staff can approve, update or terminate the union accounts. A key principle of the GDPR is to processs personal data securely with 'appropriate technical and organisational measures'. Therefore it's important to consider risk analysis, organisational policies and physical and technical measures. The measures we choose should comply with the CIA triad (confidentiality, integrity and availability). In the event of an incident the USU system should restore access and availability to users in short time. We should also have processes to test the effectiveness of our measures and act on improvements required.   

**Requirement Statements:**

1. Login and Authentication for USU system logins.

All USU officers must login with an unique username and a password which is minimum 12 characters including upper and lower case, numbers and special characters. This ensures only authorised USU officers can access the USU system. If invalid credentials are entered their access is denied. After 3 consecutive failed login attempts the account is temporarily locked for 20 minutes and via email the user is notified, protecting against brute-force attacks. The system uses Multi-factor authentication (MFA) using a SMS or email one-time code. This adds an extra layer of protection for the sensitive data. If code is not correct access is denied. Sessions can be managed by automatically logging out after 10 minutes of inactivity. This ensures if a workstation is left access to the account by others is prevented. Lastly, all login attempts must be logged to an audit log with the username, timestamp, IP address and device so we can trace logins and detect suspicious activity.
   
2. Only authenticated USU officers can access the FR-USU-1 functions, which can be ensured with role-based access control (RBAC).

RBAC determine access rights and helps the USU subsystem to assign permissions more effectively, maintain compliance and protect sensitive information. We need to make sure that only verified USU operators can approve memberships, approve updates of registration details and approve termination of memberships. PoLP is the principle of least priviledged, where users are granted only yhte minimum access rights and permissions needed to perform the authorised job, and nothing more. For example, the union can request an update in their registration details but USU operators are the only ones who can approve this update and therefore allow it to show on the website. This prevents unauthorised manipulation of union membership data ensuring integrity. If a user was to login and perform the function requirements (FR-USU-1) with a non-USU-officer account their access will be denied.

3. All personal and membership data will be encrypted in storage (AES-256) and in transit (TLS 1.3).

The GDPR says we must implement measures to process personal information securely. This can be done with encryption which can be low cost. Sensitive personal and union data like student passwords,IDs,contact information and event details should be encrypted at rest with AES-256 (uses a 256-bit key to convert plaintext into ciphertext prevent brute force) and in transit using TLS 1.3 (using a faster handshake). So data stored in database should be encrypted and when transferred over the network should be monitored, readable only when decrypted authorised.
 
4. All union-related actions (approval, update, termination) must be logged with timestamp, user ID, and action type.

The National Cyber Security Centre say 'logging is the foundation on which security monitoring and situational awareness are built'. The USU subsystem will maintain an audit log for all operations on union account like approval, update and termination. The log should record the user, timestamp, action and affected union. The NCSC  says this means 'we will be better prepared for the upmost pressing questions and give the best chance of recovering and learning how to defend the system better'. It is important to review these logs regularly (every 6 months) that they are correctly created. 

5. All data is securely reteained suring deactivated period (1 month) and then permanently deleted. 

The GDPR says 'organisations must not keep personal data longer than necessary for the specified purpose and must have a clear data retention policy that justifies these periods'. To justify the retention policy: unions may want to reactivate their account. Users have a right that their data is deleted when it is no longer necessary for its original purpose. Deletion must include all union officer and student member data. After 1 month we verify the deletion of records and that archived data is inaccessible to unauthorised users. 
 

---

### 3.2 Performance

The goal is to ensure USU operators can carry out functional requirements FR-USU-1 without delays regardless of large amounts of many USU's memberships data. The ISO 25000 says 'Performance efficiency represents the degree to which a product performs its functions within specified time and throughput parameters and is efficient in the use of resources'. We must implement measures that meet performance requirements. Without this quality our system can cause USU operators problems and prevent meeting the needs of everyone involved correctly and in time.

**Requirement Statements:**  

1. Response time for approval or termination actions must be ≤3 seconds for a single USU officer.

ISO 25000 states that a sub-characteristic of performance efficiency is 'Time behaviour - Degree to which the response time and throughput rates of a product or system, when performing its functions, meet requirements.' The USU OS will ensure any action by the USU operator is completed within 3 seconds under normal load conditions for a single concurrent user, ensuring usability and operational efficiency for critical administrative functions. This is measurable with logs recording the start and end time of an action performed by the user. 

2. System must support 50 concurrent USU officers performing operations without noticeable delay.

ISO 25000 (ISO/IEC 25010:2011) states that a sub-characteristic of performance efficiency is Capacity 'Degree to which the maximum limits of a product or system parameter meet requirements' and Scalability 'Degree to which the system can effectively and efficiently expand to accommodate increased load.' The USU Operation System will ensure that up to 50 USU officers can perform approval, update, or termination operations concurrently without noticeable delays, ensuring smooth and efficient management of union accounts during peak administrative periods. This is measurable by performing load testing with 50 virtual users and recording response times for each operation to verify that system performance remains within acceptable thresholds.

3. Throughput - system shall handle at least 1000 membership approval/update/termination requests per hour during peak periods.

Throughput measures the number of operations a system can perform within a given period of time. For the USU Operation System, ensuring a throughput of at least 1000 requests per hour during peak periods guarantees that the system can support high loads from multiple university-specific student unions without causing delays or service disruption. This is measurable by logging the timestamp of each request and calculating the number of requests processed per hour. Meeting this requirement ensures operational efficiency, scalability, and a responsive experience for USU officers managing union accounts. 
   
 
3.2 Performance

Goal: Ensure USU officers can efficiently process union membership operations and manage nationwide events without delays, maintaining a responsive and usable system.

**Requirement Statements:**

1. Response Time for Single User

Requirement: Response time for approval, update, or termination actions must be ≤3 seconds for a single USU officer under normal load conditions.

Rationale: ISO 25000 states that a sub-characteristic of performance efficiency is “Time behaviour - Degree to which the response time and throughput rates of a product or system, when performing its functions, meet requirements.” Meeting this response time ensures usability and operational efficiency for critical administrative functions.

Verification: Measured using system logs that record the start and end time of each action.

2. Concurrency

Requirement: The system must support 50 concurrent USU officers performing operations (approvals, updates, or terminations) without noticeable delay.

Rationale: ISO 25000 emphasizes multi-user efficiency, ensuring a system can maintain acceptable response times under concurrent use. Supporting 50 concurrent operators ensures that multiple USU officers can perform nationwide administration tasks simultaneously without degrading performance.

Verification: Conduct load testing with simulated concurrent users to confirm response times remain ≤3 seconds per action.

3. Throughput

Requirement: The system shall handle at least 1,000 membership approval, update, or termination requests per hour during peak periods.

Rationale: ISO 25000 notes that throughput is a key measure of time behavior, indicating the system’s capacity to process multiple requests efficiently. Ensuring a throughput of 1,000 requests/hour allows USU officers to manage high-volume operations, particularly during peak registration or event periods.

Verification: System logs and monitoring tools will track the number of requests processed per hour; testing under peak load conditions will verify compliance.

4. Scalability Margin 

Requirement: The system should maintain acceptable performance with up to 20% more concurrent users (60 USU officers) or 20% higher throughput (1,200 requests/hour) to accommodate unexpected peak loads.

Rationale: Providing a scalability margin ensures the system remains usable as the federation grows, preventing performance bottlenecks during unusually high activity.

Verification: Conduct stress testing under elevated load conditions to confirm acceptable response times and throughput.
---

### 3.3 Reliability
**Requirement Statements:**  
1. FR-USU-1 functions must be available **99.5% of business hours**.  
2. System must provide **meaningful error messages** for invalid or incomplete applications.  
3. Daily **backups** must allow recovery within **2 hours** in case of system failure.  

---

### 3.4 Scalability
**Requirement Statements:**  
1. System must handle up to **200 concurrent USU officers** without performance degradation.  
2. Must support up to **500 university-specific student unions** and their associated members/events.  
3. Must allow **auto-scaling** during peak periods (e.g., start of academic year) to maintain performance.  

---

## 4. References
1. COMP5047 Case Study: USU Federation of Student Unions.  
2. GDPR Regulations (EU).  

