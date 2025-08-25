# 1. Web Application Overview

# 1.1 Web App Name
Airline Reservation Management System using AWS Elastic Beanstalk.

# 1.2 Web App Description

# Problem Solved:

Current flight reservation systems lack real-time flight status updates and efficient luggage tracking. Our system addresses these gaps by providing a seamless booking process, real-time notifications, and enhanced user experience through an integrated backend.

# Purpose of the Application:

This web application allows passengers to book flights, track luggage, and receive real-time flight updates. Admins can manage flight schedules, monitor bookings, and handle ticket pricing efficiently.

# Target Users:

Passengers: Search, book, and manage flight tickets.
Ground Staff: Manage check-ins, boarding, and baggage tracking.

# 2. Web Application Functionalities
# 2.1 Features & Functionalities

User Management: Passengers register, log in, and update profiles; admins manage flights and pricing.
Flight Search & Booking: Users search flights by source, destination, date, and price, with REST API fetching real-time flight data.
Real-Time Flight Status Updates: Kafka streams instant flight status updates (delays, cancellations).
Ticket Booking & Payment Processing: Secure booking with Stripe/PayPal integration; Kafka ensures booking confirmations.
Flight Check-in & Boarding Pass Generation: Online check-in and digital boarding pass generation.

# 2.2 Major Pages and Routes

Home Page: Flight search, popular routes, offers
Login & Registration: Passenger/Admin authentication
Flight Search & Booking: Displays flight options, pricing, and booking functionality
Dashboard: User bookings, flight status, check-in options
Payment Gateway Page: Secure transactions via Stripe/PayPal

# 2.3 API Endpoints (Spring Boot REST API)

# User Authentication:

POST /register - New user signup
POST /login - User authentication
GET /users/{id} - Fetch user profile

# Flight Management:

GET /flights - Fetch available flights
POST /flights - Admin adds a new flight
DELETE /flights/{id} - Remove a flight

# Booking System:

POST /bookings - Create a new booking
GET /bookings/{userId} - Retrieve user bookings

# Payment Integration:

POST /payments - Process payment via Stripe/PayPal
GET /payments/{bookingId} - Fetch payment status
Real-Time Updates (Kafka):
Flight status updates
Booking confirmation messages

# 2.4 Database Schema & Design

# Key Tables:

Users: userId (PK), name, email, password, role
Flights: flightId (PK), source, destination, schedule, availableSeats
Bookings: bookingId (PK), userId (FK), flightId (FK), paymentStatus
Luggage: baggageId (PK), bookingId (FK), status

# 3. Tech Stack

Frontend: JSP / React
Backend: Spring Boot (REST APIs)
Messaging System: Kafka (Flight status, booking updates, baggage tracking)
Database: Amazon DynamoDB (NoSQL)
Authentication: Spring Security and Spring MVC
Payment Gateway: Stripe API

# 4. How to Run the Application
Running Locally

# Clone the repository:

git clone https://github.com/yourusername/AirlineReservationSystem.git
cd AirlineReservationSystem

Update application.properties with your database configuration.

# Build the project:

mvn clean package

# Run the application:

java -jar target/flightticket-0.0.1-SNAPSHOT.jar

# Open the app in your browser:

http://localhost:8080

# Running on AWS Elastic Beanstalk :

Package the JAR using mvn package.
Log in to AWS Elastic Beanstalk and create a new Java environment.
Upload the JAR file and deploy.
Access the application via the Elastic Beanstalk URL provided.

# 5. Conclusion

The Airline Reservation and Flight Management System is a robust, scalable, and secure web application designed to enhance flight booking experiences with real-time updates and efficient management. By integrating Spring Boot, Kafka, and AWS services, the project ensures high availability and seamless user interactions.
