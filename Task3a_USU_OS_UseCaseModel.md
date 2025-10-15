# COMP5047 Task 3a: Specification and Modelling Software Functional Requirements, Use Case Model
**Subsystem:** USU Operation System  

---
Below is an outline of the 7 use cases (UC) for USU operation system. 

<details>
<summary>UC-01: Submitting and approving USU Membership</summary>

## UC-01: Submitting and approving USU Membership

**Primary Actor:** USU officer **Secondary Actor:** Union officer

Union officer submits their membership application to join the USU federation. USU officer revoews and approves the application via USU OS, creating a tenant account and enabling access for the union.

**Entry Conditions:**

- Union Officer has filled and submitted the membership application.
- USU Officer is logged in to USU OS with permissions to approve memberships

   
**Exit Conditions (on success)**

- Union membership is approved and active 
- Tenant account and access accounts are created for the union  
- Notification is sent to the Union Officer about approval or rejection

| **Actor: Union Officer**                     | **Actor: USU Officer**                                | **System: USU OS**                                                                                                                                        |
| -------------------------------------------- | ----------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1. Fills in the membership application form. | —                                                     | 2. Validates the submitted data and ensures all required fields are complete.                                                                             |
| 3. Submits the application.                  | —                                                     | 4. Notifies the USU Officer of a new application.                                                                                                         |
| —                                            | 5. Opens the list of pending membership applications. | 6. Displays all pending applications.                                                                                                                     |
| —                                            | 7. Selects a specific application to review.          | 8. Shows full union details and representative data.                                                                                                      |
| —                                            | 9. Reviews the application.                           | 10. Waits for the USU Officer to decide.                                                                                                                  |
| —                                            | 11. Clicks **Approve Application**                    | 12. Validates data, finalizes approval, creates tenant account, generates access accounts, activates membership, and sends notification to Union Officer. |
| 13. Receives confirmation of approval.       | —                                                     | 14. Displays success message and updated status.                                                                                                          |

**Exceptional flows**
1. incomplete application: system detects missing fields -> notifies Union Officer to complete data -> application resubmitted
2. invalid data: system flags error -> USU officer rejects application -> notifies UO with reason
3. system error during account creation: system logs error -> notifies USU officer -> manual intervention required

</details>

<details>
<summary>UC-02: Approve Updates to USU Membership</summary>

## UC-02: Approve Updates to USU Membership

**Primary Actor:** USU officer **Secondary Actor:** Union officer

UO Officer submits a request to update their union membership information and the USU officer reviews and approves the updates via USU OS.

**Entry Conditions**

- Union has an active membership in USU
- USU Officer is logged in with permissions to approve membership updates

**Exit Conditions (on success)**

- Union’s registration data is updated in the USU OS
- Relevant Union Officers are notified of the changes

**Main Flow**

| **Actor: Union Officer**                        | **Actor: USU Officer**                       | **System: USU OS**                                                                   |
| ----------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------------ |
| 1. Submits a request to update membership data. | —                                            | 2. Receives the update request and validates submitted data.                         |
| —                                               | 3. Opens list of pending membership updates. | 4. Displays all pending update requests.                                             |
| —                                               | 5. Selects specific update request.          | 6. Shows current and proposed membership details.                                    |
| —                                               | 7. Reviews and verifies the update request.  | 8. Waits for USU Officer to approve or reject.                                       |
| —                                               | 9. Clicks **Approve Update**.                | 10. Applies updates to membership data, logs the change, and notifies Union Officer. |
| 11. Receives confirmation of approved updates.  | —                                            | 12. Displays updated membership status.                                              |

**Exceptional Flows:**
- Invalid update data: system detects error -> USU officer rejects request -> notifies UO
- missing required fields: system notifies UO to complete missing data -> request resubmitted
- system failure during update: system logs error -> notifies USU officer -> manual intervention needed

**Special requirements**
- updates must be logged for audit purposes
- notifications must reach UO via email and USU OS dashboard
- changes must be reflected in real time accross system

</details>

<details>
<summary>UC-03: Termination of USU Membership</summary>

## UC-03: Termination of USU Membership

**Primary Actor:** USU officer **Secondary Actor:** Union officer **System:** USU OS

A UO requests termination of their uni membership to USU. USU officer reviews, approves and processes the termination updating the system as needed. 

**Entry Conditions**
 
- Union Officer is logged in to the system
- USU Officer is logged in with termination approval permissions
- The union’s account is active in the USU OS

**Exit Conditions (on success)**

- Union’s account is deactivated
- Data of the union is scheduled for removal according to policy
- Notifications are sent to relevant people

**Main Flow**
| **Actor: Union Officer**                              | **Actor: USU Officer**                         | **System: USU OS**                                             |
| ----------------------------------------------------- | ---------------------------------------------- | -------------------------------------------------------------- |
| 1. Submits request for termination of USU membership. | —                                              | 2. Receives termination request.                               |
| —                                                     | 3. Reviews termination request and union data. | 4. Validates request against rules and policies.               |
| —                                                     | 5. Approves or rejects termination request.    | 6. If approved, marks union account as inactive.               |
| —                                                     | 7. Confirms completion to Union Officer.       | 8. Schedules data removal and disables all student access.     |
| —                                                     | 9. Monitors the removal process.               | 10. Sends notification to the union and internal logs updated. |

**Exceptional flows**

- data incomplete or there's pending events -> USU officer rejects request -> system notifies UO
- system error: system fails during process, log error -> notify USU officer 

</details>

<details>
<summary>UC-04: Initiation of New Event</summary>

## UC-04: Initiation of New Event

**Primary Actor:** USU officer **Secondary Actor:** Union officer **System:** USU OS

USU officer creates a new nationwide or regional even in USU OS then the system stores the evenet details, announces it on the portal, notifies UO's and students and opens the event participation endorsement.

**entry conditions:**

- USU officer is logged in with event creation permissions
- event data is ready for input

**exit conditions (On success)**

- event is successfully created in USU OS
- notifications sent to UO and student members
- even is open for subscription, registration and endorsement

**main flow**

| **Actor: USU Officer**                                                                                                 | **Actor: Union Officer**               | **System: USU OS**                                                                         |
| ---------------------------------------------------------------------------------------------------------------------- | -------------------------------------- | ------------------------------------------------------------------------------------------ |
| 1. Opens “Create New Event” form.                                                                                      | —                                      | 2. Displays blank event creation form with required fields.                                |
| 3. Fills in event details (name, theme, team, date/time, venue, plan, constraints, scope, promotion scope, materials). | —                                      | 4. Validates input fields and checks for conflicts (e.g., duplicate events, date clashes). |
| 5. Submits the event creation request.                                                                                 | —                                      | 6. Stores event data in the system database.                                               |
| —                                                                                                                      | 7. Receives notification of new event. | 8. Publishes the event on the USU portal.                                                  |
| —                                                                                                                      | —                                      | 9. Sends notifications to union officers.                                                  |
| —                                                                                                                      | —                                      | 10. Sends notifications to student members.                                                |
| —                                                                                                                      | —                                      | 11. Opens event for subscription, registration, and union endorsement.                     |
| 12. Confirms successful creation.                                                                                      | —                                      | 13. Displays success message and updated event status.                                     |

**Exceptional flows**

- incomplete data -> system alerts USU officer to fill required fields -> event creation paused
- event overlaps with another major even -> system tells officer -> USU officer decides to proceed or modify
- saving fails -> system logs error -> USU officer notified to retry later


</details>

<details>
<summary>UC-05: Event Announcements and Progress Updates</summary>

**Primary Actor:** USU officer **Secondary Actor:** Union officer, student members **System:** USU OS

USU officer makes announcement or posts progress updates on an existing event. The system publishes the update on USU portal and sends notifications to subscribed students and relevant UO's.

**entry conditions:**

- USU officer is logged in with event creation permissions
- Event has already been created and published in the system

**exit conditions (On success):**

- announcement or update is successfully posted
- notifications are delivered to all relevant users
- event page reflects the latest information

**main flow**

| **Actor: USU Officer**                     | **Actor: Union Officer**            | **Actor: Student Members**          | **System: USU OS**                                          |
| ------------------------------------------ | ----------------------------------- | ----------------------------------- | ----------------------------------------------------------- |
| 1. Selects an existing event to update.    | —                                   | —                                   | 2. Displays current event details and update options.       |
| 3. Enters announcement or progress update. | —                                   | —                                   | 4. Validates content for completeness and allowed format.   |
| 5. Submits the update.                     | —                                   | —                                   | 6. Publishes update on the USU portal.                      |
| —                                          | —                                   | 7. Receives notification of update. | 8. Pushes notifications to subscribed student members.      |
| —                                          | 9. Receives notification of update. | —                                   | 10. Logs the update for auditing and reference.             |
| 11. Confirms completion of update.         | —                                   | —                                   | 12. Displays confirmation message and updated event status. |

**exceptional flows**

- system detects empty fields or unsupported file types -> prompts USU officer to correct
- if notification fail the system retries automatically and logs failures
- event deleted or inactive -> USU officer notified -> cannot post event

</details>

<details>
<summary>UC-06: Student Participation in Events</summary>

**Primary Actor:** student member **Secondary Actor:** Union officer, USU Officer **System:** USU OS

A student member subscribes to receive updates about an event and/or registers to participate. System records student's participation and ensures notifications are delivered about updates.

**Entry Conditions:**

- student is registered with their university-specific student union
- event exists and is open for subscription/registration

**Exit conditions**

- student is subscribed to event notifs
- participation if registered is confirmed
- event status is updated with participant list

**main flow**

| **Actor: Student Member**                   | **Actor: Union Officer**                                        | **Actor: USU Officer** | **System: USU OS**                                                            |
| ------------------------------------------- | --------------------------------------------------------------- | ---------------------- | ----------------------------------------------------------------------------- |
| 1. Searches for an event of interest.       | —                                                               | —                      | 2. Displays list of available events with details (date, venue, scope).       |
| 3. Selects event to subscribe or register.  | —                                                               | —                      | 4. Confirms event is open for subscription/registration.                      |
| 5. Chooses to subscribe, register, or both. | —                                                               | —                      | 6. Records student subscription and/or registration in the system.            |
| —                                           | 7. Receives notification of student registration (if required). | —                      | 8. Sends confirmation to student and updates participant count.               |
| 9. Confirms completion of registration.     | —                                                               | —                      | 10. Displays success message and allows further actions (e.g., cancel, edit). |

**exceptional flows**

- event full -> registration fails -> system notifies student -> option to join waiting list is shown
- registration deadline passed -> system prevents registration -> notifies student
- invalid student data -> system validates student membership -> rejects if not valid member of union

</details>

<details>
<summary>UC-07:  Union’s Participation in Events</summary>

## UC-07: Union’s Participation in Events

**Primary Actor:** Union Officer **Secondary Actor:** USU officer **System:** USU OS

UO endorses a nationwide or regional event on behalf of their uni specific student union, signaling official support and participation. System records the endorsement and updates event's status.

**entry conditions**

- union officer logged in and has permission to endorse events
- event exists and is open for endorsement

**exit conditions**

- event endorsed by union
- event status updated in USU system to reflect union participation
- notifs sent to relevant USU officers and student members

**Main flow**

| **Actor: Union Officer**                           | **Actor: USU Officer**                         | **System: USU OS**                                                            |
| -------------------------------------------------- | ---------------------------------------------- | ----------------------------------------------------------------------------- |
| 1. Views list of events available for endorsement. | —                                              | 2. Displays event details, including scope, organizers, and participant info. |
| 3. Selects an event to endorse.                    | —                                              | 4. Confirms the event is eligible for endorsement.                            |
| 5. Clicks **Endorse Event**.                       | —                                              | 6. Validates union’s permission and records endorsement.                      |
| —                                                  | 7. Receives notification of union endorsement. | 8. Updates event status to show union participation.                          |
| 9. Confirms completion.                            | —                                              | 10. Displays success message and updated event status.                        |

**exceptional flows:**

- event closed for endorsement -> system prevents endorsement -> notifies UO
- insufficient permissions -> UO cannot endorse -> system displays error message
- event does not exist -> system validates event ID -> reject actions and notifies officer 

</details>
