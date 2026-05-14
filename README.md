# Smart Hotel Booking System - Microservices Architecture

A comprehensive hotel booking platform built with .NET 8 microservices architecture.

## Architecture Overview

This project implements a microservices-based backend system with the following services:

### Services

1. **UserService** (Port: 5001)
   - User authentication and authorization
   - JWT token generation
   - Role-based access control (Guest, Hotel Manager, Admin)

2. **HotelService** (Port: 5002)
   - Hotel and room management
   - Search functionality
   - Availability tracking

3. **BookingService** (Port: 5003)
   - Booking creation and management
   - Cancellation handling (24-hour policy)
   - Booking status tracking

4. **PaymentService** (Port: 5004)
   - Payment processing
   - Refund management
   - Multiple payment methods support

5. **ReviewService** (Port: 5005)
   - Customer reviews and ratings
   - Hotel manager responses
   - Average rating calculation

6. **LoyaltyService** (Port: 5006)
   - Loyalty points management
   - Points redemption
   - Rewards tracking

### Building Blocks

- **Common Library**: Shared models, DTOs, enums, and utilities

## Technology Stack

- **.NET 8**: Modern framework for building microservices
- **Entity Framework Core**: ORM for data access
- **In-Memory Database**: For development and testing
- **JWT Authentication**: Secure token-based authentication
- **Swagger/OpenAPI**: API documentation
- **BCrypt**: Password hashing

## Project Structure

```
SmartHotelBooking/
├── src/
│   ├── Services/
│   │   ├── UserService/
│   │   ├── HotelService/
│   │   ├── BookingService/
│   │   ├── PaymentService/
│   │   ├── ReviewService/
│   │   └── LoyaltyService/
│   ├── ApiGateway/
│   └── BuildingBlocks/
│       └── Common/
└── SmartHotelBooking.sln
```

## Getting Started

### Prerequisites

- .NET 8 SDK
- Visual Studio 2022 or Visual Studio Code
- Postman or similar API testing tool

### Running the Services

Each service can be run independently:

```powershell
# UserService
cd src/Services/UserService
dotnet run

# HotelService
cd src/Services/HotelService
dotnet run

# BookingService
cd src/Services/BookingService
dotnet run

# PaymentService
cd src/Services/PaymentService
dotnet run

# ReviewService
cd src/Services/ReviewService
dotnet run

# LoyaltyService
cd src/Services/LoyaltyService
dotnet run
```

### Building the Solution

```powershell
dotnet build
```

### Swagger Documentation

Each service exposes Swagger UI at:
- `https://localhost:<port>/swagger`

## API Endpoints

### UserService
- `POST /api/auth/register` - Register new user
- `POST /api/auth/login` - Login user
- `GET /api/auth/{userId}` - Get user details

### HotelService
- `POST /api/hotels` - Create hotel
- `GET /api/hotels/{hotelId}` - Get hotel by ID
- `POST /api/hotels/search` - Search hotels
- `PUT /api/hotels/{hotelId}` - Update hotel
- `DELETE /api/hotels/{hotelId}` - Delete hotel
- `GET /api/hotels/{hotelId}/rooms` - Get hotel rooms
- `POST /api/hotels/rooms` - Create room

### BookingService
- `POST /api/bookings` - Create booking
- `GET /api/bookings/{bookingId}` - Get booking by ID
- `GET /api/bookings/user/{userId}` - Get user bookings
- `GET /api/bookings/hotel/{hotelId}` - Get hotel bookings
- `PUT /api/bookings/{bookingId}/cancel` - Cancel booking
- `PUT /api/bookings/{bookingId}/confirm` - Confirm booking

### PaymentService
- `POST /api/payments/process` - Process payment
- `GET /api/payments/{paymentId}` - Get payment by ID
- `GET /api/payments/booking/{bookingId}` - Get payment by booking
- `POST /api/payments/{paymentId}/refund` - Refund payment

### ReviewService
- `POST /api/reviews` - Create review
- `GET /api/reviews/{reviewId}` - Get review by ID
- `GET /api/reviews/hotel/{hotelId}` - Get hotel reviews
- `GET /api/reviews/user/{userId}` - Get user reviews
- `POST /api/reviews/{reviewId}/respond` - Respond to review
- `GET /api/reviews/hotel/{hotelId}/average-rating` - Get average rating

### LoyaltyService
- `GET /api/loyalty/account/{userId}` - Get loyalty account
- `POST /api/loyalty/add-points` - Add points
- `POST /api/loyalty/redeem` - Redeem points
- `GET /api/loyalty/redemptions/{userId}` - Get redemptions

## Features

### User Management
- Secure registration and authentication
- Role-based access (Admin, Hotel Manager, Guest)
- JWT token-based authorization

### Hotel Management
- Hotel listing and management
- Room inventory management
- Dynamic pricing
- Amenities tracking

### Booking System
- Real-time availability checking
- Booking confirmation
- 24-hour cancellation policy
- Status tracking (Pending, Confirmed, Cancelled, Completed)

### Payment Processing
- Multiple payment methods
- Secure transaction handling
- Refund processing
- Payment status tracking

### Reviews & Ratings
- Customer feedback system
- 1-5 star rating
- Hotel manager responses
- Average rating calculation

### Loyalty Program
- Earn 10 points per dollar spent
- Redeem points for discounts (1 point = $0.01)
- Transaction history
- Points balance tracking

## Configuration

Each service uses `appsettings.json` for configuration:

```json
{
  "JwtSettings": {
    "SecretKey": "YourSuperSecretKeyForJWTTokenGeneration123456",
    "Issuer": "SmartHotelBooking",
    "Audience": "SmartHotelBookingUsers"
  }
}
```

## Database

Currently using In-Memory database for development. For production:
- Replace with SQL Server, PostgreSQL, or MySQL
- Update connection strings in `appsettings.json`
- Run migrations for each service

## Security

- Passwords hashed using BCrypt
- JWT tokens for authentication
- CORS enabled for development
- Role-based authorization

## Future Enhancements

- [ ] API Gateway implementation (Ocelot)
- [ ] Message queue integration (RabbitMQ/Kafka)
- [ ] Distributed caching (Redis)
- [ ] Docker containerization
- [ ] Kubernetes orchestration
- [ ] Logging and monitoring (Serilog, ELK)
- [ ] Health checks
- [ ] Rate limiting
- [ ] Email notifications
- [ ] SMS notifications
- [ ] Real-time notifications (SignalR)

## Contributing

1. Fork the repository
2. Create your feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## License

This project is for educational purposes.
