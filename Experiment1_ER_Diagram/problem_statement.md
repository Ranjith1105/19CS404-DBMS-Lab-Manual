# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**  
- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram:
*Paste or attach your diagram here*  
![ER Diagram](https://github.com/user-attachments/assets/ece76bb2-0f81-4665-bd6c-d45658e53f3c)

### Entities and Attributes
| Entity           | Attributes (PK, FK)                                      | Notes                                          |
| ---------------- | -------------------------------------------------------- | ---------------------------------------------- |
| Member           | MemberID (PK), Name, MembershipType, StartDate           | Each member is uniquely identified by MemberID |
| Program          | ProgramID (PK), ProgramName (Yoga/Zumba/etc)             | Multiple members & trainers can be linked      |
| Trainer          | TrainerID (PK), TrainerName, Specialization              | Can handle multiple programs                   |
| Session          | SessionID (PK), Date, Time, ProgramID (FK)               | Represents each class/training session         |
| Attendance       | AttendanceID (PK), SessionID (FK), MemberID (FK), Status | Tracks participation                           |
| Payment          | PaymentID (PK), MemberID (FK), Amount, Date, PaymentType | Covers membership + session fees               |
| PersonalTraining | PTID (PK), MemberID (FK), TrainerID (FK), Date, Time     | Tracks one-to-one training                     |

### Relationships and Constraints

| Relationship              | Cardinality | Participation | Notes                                                       |
| ------------------------- | ----------- | ------------- | ----------------------------------------------------------- |
| Member – Program          | M:N         | Partial       | A member can join many programs; a program has many members |
| Program – Trainer         | M:N         | Mandatory     | Trainers assigned to multiple programs                      |
| Member – PersonalTraining | M:N         | Optional      | Not all members book PT                                     |
| Session – Program         | M:1         | Mandatory     | Each session belongs to a program                           |
| Member – Attendance       | M:N         | Mandatory     | Members attending sessions                                  |
| Member – Payment          | 1:M         | Mandatory     | A member can make many payments                             |


### Assumptions
Assumptions

One membership type per member.

A program must have at least one trainer.

Personal training is optional and billed separately.

Attendance is recorded only when members participate.

---

# Scenario B: City Library Event & Book Lending System

**Business Context:**  
The Central Library wants to manage book lending and cultural events.

**Requirements:**  
- Members borrow books, with loan and return dates tracked.  
- Each book has title, author, and category.  
- Library organizes events; members can register.  
- Each event has one or more speakers/authors.  
- Rooms are booked for events and study.  
- Overdue fines apply for late returns.

### ER Diagram:
*Paste or attach your diagram here*  
![ER Diagram2](https://github.com/user-attachments/assets/128778b9-3147-4d3d-9144-eb392b907340)

### Entities and Attributes

| Entity  | Attributes (PK, FK)                                                 | Notes                    |
| ------- | ------------------------------------------------------------------- | ------------------------ |
| Member  | MemberID (PK), Name, JoinDate                                       | Library user             |
| Book    | BookID (PK), Title, Author, Category                                | Each book unique         |
| Loan    | LoanID (PK), MemberID (FK), BookID (FK), LoanDate, ReturnDate, Fine | Tracks borrowing         |
| Event   | EventID (PK), EventName, EventDate                                  | Cultural events          |
| Speaker | SpeakerID (PK), Name, Expertise                                     | Authors/speakers invited |
| Room    | RoomID (PK), RoomName, Capacity                                     | Used for events/study    |


### Relationships and Constraints

| Relationship         | Cardinality | Participation | Notes                       |
| -------------------- | ----------- | ------------- | --------------------------- |
| Member – Book (Loan) | M:N         | Mandatory     | Members borrow many books   |
| Loan – Fine          | 1:1         | Optional      | Fine applies if late        |
| Event – Member       | M:N         | Optional      | Members register for events |
| Event – Speaker      | M:N         | Mandatory     | Each event has ≥1 speaker   |
| Event – Room         | M:1         | Mandatory     | Each event held in a room   |

### Assumptions
Each book has only one copy in the database (copies could be modeled separately if needed).

Fines are tracked as part of loan record.

Members may or may not attend events.

Each event takes place in exactly one room.

---

# Scenario C: Restaurant Table Reservation & Ordering

**Business Context:**  
A popular restaurant wants to manage reservations, orders, and billing.

**Requirements:**  
- Customers can reserve tables or walk in.  
- Each reservation includes date, time, and number of guests.  
- Customers place food orders linked to reservations.  
- Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).  
- Bills generated per reservation, including food and service charges.  
- Waiters assigned to serve reservations.

### ER Diagram:
*Paste or attach your diagram here*  
![Untitled Diagram](https://github.com/user-attachments/assets/226c37ae-112d-4f6c-be93-ac7d8e93231e)

### Entities and Attributes

| Entity      | Attributes (PK, FK)                                               | Notes                                      |
| ----------- | ----------------------------------------------------------------- | ------------------------------------------ |
| Customer    | CustomerID (PK), Name, Contact                                    | Walk-in or reserved                        |
| Reservation | ResID (PK), CustomerID (FK), Date, Time, NoOfGuests, TableID (FK) | One reservation per table                  |
| Table       | TableID (PK), Capacity                                            | Assigned per reservation                   |
| Order       | OrderID (PK), ResID (FK), OrderTime                               | Each reservation can place multiple orders |
| Dish        | DishID (PK), DishName, Category (Starter/Main/Dessert), Price     | Menu items                                 |
| OrderDetail | OrderDetailID (PK), OrderID (FK), DishID (FK), Quantity           | Junction table                             |
| Bill        | BillID (PK), ResID (FK), TotalAmount, ServiceCharge               | One bill per reservation                   |
| Waiter      | WaiterID (PK), Name                                               | Assigned to serve reservations             |

### Relationships and Constraints

| Relationship           | Cardinality | Participation | Notes                                   |
| ---------------------- | ----------- | ------------- | --------------------------------------- |
| Customer – Reservation | 1:M         | Optional      | Customer can make multiple reservations |
| Reservation – Table    | 1:1         | Mandatory     | Each reservation linked to one table    |
| Reservation – Order    | 1:M         | Mandatory     | Reservation can have many orders        |
| Order – Dish           | M:N         | Mandatory     | Orders include multiple dishes          |
| Reservation – Bill     | 1:1         | Mandatory     | One bill per reservation                |
| Reservation – Waiter   | M:1         | Mandatory     | Each reservation assigned to one waiter |

### Assumptions
Walk-in customers treated as reservations without advance booking.

One waiter handles a reservation at a time.

Service charge fixed per bill.

Dish categories are predefined (starter, main, dessert).
---
