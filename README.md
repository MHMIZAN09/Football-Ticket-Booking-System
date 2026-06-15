## Question 1: What role does a Foreign Key play in the Bookings table, and how does it safeguard against entering a ticket sale for a match that doesn't exist?

A foreign key is used to connect one table with another table. In the Bookings table, user_id connects a booking to the Users table, and match_id connects a booking to the Matches table.

It protects the database from invalid data. For example, if someone tries to insert a booking for a match that does not exist in the Matches table, the database will reject that booking. So, foreign keys maintain referential integrity and make sure every booking belongs to a valid user and a valid match.

## Question 2: Why are we unable to use an aggregate function like COUNT(booking_id) inside a standard WHERE clause to filter match rows? How does HAVING solve this?
We cannot use aggregate functions like COUNT(), AVG(), or SUM() directly inside a normal WHERE clause because WHERE filters rows before grouping happens.

Aggregate functions work after GROUP BY. So, when we need to filter grouped results, we use HAVING.

### Example:
``` sql
SELECT match_id, COUNT(booking_id)
FROM Bookings
GROUP BY match_id
HAVING COUNT(booking_id) > 2;
```
Here, first the bookings are grouped by match_id, then the number of bookings is counted, and finally HAVING filters the result.


### Question 3: If a Primary Key column guarantees that all row entries are completely unique, why does the database system also explicitly forbid it from containing a NULL value?
A primary key is used to uniquely identify each row in a table. If a primary key contains NULL, then the database cannot properly identify that row.

NULL means unknown or missing value. Since every row must have a clear identity, the primary key cannot be missing. That is why a primary key must be both unique and not null.


# ERD Link (Public): https://drive.google.com/file/d/1xPVtpwkRqe9MgVSXEXCSEjBCEjBiT86V/view?usp=sharing
# GitHub Repository Link (Public):
# Interview Video Link (Public): 
