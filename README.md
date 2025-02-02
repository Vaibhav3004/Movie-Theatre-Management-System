🎬 Movie Theatre Management System
📌 Overview
The Movie Theatre Management System is a SQL-based relational database designed to manage online movie ticket bookings. Inspired by platforms like BookMyShow, this system efficiently handles movies, theaters, screens, showtimes, customers, and bookings, ensuring data integrity, seamless seat reservations, and user management.

🚀 Features
✔️ Movie Search & Showtime Management 🎥
✔️ Efficient Ticket Booking & Seat Allocation 🎟️
✔️ User Management (Registration & Authentication) 👤
✔️ Reports & Analytics on Movie Popularity & Bookings 📊
✔️ Scalable for Future Enhancements 🔄

📂 Database Schema
Tables & Relationships
The database consists of seven core tables:

1️⃣ Movies – Stores movie details (Title, Genre, Duration, Rating, Language).
2️⃣ Theaters – Manages theaters with location and screen count.
3️⃣ Screens – Contains screen details (Capacity, Theater ID).
4️⃣ Showtimes – Handles movie schedules (Start Time, End Time).
5️⃣ Customers – Stores user details (Name, Email, Phone).
6️⃣ Tickets – Manages bookings, linking movies, showtimes, and customers.
7️⃣ Staff – Stores staff details for managing operations.

🔗 ER Diagram Preview:

🛠️ SQL Commands
📌 Creating Tables
sql
Copy
Edit
CREATE TABLE Movies (
    MovieID INT PRIMARY KEY AUTO_INCREMENT,
    Title VARCHAR(255) NOT NULL,
    Genre VARCHAR(100),
    Duration INT,
    Rating FLOAT,
    ReleaseDate DATE,
    Language VARCHAR(50)
);
sql
Copy
Edit
CREATE TABLE Theaters (
    TheaterID INT PRIMARY KEY AUTO_INCREMENT,
    Name VARCHAR(255) NOT NULL,
    Location VARCHAR(255),
    NumberOfScreens INT
);
📌 Sample Queries
✅ List all movies and their showtimes

sql
Copy
Edit
SELECT Movies.Title, Showtimes.StartTime, Showtimes.Date 
FROM Movies 
LEFT JOIN Showtimes ON Movies.MovieID = Showtimes.MovieID;
✅ Find all customers who purchased tickets for a specific showtime

sql
Copy
Edit
SELECT Customers.CustomerName, Customers.Email 
FROM Customers 
WHERE CustomerID IN (SELECT CustomerID FROM Tickets WHERE ShowtimeID = 401);
✅ Get movies with ratings higher than the average

sql
Copy
Edit
SELECT Title, Rating 
FROM Movies 
WHERE Rating > (SELECT AVG(Rating) FROM Movies);
📊 Insights & Reports
🎟 Total Number of Bookings: COUNT(Tickets.TicketID)
⭐ Top-rated Movies: Movies with Rating > 8
🏆 Most Popular Theaters: GROUP BY TheaterID ORDER BY COUNT(Tickets.TicketID) DESC
📈 Peak Showtime Hours: GROUP BY StartTime ORDER BY COUNT(Tickets.TicketID) DESC
🔥 Future Enhancements
✅ Real-time seat availability tracking
✅ Integration with payment gateways
✅ AI-powered recommendation engine
✅ Optimized queries for better performance

👨‍💻 Developed By
Vaibhav Devare
