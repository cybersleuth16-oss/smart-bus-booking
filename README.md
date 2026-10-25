# Smart Bus Ticket Booking & Reservation System

A beginner-friendly Python 3 console application that manages bus routes, seat bookings, cancellations, schedules and reports.

## Python requirement
Python 3. Built-in functionality only; no external packages.

## How to run
- Locally: `python main.py`
- Google Colab: paste the contents of `main.py` into one cell, run it, and type menu choices in the box under the cell.

## Menu guide
1. View Available Routes - all routes, only routes with seats, or schedule by departure city
2. Search for a Route - by route ID or city (case-insensitive)
3. Book a Ticket - enter name, age, route ID and number of seats
4. View My Bookings - all bookings, including cancelled ones
5. Cancel a Booking - by booking ID (Confirmed bookings only)
6. View Seat Availability - available vs total seats, with status
7. Generate Booking Report - counts, reserved seats, confirmed revenue, fully booked routes
8. Exit

## Sample workflow
1. Choose 3 and book: Ahmed, age 24, R101, 2 seats -> Booking B1001, total Rs. 2400.
2. Choose 6 -> R101 shows 38/40 seats.
3. Choose 5 and cancel B1001 -> 2 seats restored, status Cancelled.
4. Choose 7 -> the cancelled booking is excluded from confirmed revenue.

## Storage limitation
All data is stored in memory only. Routes and bookings are lost when the program closes (or the Colab session resets). No database or file storage is used.

## Constraints
Console only. No GUI, website, database, payment gateway, third-party API or external libraries.

## Files
- main.py - complete source code
- test_cases.txt - 12 test scenarios with expected and actual results
- DEMONSTRATION.md - explanation notes for the demonstration
- screenshots/ - route listing, booking, cancellation, report
