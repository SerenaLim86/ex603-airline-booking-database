# Schema Definition

**Task 1.1: all five relation schemas, their attributes, domains, and primary keys.**

**5 Relation schemas for Paw Airline Booking Database:**
- passengers
- flights
- bookings
- airports
- flight_routes


**Attributes, domains, primary keys(PK) and foreign keys(FK) in each schema are listed below:**

```mermaid
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
