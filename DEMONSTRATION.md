# Demonstration Notes - Smart Bus Reservation System

## 1. Program flow
- main() runs a `while True` loop: show menu -> read choice -> run the matching function -> repeat.
- Non-numeric input uses `continue` (menu shows again); unsupported numbers get an error message.
- Option 8 uses `break` to leave the loop cleanly.

## 2. Data structures (and why)
- List of dictionaries (`routes`, `bookings`): ordered records, each with named fields.
- Tuple (`SUPPORTED_CITIES`): a fixed collection that should not change.
- Set (`issued_ids`): fast duplicate check so booking IDs are unique.
- Strings / integers: IDs and status; age, seats and fares.

## 3. Booking and validation (book_ticket)
Checks happen in order: name not blank -> age positive integer -> route exists -> seats positive integer -> seats <= available.
The function stops (return) at the first failure, so nothing changes on a bad request.
Only after all checks pass: generate a unique ID, total fare = price x seats, append the record with status Confirmed, then subtract the seats.

## 4. Cancellation (cancel_booking)
- A for-else loop searches by booking ID; the else block says "not found".
- If found but not Confirmed -> "already cancelled" (no seat change).
- If Confirmed -> add the booking's seats back to its route, set status to Cancelled, keep the record for history.
- Seats are restored exactly once because a Cancelled booking is rejected next time.

## 5. Report (generate_report)
- Counts all records, confirmed and cancelled.
- Nested loops: outer loop over routes, inner loop over bookings that match the route AND are Confirmed. Seats and fares are summed from those only, so cancelled bookings never reach revenue.
- Fully booked routes are counted from routes whose available seats equal 0.

## 6. Where each required concept is
| Concept | Location |
|---|---|
| enumerate() | view_routes, view_bookings |
| continue | view_routes filter, view_seat_availability, main |
| break | search_route, cancel_booking, main |
| for-else | search_route, cancel_booking |
| Nested for loops | route_schedule, generate_report |
| Nested conditions | book_ticket, cancel_booking |
| Tuple / set | SUPPORTED_CITIES / issued_ids |

## 7. Suggested live demo order
1. Menu 1 (routes) 2. Menu 2 (search "hyderabad", then "Atlantis") 3. Menu 4 on empty (No bookings found)
4. Menu 3 valid booking, then invalid seats (0 and 99) 5. Menu 6 (seat status)
6. Menu 5 cancel, then cancel again 7. Menu 7 report 8. Menu 8 exit
