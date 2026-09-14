# Constraints
**Task 1.3: every constraint with its justification, including each ON DELETE choice.**

**For each schema below, listed their constraint and ON DELETE behavior.**

PASSENGERS: 
    VARCHAR passenger_username FK, INT booking_id FK

BOOKINGS:
    INT flight_id FK
   
FLIGHTS:
    INT booking_id FK
       
AIRPORTS:
    INT flight_id FK
    
FLIGHT_ROUTES:
    INT flight_id FK

>**Note:** booking_id and flight_id are FK in both PASSENGERS and FLIGHT_ROUTES schemas

|Attribute| Domain Values  | Constraints |
| --- | --- | --- |
| passenger_username| Variable length up to 10 characters; cannot be blank; no duplicates | NOT NULL, UNIQUE |
| booking_id| Integers, up to 10; cannot be blank; no duplicates | NOT NULL, UNIQUE | 
| flight_id| Integers, up to 5; cannot be blank; no duplicates | NOT NULL, UNIQUE | 
| passenger_email| Variable length up to 50 characters; cannot be blank; no duplicates, must have @ in email| NOT NULL, UNIQUE |
| passenger_phone| Integers, up to 10; cannot be blank; no duplicates | NOT NULL, UNIQUE | 


**ON DELETE Behavior:**

If passenger_username is deleted from user account due to inactivity or user. staff manual delete, it will set as NULL, passenger_id and other information will still remain for this user history record. 