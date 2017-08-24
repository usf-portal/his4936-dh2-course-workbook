# Examples

## Model Sketch

```
Sample of Historical Modeling... A Corpus of Letters Between Early U.S. Diplomats

MOST COMMON SQL FIELD TYPES

# INTEGER - Used for storing whole numbers, including ID numbers
# DOUBLE - Used for non-whole numbers (including geographical coordinates)
# BOOLEAN - Used for all true/false values
# VARCHAR - Used for MOST short strings, used for small bits of text, like descriptive labels
# CHAR - Used for storing a single character only
# LONGTEXT - Used rarely, only when you expect to store large chunks of text, like an entire letter

Person:
    id = INTEGER (Primary Key)
    first_name = VARCHAR
    middle_name = VARCHAR
    last_name = VARCHAR
    sex = VARCHAR
    origin = VARCHAR
    birth_date = DATETIME
    death_date = DATETIME
    notes = LONGTEXT

Address:
    id = INTEGER (Primary Key)
    street = VARCHAR
    street_2 = VARCHAR
    city = VARCHAR
    state_province = VARCHAR
    country = VARCHAR
    notes = LONGTEXT

Organization:
    id = INTEGER (Primary Key)
    name = VARCHAR
    origin = VARCHAR
    address = INTEGER (Foreign Key, Address)
    notes = LONGTEXT

Occupation:
    id = INTEGER (Primary Key)
    name = VARCHAR
    organization = INTEGER (Foreign Key, Organization)
    notes = LONGTEXT

Letter:
    id = INTEGER (Primary Key)
    title = VARCHAR
    address = INTEGER (Foreign Key, Address)
    from_person_id = INTEGER (Foreign Key, Person)
    to_person_id = INTEGER (Foreign Key, Person)
    sent = DATETIME
    received = DATETIME
    content = LONGTEXT
    notes = LONGTEXT

PersonOccupation:
    person_id = INTEGER (Foreign Key, Person)
    occupation_id = INTEGER (Foreign Key, Occupation)
    start_date = DATETIME
    end_Date = DATETIME
    notes = LONGTEXT

```
