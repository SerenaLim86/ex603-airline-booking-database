# EX603 Assignment - Paw Airline Booking Database

**Summary:**

Airline Booking database for our new airline company Paw Air. This databsase will store date for passengers, flights, bookings, airports, flight_routes information. 

**Domain:** 

The main purpose of this database is to store and allow processing of the airline flight, passenger and booking information. The database is mainly use for tracking and recording all the online bookings in the official airline site, but not third party or in person bookings. Users for this table will be internal staffs in the company, such as IT, production support, customer services, business development, marketing, machine learning and also enterprise data stragety. This table enable analysis, reporting and triaging system issue in production and provide real time data from request. 


**Schema：**

Below are the five roles for the Paw Airline Booking database and our design decisions.
actor - passengers
producer - flights
event - bookings
catalog - airports
junction - flight_routes

**Paw Airline Booking ERD:**

>airline-booking ERD using mermaid diagram

```mermaid
%%{init: {'theme': 'redux-color'}}%%
erDiagram

    PASSENGERS {
        INT passenger_id PK
        VARCHAR passenger_username FK
        VARCHAR passenger_first_name
        VARCHAR passenger_middle_name
        VARCHAR passenger_last_name
        VARCHAR passenger_email
        VARCHAR passenger_phone
        VARCHAR passenger_address_street
        VARCHAR passenger_address_city
        VARCHAR passenger_address_state
        DATE passenger_DOB
        DATE passenger_enroll_date
        INT booking_id FK
    }

    BOOKINGS {
        INT booking_id PK
        INT booking_status
        DATE booking_date
        TIMESTAMP booking_time
        INT flight_id FK
        FLOAT fare_price
    }

    FLIGHTS {
        INT flight_id PK
        INT booking_id FK
        INT flight_type
        DATE depart_date
        TIMESTAMP depart_time
        DATE arrive_date
        TIMESTAMP arrive_time
    }

    AIRPORTS {
        VARCHAR depart_destination
        VARCHAR depart_destination_city
        VARCHAR depart_destination_country
        VARCHAR depart_destination_status
        VARCHAR arrive_destination
        VARCHAR arrive_destination_city
        VARCHAR arrive_destination_country
        VARCHAR arrive_destination_status
        INT flight_id FK
        VARCHAR flight_depart_status
        VARCHAR flight_arrive_status
    }

    FLIGHT_ROUTES {
        INT booking_id PK
        INT booking_status
        DATE depart_date
        TIMESTAMP depart_time
        DATE arrive_date
        TIMESTAMP arrive_time
        INT flight_id FK
        INT fare_price
    }

    PASSENGERS ||--o{ BOOKINGS : "owns"
    PASSENGERS ||--o{ FLIGHTS : "owns"
    FLIGHTS ||--o{ AIRPORTS : "uses"
    FLIGHTS ||--o{ FLIGHT_ROUTES : "routes"
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