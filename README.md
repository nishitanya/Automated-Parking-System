# Automated Parking System

## Project Overview

This project is a real-time automated parking system built using basic digital logic ICs. It handles vehicle entry and exit, monitors parking space availability, and calculates the parking fee based on how long a car is parked. The system is suitable for public locations like shopping malls, airports, and stadiums where organized parking is essential.

<img width="1224" height="996" alt="unnamed" src="https://github.com/user-attachments/assets/f4d1367c-0465-4d4e-9eee-e2ed50f81363" />

## System Structure

### Master Clock

The timing unit of the project is built using two decade counters. A 10 Hz digital clock drives the first counter. When it reaches 9, it resets and increments the second counter. This allows the clock to run from 00 to 99. These values are used for storing entry time and calculating the parking duration.

### Car Number Input and Memory Storage

Car numbers are input using 12-bit BCD values (representing three digits). These act as addresses in the 2K8 RAM. When a car enters, the write pin is enabled and the current clock value is stored at that address. When the car exits, the value is read and used to calculate the fee.

### Car Counter

The total parking capacity can be set using two BCD switches. A comparator checks if the current number of cars is less than the maximum capacity. If space is available, entry is allowed and the car counter is incremented. When a car exits, the counter is decremented. This is managed using a BCD Up/Down counter.

### Parking Fee Calculator

When a car exits, its entry time is fetched from RAM and the current time is obtained from the clock. A BCD subtractor calculates the difference, representing the duration of parking. The subtraction is implemented using 4-bit binary adders with 9's and 10's complement logic. The result is displayed on a seven segment display.



