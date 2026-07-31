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
<img width="822" height="848" alt="image" src="https://github.com/user-attachments/assets/ed3fc78c-d011-4075-a906-9cfb78ffc6eb" />


### Entities and Attributes
### Entities and Attributes

| Entity  | Attributes (PK, FK)                                            | Notes                      |
|---------|------------------------------------------------------------------|----------------------------|
| Member  | MemberID (PK), Name, Phone, Email                               | Library member             |
| Book    | BookID (PK), Title, Author, Category                            | Books in the library       |
| Loan    | LoanID (PK), LoanDate, ReturnDate, MemberID (FK), BookID (FK)   | Tracks borrowed books      |
| Event   | EventID (PK), EventName, EventDate                              | Library events             |
| Speaker | SpeakerID (PK), SpeakerName                                     | Event speaker/author       |
| Room    | RoomID (PK), RoomName, Capacity                                 | Event and study rooms      |
| Fine    | FineID (PK), Amount, LoanID (FK), MemberID (FK)                 | Overdue fine information   |


### Relationships and Constraints

### Relationships and Constraints

| Relationship            | Cardinality | Participation | Notes                                   |
|-------------------------|-------------|---------------|-----------------------------------------|
| Member borrows Book     | M:N         | Total         | Implemented through Loan                |
| Member registers Event  | M:N         | Partial       | Members may join multiple events        |
| Event has Speaker       | M:N         | Total         | Each event has one or more speakers     |
| Event uses Room         | M:1         | Total         | One room is assigned per event          |
| Loan generates Fine     | 1:0..1      | Partial       | Fine only for overdue returns           |
| Member pays Fine        | 1:M         | Partial       | A member may have multiple fines        |

### Assumptions

- A member can borrow multiple books.
- A book can be borrowed by only one member at a time.
- A loan records both loan and return dates.
- A fine is generated only for overdue returns.
- Members can register for multiple events.
- An event may have multiple speakers.
- Each event is conducted in one room.

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
<img width="1305" height="692" alt="image" src="https://github.com/user-attachments/assets/6e90beb3-2112-4dbe-88dd-3b5aee1d4234" />


### Entities and Attributes

| Entity  | Attributes (PK, FK)                                   | Notes                        |
|---------|--------------------------------------------------------|------------------------------|
| Member  | MemberID (PK), Name, Phone, Email                      | Library member               |
| Book    | BookID (PK), Title, Author, Category                   | Books available in library   |
| Loan    | LoanID (PK), LoanDate, ReturnDate, MemberID (FK), BookID (FK) | Tracks borrowed books |
| Event   | EventID (PK), EventName, EventDate                     | Library cultural events      |
| Speaker | SpeakerID (PK), SpeakerName                            | Event speakers/authors       |
| Room    | RoomID (PK), RoomName, Capacity                        | Rooms for events and study   |
| Fine    | FineID (PK), Amount, LoanID (FK), MemberID (FK)        | Overdue fine details         |

### Relationships and Constraints

| Relationship           | Cardinality   | Participation | Notes                                    |
|------------------------|---------------|---------------|------------------------------------------|
| Member borrows Book    | M:N (via Loan)| Total         | Loan stores loan and return dates        |
| Member registers Event | M:N           | Partial       | Members may register for multiple events |
| Event has Speaker      | M:N           | Total         | Each event has one or more speakers      |
| Event uses Room        | M:1           | Total         | One room is assigned per event           |
| Loan generates Fine    | 1:0..1        | Partial       | Fine generated only for overdue loans    |
| Member pays Fine       | 1:M           | Partial       | Member may have multiple fines           |

### Assumptions
- A member can borrow multiple books.
- A book can be borrowed multiple times but only by one member at a time.
- Each loan records both loan date and return date.
- Overdue loans generate fines.
- Members can register for multiple events.
- An event can have one or more speakers.
- One room is allocated for one event at a given time.

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
<img width="1057" height="586" alt="image" src="https://github.com/user-attachments/assets/ff45ff0c-f8de-46f5-81f8-053eaafaadc7" />

### Entities and Attributes

| Entity      | Attributes (PK, FK)                                           | Notes                           |
|-------------|---------------------------------------------------------------|---------------------------------|
| Customer    | CustomerID (PK), Name, Phone                                 | Restaurant customer             |
| Reservation | ReservationID (PK), Date, Time, Guests, CustomerID (FK)      | Table reservation               |
| Table       | TableID (PK), TableNo, Capacity                              | Dining table                    |
| Order       | OrderID (PK), ReservationID (FK)                             | Food order                      |
| Dish        | DishID (PK), DishName, Price, CategoryID (FK)                | Menu item                       |
| Category    | CategoryID (PK), CategoryName                                | Starter, Main, Dessert          |
| Bill        | BillID (PK), FoodCharge, ServiceCharge, TotalAmount, ReservationID (FK) | Reservation bill     |
| Waiter      | WaiterID (PK), WaiterName                                    | Restaurant staff                |

### Relationships and Constraints
| Relationship               | Cardinality | Participation | Notes                                   |
|----------------------------|-------------|---------------|-----------------------------------------|
| Customer reserves Reservation | 1:M      | Total         | Customer may reserve many tables        |
| Reservation assigned Table | M:1         | Total         | One table per reservation               |
| Reservation places Order   | 1:M         | Total         | One reservation can have many orders    |
| Order contains Dish        | M:N         | Total         | Each order contains multiple dishes     |
| Dish belongs Category      | M:1         | Total         | Each dish belongs to one category       |
| Reservation generates Bill | 1:1         | Total         | One bill per reservation                |
| Waiter serves Reservation  | 1:M         | Total         | One waiter serves many reservations     |

### Assumptions

- Customers can reserve a table or walk in.
- Each reservation is assigned one table.
- A reservation may contain multiple food orders.
- Each dish belongs to one category.
- One bill is generated for each reservation.
- One waiter can serve multiple reservations.


## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
