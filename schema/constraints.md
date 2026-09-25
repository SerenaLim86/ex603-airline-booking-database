# Constraints
**Task 1.3: every constraint with its justification, including each ON DELETE choice.**

The constraints table:

|FK| ON DELETE   | reason |
| --- | --- | --- |
|departure_airport_id| DELETE SET NULL  | maintain data |
|arrival_airport_id| DELETE SET NULL  | maintain data |
|route_id| DELETE SET NULL  | maintain data |
|passenger_id| DELETE CASCADE  | remove and archive to del table |
|flight_id| DELETE SET NULL  | maintain data |

- Almost all of the attributes in the tables are set to NOT NULL since most are required field in the database.
 - FK like flight_id referece attribute in other tables are set DELETE on NULL because we wanted to maintain the other data even they are removed. If we need to access the other information with a joint, we cn still access. Another consideration is to keep history records.
 -  passenger_id is set to on DELETE CASCADE because it is better to create a history table in the future for archieved member than setting a member to NULL. Keeping it as NULL with other active record will be wasting space in these tables and become messy overtime.

 The CHECK constraints:

 - Some fields required a standardize format like email
 - Selections like flight status are desgned to have a CHECK to allow only the listed values for entry. (ex. 'Confirmed', 'Cancelled', 'Pending')

 **For each schema below, listed their constraint and ON DELETE command.**

PASSENGERS: 
    
    CHECK (passenger_email ~ '^[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,}$'),

BOOKINGS:
    
    CHECK (booking_status IN ('Confirmed', 'Cancelled', 'Pending'))
    
    FOREIGN KEY (passenger_id) REFERENCES passenger(passenger_id) ON DELETE CASCADE,
   
    FOREIGN KEY (flight_id) REFERENCES flights(flight_id) ON DELETE SET NULL
   
FLIGHTS:
    
    CHECK (departure_status IN ('Scheduled', 'Cancelled', 'Delayed', 'Early'))
    
    CHECK (arrival_status IN ('Scheduled', 'Cancelled', 'Delayed', 'Early'))
       
AIRPORTS:
    
    CHECK (airport_status IN ('Operate', 'Closed'))
    
FLIGHT_ROUTES:
   
    CHECK (route_status IN ('Active', 'Pending', 'Suspected'))
    
    FOREIGN KEY (departure_airport_id) REFERENCES airports(airport_id) ON DELETE SET NULL

    FOREIGN KEY (arrival_airport_id) REFERENCES airports(airport_id) ON DELETE SET NULL

    CHECK (departure_airport_id <> arrival_airport_id)


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