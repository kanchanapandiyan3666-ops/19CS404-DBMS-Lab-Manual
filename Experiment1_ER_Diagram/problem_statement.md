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
<img width="972" height="613" alt="Screenshot 2026-09-11 205800" src="https://github.com/user-attachments/assets/1eb928bb-31bc-4d7b-8e04-304a8ca87e18" />

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|Member|	Member_ID (PK), Name, Membership_Type, Start_Date, Phone, Email|	Stores member registration details.|
|Program|	Program_ID (PK), Program_Name, Category, Duration, Schedule	|Stores fitness program details such as Yoga, Zumba, etc.|
|Trainer|	Trainer_ID (PK), Trainer_Name, Specialization, Phone, Email	|Stores trainer details and specialization.|
|Session|	Session_ID (PK), Session_Date, Session_Time|	Stores personal training session information.|
|Attendance	|Attendance_ID (PK), Status, Remarks|	Records attendance for each training session.|
|Payment|	Payment_ID (PK), Amount, Payment_Date|	Stores payment details made by members.|

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|Member — Joins — Program	|M:N|	Partial	|A member can join multiple programs, and a program can have multiple members.|
|Program — Assigned_to — Trainer|	M:N |Partial|	A program can have multiple trainers, and a trainer can be assigned to multiple programs.|
|Member — Books — Session	|1:M|	Partial|	A member can book multiple sessions, while each session is booked by one member.|
|Trainer — Conducts — Session|	1:M	|Partial|	A trainer can conduct multiple sessions, while each session is conducted by one trainer.|
|Session — Has — Attendance	|1:1|	Total (Session)	|Each session has an attendance record.|
|Member — Makes — Payment|	1:M	|Partial|	A member can make multiple payments, and each payment belongs to one member.|

### Assumptions
-Each member, program, trainer, session, attendance record, and payment has a unique ID.

-A member can join multiple fitness programs, and a program can have multiple members.

-A program can have multiple trainers, and a trainer can be assigned to multiple programs.

-Each personal training session is associated with one member and one trainer.

-Attendance is recorded for each session.

-Payments are made only by registered members.

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
<img width="993" height="592" alt="Screenshot 2026-09-11 205819" src="https://github.com/user-attachments/assets/d38d84f7-8153-480b-9b3c-94814be9d19d" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|Reports|	User_ID (FK), Reg_No, Book_No, Issue_Return	|Stores book issue and return report details.|
|Staff	|Staff_ID (PK), Name|	Stores staff information.|
|Authentication| System	Login_ID (PK), Password	|Stores login and authentication details.|
|Readers|	User_ID (PK), FirstName, LastName, Name, Email, Phone_No, Address	|Stores reader/member details.|
|Books	|Book_No (PK), ISBN, Title, Author_No, Category, Edition	|Stores book information.|
|Publisher|	Publisher_ID (PK), Name, Year_Of_Publication|	Stores publisher details.|

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|Reports| — Manages — Staff|	N:1	|Partial|	Multiple reports can be managed by one staff member.|
|Staff| — Login — Authentication System|	N:1|	Partial|	Multiple staff members can use the authentication system.|
|Staff |— Keeps Track Of — Readers|	M:N|	Partial|	Staff can keep track of multiple readers, and readers can be managed by multiple staff members.|
|Staff |— Maintain — Books	|1:N|	Partial|	One staff member can maintain multiple books.|
|Publisher| — Published By — Books|	1:N	|Partial|	One publisher can publish multiple books, while each book is associated with a publisher.|
|Readers |— Reserve/Return Date — Books|	1:N|	Partial|	A reader can reserve/return multiple books. The relationship stores ReserveDate, Due_Date, and Return_Date.|
### Assumptions
-Each Staff member has a unique Staff_ID.

-Each Reader has a unique User_ID.

-Each Book has a unique Book_No.

-Each Publisher has a unique Publisher_ID.

-A staff member can manage multiple reports.

-Staff members can maintain multiple books and keep track of readers.

-A publisher can publish multiple books, while each book belongs to one publisher.

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
<img width="1007" height="608" alt="Screenshot 2026-09-11 205652" src="https://github.com/user-attachments/assets/a961dc4a-32fe-4b9d-93b3-2d1eb8113f49" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|Customer	|C_ID (PK), Name, Email, Phone, Address|	Stores customer details.|
|Reservation|	R_ID (PK), C_ID (FK), ID (FK), Date	|Stores reservation details made by customers.|
|Restaurant|	ID (PK), Name, Location	|Stores restaurant information.|
|Order| O_ID (PK), C_ID (FK), ID (FK), Amount, Date|	Stores customer order details.|
|Menu Item|	M_ID (PK), R_ID (FK), Name, Price, Description|	Stores menu items offered by restaurants.|
|Delivery	|D_ID (PK), O_ID (FK), Date, Status|	Stores delivery details for orders.|
### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|Customer — Have — Reservation|	1:M	|Partial|	A customer can make multiple reservations, while each reservation belongs to one customer.|
|Restaurant — Have — Reservation|	1:M|	Partial|	A restaurant can have multiple reservations, while each reservation is for one restaurant.|
|Customer — Place — Order	|1:M	|Partial	|A customer can place multiple orders, while each order belongs to one customer.|
|Restaurant — Receive — Order|	1:M	|Partial|	A restaurant can receive multiple orders, while each order is received by one restaurant.|
|Restaurant — Offers — Menu Item|	1:M	|Total (Menu Item)|A restaurant can offer multiple menu items, while each menu item belongs to one restaurant.|

### Assumptions
-A customer can make multiple reservations.

-A customer can place multiple orders.

-A restaurant can receive multiple orders and reservations.

-A restaurant can offer multiple menu items.

-Each menu item belongs to one restaurant.

-An order may have one associated delivery.



---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
