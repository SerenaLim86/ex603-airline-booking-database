# EX603 Assignment - Paw Airline Booking Database

**Summary:**

Airline Booking database for our new airline company Paw Air. This databsase will store date for passengers, flights, bookings, airports, flight_routes information. 

**Domain:** 

The main purpose of this database is to store and allow processing of the airline flight, passenger and booking information. The database is mainly use for tracking and recording all the online bookings in the official airline site, but not third party or in person bookings. Users for this table will be internal staffs in the company, such as IT, production support, customer services, business development, marketing, machine learning and also enterprise data stragety. This table enable analysis, reporting and triaging system issue in production and provide real time data from request. 


**Schema：**

Below are the five roles for the Paw Airline Booking database and our design decisions. Each role is created into each own seperate table.

actor - passengers
producer - flights
event - bookings
catalog - airports
junction - flight_routes

**Design decisions**
passengers:

flights:

bookings:

airports:

flight_routes:


**Paw Airline Booking ERD:**

>airline-booking ERD using mermaid diagram

```mermaid
%%{init: {'theme': 'redux-color', 'look': 'classic'}}%%
erDiagram

    AIRPORTS {
        VARCHAR airport_id PK
        VARCHAR airport_name UK
        VARCHAR airport_code UK
        VARCHAR airport_city
        VARCHAR airport_country
        VARCHAR airport_status
    }

    PASSENGER {
        VARCHAR passenger_id PK
        VARCHAR passenger_username UK
        VARCHAR passenger_first_name
        VARCHAR passenger_middle_name
        VARCHAR passenger_last_name
        DATE passenger_DOB
        VARCHAR passenger_email UK
        VARCHAR passenger_phone
        DATE passenger_enroll_date
        VARCHAR passenger_loyalty_id UK
        VARCHAR passenger_address_street
        VARCHAR passenger_address_city
        VARCHAR passenger_address_state
        VARCHAR passenger_address_country
    }

    FLIGHT_ROUTES {
        INT route_id PK
        VARCHAR departure_airport_id FK
        VARCHAR arrival_airport_id FK
        INT route_distance
        INT estimated_duration
        VARCHAR route_status
    }

    FLIGHTS {
        VARCHAR flight_id PK
        INT route_id FK
        VARCHAR flight_number
        TIMESTAMP departure_date
        TIMESTAMP arrival_date
        VARCHAR departure_status
        VARCHAR arrival_status
    }

    BOOKINGS {
        INT booking_id PK
        VARCHAR passenger_id FK
        VARCHAR flight_id FK
        VARCHAR booking_status
        TIMESTAMP booking_date
        NUMERIC fare_price
    }

    AIRPORTS ||--o{ FLIGHT_ROUTES : "departure"
    AIRPORTS ||--o{ FLIGHT_ROUTES : "arrival"
    FLIGHT_ROUTES ||--o{ FLIGHTS : "own"
    PASSENGER ||--o{ BOOKINGS : "makes"
    FLIGHTS ||--o{ BOOKINGS : "has"
```

4. Query catalogue — per unit, a short table listing the queries and the business question each answers, linked to the .sql files.

5. Technical highlights — three to five things a reader should notice:
    - Flight and airports information are closely related to each other and likey be use together to perform join for flight information 
    - 
    - 

6. What I would do differently?

    I would look more into other possible attribute and see example airline site for references. I would also look into other possible issue and difficulties when this table is used by different audience or users. 

7. Video presentation — embed or link the video.

8. How to run it — the commands to create the schema and execute a query. Assume the reader has a database and nothing else.