---
## Functional Requirements for USU Operation System 
---

# 4.1. Union Officer Functional Requirements – USU Operation System

**grouped according to types of users**

<details>
<summary>4.1. Union Officer Functional Requirements – USU Operation System</summary>

### FR-UO-1: Managing USU Membership

**(a) Creating a Union Membership**  
my subsytem needs to let USU officers review and handle new union applications easily. For each application, officers should be able to see the registration details:  
- the university name and address
- union website link
- info on union reps (name, contact, student ID, role, USU ID)  
- info on delegated IT officers (names, contact details and user IDs in USU system as students)  

Once approved:  
- a tenant account for the union is created in the system
- above registration data of studiont union stored in USU computer system 
- creation of computer access accounts for the delegated IT officers and ready for activate according to the information provided
- the union’s website gets either created or mirrored on the USU portal.  
- all data is stored securely.  
- officers and the union get notifications that the membership is approved.

**(b) Updating Membership Data**  
- officers should be able to see requested changes from unions  
- approve or reject updates.  
- changes automatically reflect in the system 
- notify the union about what’s changed.

**(c) Terminating Membership**  
- handle termination requests from unions
- deactivate union accounts and remove access
- keep a record for a short time, then delete the data permanently
- notify everyone involved.

---

### FR-UO-3: Managing Societies

**(a) Approving New Societies**  

- officers should be able to approve society applications including:  
  - name: the name of the society
  - theme: a description of the society about its theme topic and targeted group of students.
  - organisation team: the society leader, including name, student ID, USU user ID; information about other members of organisation team and their roles.
  - contact address: the contact person’s name, address, telephone number, email address. 

- store the approved data and show the society on the union’s portal.

**(b) Approval of requests of changes in societies registration data**
- officers should see the requested changes from union of thier registered data 
- approve or reject updates
- once approved these changes should update automatically in the system
- notify the union what has changed

**(c) Approval of request of termination of society**
- handle termination requests from unions
- once terminated deactivate union account (removed from union website) and remove access
- keep a record of the acccount data stored in system with record of deactivation kept for a short time before deleting data permanently
- notify everyone involved

**(d) Monitoring the operations of societies**  
- keep track of all events run by societies 
- notify union officers about new or updated events with full details of event info
- provide a simple dashboard for monitoring events and feedback 
- allow comments or flags if there are issues

---

### FR-UO-5: Managing Union Events

Officers should be able to create and manage events with all the info:  
- ame, theme, connection to other events 
- organisers and their roles
- date, time, venue
- event plan (optional)
- participation requirements (if required register or ticket onsite or online)  
- scope (public, university-specific, or group-specific)
- promotion scope and materials (photos, videos, posters, links)

the system should:  
- store all the event info in USU system   
- notify USU officers and relevant unions  
- automatically make a webpage for nationwide events
- handle online registration/tickets if needed

---

### FR-UO-6: Management of the union

- system should provide the facility to support the operation of the student union, including running annual elections and by-elections of union personnel   
- make sure officer handover is smooth
- keep a history of past officers 
- provide reports and dashboards so officers can monitor union activities easily

</details>

<details>
<summary>4.2 Requirements of Society Leaders – USU Operation System</summary>

This part explains what the USU Operation System does for society leaders through the system. Basically, society leaders can manage their societies and events, but all interactions are tracked and supported by the USU officers via your subsystem.

## FR-SL-1: Management of Society

**(a) Activation of New Society**  
- after a union approves a new society, the USU system notifies society leaders through the web portal
- activation = society is live,so:  
  - students can subscribe to the society
  - society info is shown on the union’s website (mirrored or hosted via USU portal)

**(b) Update Society Registration Data**  
- society leaders can submit changes (e.g., handover leadership)  
- USU Operation System allows officers to review and approve these updates, which are then reflected online

**(c) Management of Society Membership**  
- Leaders can choose if new members are approved automatically or need manual approval.  
- The system tracks all subscriptions for monitoring and reporting purposes.

**(d) Communication with Society Members**  
- leaders can view their member list
- system supports group broadcasts and individual messages with all communication logged for records

**(e) Termination of the Society**  
- society leaders can submit a termination request
- once submitted, the society is deactivated (no new subscriptions)  
- USU officers review and approve the termination.  
- after approval:  
  - society is removed from the union website  
  - all members are unsubscribed  
  - data is retained in the system for record-keeping

## FR-SL-2: Management of Events

**(a) Creation of Event**  
- society leaders can propose new events through the USU Operation System
- required details include:  
  - name, theme, connection to other events  
  - organisation team (names and roles)  
  - date, time, venue  
  - optional plan/description  
  - participation rules (registration/ticketing)  
  - scope (who can join) and promotion scope  
  - promotion materials (photos, videos, text, URL, posters)  
- officers review and approve events, then the system promotes events according to the scope (students, union members, nationwide, etc.)

**(b) Update on an Event**  
- society leaders can submit updates on events (progress, changes, new info)
- USU officers review updates, and once approved, the system automatically updates the event info in real time across the portal


</details>

<details>
<summary>4.3 Requirements of Students - USU OS</summary>

explain how the USU Operation System supports student activities. Students mainly interact indirectly through the system, and USU officers manage, approve, and track these interactions.

## FR-ST-1: Registration to University-Specific Student Union
- students submit registration applications through the system (desktop/tablet interface is handled by USU officers).  
- required info includes:  
  - name, student ID, study program, year of start, length of program  
  - contact addresses (email, mobile, postal)  
  - optional supporting documents (like student card)  
- USU officers use the system to validate registrations (automatically via university IT or manually)  
- successful registration:  
  - student gets a unique USU membership ID  
  - access to system is granted as a student user  
  - data is stored for communication and membership management

## FR-ST-2: Joining and Subscribing to Society
- Students can search and subscribe to societies via the USU system interface (officers monitor).  
- Only societies affiliated with the student’s university-specific union are available.  
- Officers can track subscriptions and approve them if needed.

## FR-ST-3: Quitting and Unsubscribing from a Society
- students can request to quit/unsubscribe from a society 
- USU system logs these actions and updates the student’s membership status
- officers are notified of changes and can review if necessary

## FR-ST-4: Communication to Society
- students can send messages to societies they belong to
- messages are broadcasted only to members
- USU officers can monitor for inappropriate content or issues if needed

## FR-ST-5: Initiation of New Society
- students can propose a new society by submitting an application via the system.  
- application info includes:  
  - name, theme, organisation team (applicant becomes default leader), contact info  
- USU officers review and approve applications before the society becomes active 
- once approved, the society is visible on the union’s website and students can subscribe

## FR-ST-6: Participation in Events
- students can search for events, view details, and subscribe for updates via the system
- registration or ticketing requests are submitted through the USU system
- USU officers monitor participation, approve registrations if needed, and ensure event info is updated in real time

</details>

<details>
<summary>4.4.	Requirements of USU Operators</summary>

What USU officers can do using the USU Operation System to manage the federation of student unions and their events.

## FR-USU-1: Management of Unions

### (a) Approval of USU membership
- officers use the system to review and approve membership applications from university-specific student unions  
- approval means:  
  1. unions’ registration data will be stored in the system and used for communication with the union and its student members  
  2. union officers as recorded in the registration data will get access to the system as Union Officers
  3. union account becomes active so students can register as members  
  4. events organised by the union get promoted through the USU system
  5. the union can officially participate in nationwide USU events  

### (b) Approval of updates to USU registration data
- officers can review and approve requests to update union data (like personnel changes, contact info, or website updates)  
- all updates are stored and tracked in the system

### (c) Approval of termination of USU membership
- officers can review requests to terminate a union’s membership  
- when a termination request is received, the account becomes inactive:  
  1. no new student registrations are allowed for that university.  
  2. no updates to union registration data are possible.  
  3. union events or info updates stop.  
  4. union cannot participate in USU events
- after approval:  
  1. Union account stays inactive for one month 
  2. After a month, all union data, union officer accounts, and student memberships are **permanently deleted**.

## FR-USU-2: Management of USU Events

### (a) Initiation of New Event
- officers can **create new events** using the system.  
- required event info:  
  - name, theme, related events, organiser names/roles  
  - date, time, venue, optional plan  
  - participation rules (registration/tickets)  
  - scope (who can attend)  
  - promotion scope and materials (photos, videos, posters, URLs)  
- After creation:  
  1. event is announced on the USU portal
  2. union officers are notified
  3. student members are notified  
  4. subscription/participation facilities open for students 
  5. union endorsement for the event becomes possible

### (b) Announcements and Progress Updates
- officers can push announcements or updates about events
- updates are visible on the portal and pushed to all subscribed students and participating members

### (c) Student Participation
- officers can manage student subscriptions and registrations for events via the system

### (d) Union Participation
- officers can endorse events on behalf of their union through the system

</details>
