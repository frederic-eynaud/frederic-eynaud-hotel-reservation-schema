# Hotel Reservation Schema Data Structure

## Guest data

### phone table

* phone_id Primary Key, Identity
* phone_number_id Required, Extended Character Set, Length: 10

### address table

* address_id Primary Key, Identity
* street_address Required, Extended Character Set, Length: 30
* city Required, Extended Character Set, Length: 20
* state Required, Standard Character Set, Length: 2
* zip Required, Standard Character Set, Length: 5

### guest table

* guest_id Primary Key, Identity
* first_name Required, Extended Character Set, Length: 30
* last_name Required, Extended Character Set, Length: 30
* phone_id Foreign Key, phone Table, Required
* address_id Foreign Key, address Table, Required

## Room data

### room_type table

* room_type_id Primary Key, Identity
* room_type_name Required, Extended Character Set, Length: 30
* standard_occupancy Required, Int
* maximum_occupancy Required, Int
* base_price Required, Decimal(10, 2)
* additional_adult_price Decimal(10, 2)

### room table

* room_id Primary Key, Identity
* room_type Required, Foreign Key, room_type Table
* ada_accessible Required, Boolean

### amenity table

* amenity_id Primary Key, Identity
* room_id Required, Foreign Key, room Table
* amenity_name Required, Extended Character Set, Length: 30
* amenity_fee Required, Decimal(10, 2), Default 0

## Reservation data

### reservation table

* reservation_id Primary Key, Identity
* guest_id Foreign Key, guest Table, Required
* start_date Required, Date
* end_date Required, Date

### reserved_room bridge table

* reservation_id Foreign Key, reservation Table, Required
* room_id Foreign Key, room Table, Required
* number_adult Required, Int, Default 1
* number_child Required, Int, Default 0
* total_room_cost Required, Decimal(10, 2)
* Composite Key (reservation_id, room_id)
