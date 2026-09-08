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
<img width="1536" height="1024" alt="ChatGPT Image Aug 19, 2026, 01_42_21 PM" src="https://github.com/user-attachments/assets/870bcef4-e3cb-4b48-8f6d-db5b01a369b8" />




## Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|---|---|---|
| **Member** | **MemberID (PK)**, Name, MembershipType, StartDate | Stores registered gym members. |
| **Program** | **ProgramID (PK)**, ProgramName, Description, Duration | Fitness programs such as Yoga, Zumba, Weight Training. |
| **Trainer** | **TrainerID (PK)**, Name, Specialization, Phone | Trainers assigned to one or more programs. |
| **Member_Program** | **MemberID (PK, FK)**, **ProgramID (PK, FK)**, JoinDate | Associative entity for Member–Program relationship. |
| **Program_Trainer** | **ProgramID (PK, FK)**, **TrainerID (PK, FK)** | Associative entity for Program–Trainer relationship. |
| **Session_Booking** | **BookingID (PK)**, MemberID (FK), TrainerID (FK), SessionDate, SessionTime | Records personal training bookings. |
| **Attendance** | **AttendanceID (PK)**, BookingID (FK), AttendanceStatus | Stores attendance for each booked session. |
| **Payment** | **PaymentID (PK)**, MemberID (FK), BookingID (FK), Amount, PaymentDate, PaymentType | Records membership and session payments. |



## Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|---|---|---|---|
| Member **enrolls in** Program | M : N | Total (Member), Partial (Program) | A member can enroll in multiple programs; each program can have many members. |
| Program **assigned to** Trainer | M : N | Total (Program), Partial (Trainer) | A program may have multiple trainers; a trainer can teach multiple programs. |
| Member **books** Session_Booking | 1 : N | Total (Session_Booking), Partial (Member) | One member can book many personal training sessions. |
| Trainer **conducts** Session_Booking | 1 : N | Total (Session_Booking), Partial (Trainer) | One trainer can conduct many personal training sessions. |
| Session_Booking **has** Attendance | 1 : 1 | Total (Both) | Every booked session has one attendance record. |
| Member **makes** Payment | 1 : N | Total (Payment), Partial (Member) | A member can make multiple payments. |
| Session_Booking **may generate** Payment | 1 : 1 | Partial (Both) | A session payment can be linked to a booking when applicable. |



## Assumptions

- Every member has a unique **MemberID**.
- Every trainer has a unique **TrainerID**.
- Every fitness program has a unique **ProgramID**.
- Members can enroll in multiple fitness programs.
- A fitness program may have one or more trainers.
- Personal training sessions are booked by exactly one member with one trainer.
- Attendance is recorded for every booked session.
- Payments can be for either **Membership** or **Personal Training Session**.
- Membership types (Basic, Premium, Elite, etc.) are predefined.
- A booking cannot exist without both a valid member and a valid trainer.
- Only active members can enroll in programs and book training sessions.

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
<img width="1536" height="1024" alt="chat 2" src="https://github.com/user-attachments/assets/96fb7d0f-d41f-47c8-bc05-47a8e5cfcdcc" />




## Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|---|---|---|
| **Member** | **MemberID (PK)**, Name, Email, Phone, Address, JoinDate | Stores registered library members. |
| **Book** | **BookID (PK)**, Title, ISBN, PublishedYear | Stores books available in the library. |
| **Author** | **AuthorID (PK)**, AuthorName, Bio, Nationality | Stores authors and speakers associated with books and events. |
| **Category** | **CategoryID (PK)**, CategoryName, Description | Categorizes books such as Fiction, Science, History, etc. |
| **Loan** | **LoanID (PK)**, MemberID (FK), BookID (FK), LoanDate, DueDate, ReturnDate, Status | Records book borrowing and return details. |
| **Event** | **EventID (PK)**, EventName, EventDate, StartTime, EndTime, Description | Stores library cultural events. |
| **Event_Registration** | **MemberID (PK, FK)**, **EventID (PK, FK)**, RegistrationDate | Associative entity for Member–Event registration. |
| **Room** | **RoomID (PK)**, RoomName, Capacity, Location, RoomType | Stores rooms used for events and study. |
| **Loan_Fine** | **FineID (PK)**, LoanID (FK), FineDate, Amount, Reason | Stores overdue fines for late book returns. |



## Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|---|---|---|---|
| Member **borrows** Book | M : N | Partial (Member), Partial (Book) | A member can borrow multiple books; a book can be borrowed by many members over time. |
| Member **has** Loan | 1 : N | Total (Loan), Partial (Member) | A member can have multiple loan records. |
| Loan **is for** Book | N : 1 | Total (Loan), Partial (Book) | Each loan refers to one book; a book can have many loan records over time. |
| Book **written by** Author | M : N | Total (Book), Partial (Author) | A book can have multiple authors; an author can write multiple books. |
| Book **belongs to** Category | N : 1 | Total (Book), Partial (Category) | Each book belongs to one category; a category can contain many books. |
| Member **registers for** Event | M : N | Partial (Member), Total (Event) | Members can register for multiple events; an event can have multiple registered members. |
| Event **has** Author/Speaker | M : N | Total (Event), Partial (Author) | Each event has one or more speakers/authors; an author can participate in multiple events. |
| Event **held in** Room | N : 1 | Total (Event), Partial (Room) | Each event is held in one room; a room can host multiple events at different times. |
| Loan **generates** Loan_Fine | 1 : 1 | Partial (Loan), Total (Loan_Fine) | A late loan may generate one overdue fine. |


## Assumptions

- Every library member has a unique **MemberID**.
- Every book has a unique **BookID**.
- Every author has a unique **AuthorID**.
- Every category has a unique **CategoryID**.
- Every event has a unique **EventID**.
- Every room has a unique **RoomID**.
- A member can borrow multiple books.
- A book can be borrowed by different members over time.
- Each loan is associated with exactly one member and one book.
- A book may have multiple authors, and an author may write multiple books.
- Each book belongs to exactly one category.
- Members can register for multiple library events.
- Each event can have one or more speakers/authors.
- Each event is held in one room.
- A room can be used for multiple events or study sessions at different times.
- An overdue loan may generate a fine.
- A loan cannot exist without a valid member and a valid book.

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

<img width="1536" height="1024" alt="3" src="https://github.com/user-attachments/assets/876ac1b9-fe27-4375-aea3-f2edc89175d1" />

### Entities and Attributes



| Entity | Attributes (PK, FK) | Notes |
|---|---|---|
| **Restaurant** | **RestaurantID (PK)**, Name, Address, City, ContactNo, CuisineType | Stores restaurant details. |
| **Customer** | **CustomerID (PK)**, Name, Phone, Email | Stores registered customers. |
| **Reservation** | **ReservationID (PK)**, CustomerID (FK), TableID (FK), Date, Time, NumGuests | Records table reservations and walk-in bookings. |
| **Table** | **TableID (PK)**, TableNo, Capacity, Location | Stores restaurant table information. |
| **Order** | **OrderID (PK)**, ReservationID (FK), OrderDate, Status, TotalAmount | Records food orders linked to reservations. |
| **Dish** | **DishID (PK)**, DishName, Price, Description, CategoryID (FK) | Stores food items available for ordering. |
| **Category** | **CategoryID (PK)**, CategoryName, Description | Categorizes dishes such as Starter, Main Course, and Dessert. |
| **Order_Dish** | **OrderID (PK, FK)**, **DishID (PK, FK)**, Quantity | Associative entity connecting orders and dishes. |
| **Bill** | **BillID (PK)**, ReservationID (FK), FoodCharge, ServiceCharge, TotalAmount, PaymentStatus | Stores billing information for each reservation. |
| **Waiter** | **WaiterID (PK)**, Name, Phone, Shift | Stores restaurant waiter details. |
| **Reservation_Waiter** | **ReservationID (PK, FK)**, **WaiterID (PK, FK)** | Associative entity for assigning waiters to reservations. |



## Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|---|---|---|---|
| Customer **makes** Reservation | 1 : N | Total (Reservation), Partial (Customer) | A customer can make multiple reservations; each reservation belongs to one customer. |
| Reservation **reserves** Table | N : 1 | Total (Reservation), Partial (Table) | Each reservation is for one table; a table can be reserved many times over different dates/times. |
| Reservation **generates** Order | 1 : N | Partial (Reservation), Total (Order) | A reservation can have multiple food orders. |
| Order **contains** Dish | M : N | Total (Order), Partial (Dish) | Each order can contain multiple dishes; a dish can appear in many orders. |
| Dish **belongs to** Category | N : 1 | Total (Dish), Partial (Category) | Each dish belongs to one category; a category can contain many dishes. |
| Reservation **assigned to** Waiter | N : 1 | Total (Reservation), Partial (Waiter) | A reservation is served by an assigned waiter; a waiter can serve multiple reservations. |
| Reservation **generates** Bill | 1 : 1 | Total (Bill), Partial (Reservation) | Each completed reservation generates one bill containing food and service charges. |
| Restaurant **has** Reservation | 1 : N | Total (Reservation), Total (Restaurant) | A restaurant can manage many reservations. |
| Reservation **has** Guest | 1 : N | Partial (Reservation), Total (Guest) | A reservation can include one or more guests. |




## Assumptions

- Every restaurant has a unique **RestaurantID**.
- Every customer has a unique **CustomerID**.
- Every reservation has a unique **ReservationID**.
- Every table has a unique **TableID**.
- Every order has a unique **OrderID**.
- Every dish has a unique **DishID**.
- Every category has a unique **CategoryID**.
- Every bill has a unique **BillID**.
- Every waiter has a unique **WaiterID**.
- A customer can make multiple reservations.
- Each reservation is associated with exactly one customer and one table.
- A table can be reserved multiple times at different dates or times.
- A reservation may contain one or more food orders.
- Each order can contain multiple dishes.
- A dish can appear in multiple orders.
- Each dish belongs to exactly one category.
- A waiter can serve multiple reservations.
- Each reservation may be assigned to a waiter.
- A bill is generated for a reservation and includes food and service charges.
- A reservation may be associated with one bill.
- Walk-in customers can be recorded as reservations without advance booking.
## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
