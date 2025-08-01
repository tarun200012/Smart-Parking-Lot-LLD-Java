# 🚗 Smart Parking Lot Backend System (Java - Console Based)

This project is a **console-based backend system** for a **Smart Parking Lot**, designed using **Object-Oriented Programming**, **SOLID principles**, and a clean **low-level architecture**.

It supports:
- Multiple floors
- Different vehicle types
- Entry & exit tracking
- Spot allocation strategies
- Real-time availability
- Time-based fee calculation
- Concurrency handling

## 🔧 Technologies Used

- Java (No Spring Boot)
- Maven (Project Build Tool)
- JUnit 5 (for testing)
- Console-based interface
- Pure OOP Design (No external APIs or databases)

## 🧠 Problem Statement

Design a smart parking system to manage:
- **Vehicle entries/exits**
- **Spot allocation based on vehicle type**
- **Time-based fee calculation**
- **Real-time available spots**
- **Multiple entry/exit points**
- **Fair distribution of vehicle load across floors**

## 🎯 Features

| Feature                            | Description |
|-----------------------------------|-------------|
| 🚘 Vehicle Entry & Exit           | Tracks in/out time for each vehicle |
| 🅿️ Dynamic Spot Allocation        | Allocates spot based on vehicle type and strategy |
| ⏱️ Time-based Fee Calculation     | Calculates charges based on seconds parked |
| 🧮 Floor Balancing Strategy        | Allocates vehicle to the floor with most available spots |
| 📋 Real-time Spot Availability     | Displays available spots by floor and type |
| 🔄 Concurrency Safe Operations     | Handles multiple check-ins/outs concurrently (using `synchronized`) |
| 🧪 JUnit Tests                     | Multiple test cases validating logic and concurrency |

## 📁 Project Structure

src/
├── core/
│ └── ParkingLotManager.java # Core logic for entry, exit, spot tracking, fee calculation
├── model/
│ ├── Vehicle.java
│ ├── VehicleType.java
│ ├── Floor.java
│ ├── ParkingSpot.java
│ └── SpotType.java
├── strategy/
│ ├── SpotAllocationStrategy.java
│ ├── BalancedFloorStrategy.java
│ └── NearestFirstStrategy.java
├── util/
│ └── FeeCalculator.java
└── Main.java # Console app entry point

## 🔄 Flow & How It Works

1. **Vehicle Entry**
   - User inputs vehicle number & type (CAR, MOTORCYCLE, BUS)
   - System determines required spot type
   - Strategy allocates the nearest suitable spot
   - Records vehicle and timestamp

2. **Vehicle Exit**
   - User inputs vehicle number
   - Calculates time parked (in seconds)
   - Calculates fee using `FeeCalculator`
   - Releases the spot
   - Adds fee to summary

3. **Spot Allocation Strategy**
   - Pluggable via `SpotAllocationStrategy` interface
   - Two strategies implemented:
     - `NearestFirstStrategy`: Picks the first available spot
     - `BalancedFloorStrategy`: Picks floor with most available spots to balance load

4. **Concurrency**
   - `checkIn` and `checkOut` methods use `synchronized` to prevent race conditions

5. **Fee Structure**
   - Motorcycle: ₹0.10 per second  
   - Car: ₹0.20 per second  
   - Bus: ₹0.50 per second

## 🧪 Testing (JUnit 5)

Test class: `ParkingLotManagerTest.java`

### ✔️ Covered Scenarios:
- Multiple vehicles entry/exit with fee verification
- Concurrent check-ins and check-outs using threads
- Mixed operations with timing
- Fee calculation accuracy

Design Principles Followed
✅ OOP & Abstraction: Clear separation of entities like Vehicle, Floor, Spot, and strategies

✅ SOLID Principles:

S: ParkingSpot, Floor, etc. follow single responsibility

O: New strategies can be added without changing core logic

D: Spot strategy injected via constructor (SpotAllocationStrategy)

✅ Pluggable Strategy Pattern for spot allocation

✅ Extensible for future enhancements (e.g., hourly rate, GUI, Spring Boot REST APIs)

 Possible Future Enhancements
Add database for persistence

Implement hourly or slab-based billing

Add REST APIs using Spring Boot

Web-based or mobile-based front-end

Admin dashboard with analytics
