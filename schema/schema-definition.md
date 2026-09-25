# Schema Definition

**Task 1.1: all five relation schemas, their attributes, domains, and primary keys.**

**5 Relation schemas for Paw Airline Booking Database:**
- passengers
- flights
- bookings
- airports
- flight_routes


**Attributes, domains, primary keys(PK) and foreign keys(FK) in each schema are listed below:**

# Airline Reservation Database ERD

```mermaid
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

-Add Check & constrain
-Submit 2 SS
-Update mermaid PNG
-MD. Reasoning