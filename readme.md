# Hall Booking API

Hall Booking API allows users to manage rooms and bookings for a hall booking application. This API supports creating rooms, booking rooms, and retrieving information about rooms and bookings. The API is designed to handle multiple rooms and customers, ensuring that rooms cannot be double-booked.

---

## Documentation

The API documentation is available in following Postman URL: [https://documenter.getpostman.com/view/37083969/2sA3kXEgDx](https://documenter.getpostman.com/view/37083969/2sA3kXEgDx)

---

## Render URL

- **Render URL:** `https://hall-booking-api-1fp4.onrender.com`

## Endpoints

### 1. Create Room

- **Method:** POST
- **URL:** `https://hall-booking-api-1fp4.onrender.com/rooms`
- **Request Body:**

  ```json
  {
    "numberOfSeats": 50,
    "amenities": ["WiFi", "Projector", "Whiteboard"],
    "pricePerHour": 100
  }
  ```

- **Description:** Create a new room with the specified number of seats, amenities, and price per hour.
- **Responses:**
  - **201 Created:** Room was successfully created.
    ```json
    {
      "roomId": 1,
      "numberOfSeats": 50,
      "amenities": ["WiFi", "Projector", "Whiteboard"],
      "pricePerHour": 100
    }
    ```

### 2. Book Room

- **Method:** POST
- **URL:** `https://hall-booking-api-1fp4.onrender.com/bookings`
- **Request Body:**
  ```json
  {
    "customerName": "John Doe",
    "date": "2024-07-24",
    "startTime": "10:00",
    "endTime": "12:00",
    "roomId": 1
  }
  ```
- **Description:** Book a room for a customer on a specified date and time. Ensures that the room is not already booked for the given time.
- **Responses:**
  - **201 Created:** Booking was successfully created.
    ```json
    {
      "bookingId": 1,
      "customerName": "John Doe",
      "date": "2024-07-24",
      "startTime": "10:00",
      "endTime": "12:00",
      "roomId": 1
    }
    ```
  - **400 Bad Request:** Room is already booked for the given time.
    ```json
    {
      "message": "Room is already booked for the given time"
    }
    ```

### 3. List All Rooms with Booked Data

- **Method:** GET
- **URL:** `https://hall-booking-api-1fp4.onrender.com/rooms`
- **Description:** Retrieve a list of all rooms along with their booking details.
- **Responses:**
  - **200 OK:** A list of rooms with their booking details.
    ```json
    [
      {
        "roomId": 1,
        "numberOfSeats": 50,
        "amenities": ["WiFi", "Projector", "Whiteboard"],
        "pricePerHour": 100,
        "bookings": [
          {
            "bookingId": 1,
            "customerName": "John Doe",
            "date": "2024-07-24",
            "startTime": "10:00",
            "endTime": "12:00",
            "roomId": 1
          }
        ]
      }
    ]
    ```

### 4. List All Customers with Booked Data

- **Method:** GET
- **URL:** `https://hall-booking-api-1fp4.onrender.com/customers`
- **Description:** Retrieve a list of all customers along with their booking details.
- **Responses:**
  - **200 OK:** A list of customers with their booking details.
    ```json
    [
      {
        "customerName": "John Doe",
        "roomId": 1,
        "date": "2024-07-24",
        "startTime": "10:00",
        "endTime": "12:00"
      }
    ]
    ```

### 5. List Bookings by Customer

- **Method:** GET
- **URL:** `https://hall-booking-api-1fp4.onrender.com/customers/:customerName`
- **Path Parameters:**
  - `customerName` (string): The name of the customer whose bookings are to be retrieved.
- **Description:** Retrieve all bookings made by a specific customer.
- **Responses:**
  - **200 OK:** A list of bookings made by the specified customer.
    ```json
    [
      {
        "bookingId": 1,
        "customerName": "John Doe",
        "date": "2024-07-24",
        "startTime": "10:00",
        "endTime": "12:00",
        "roomId": 1
      }
    ]
    ```

---

## Getting Started

### Prerequisites

- Node.js
- npm (Node Package Manager)

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/arunkarthik0712/hall-booking-api.git
   ```
2. Navigate to the project directory:
   ```bash
   cd hall-booking-api
   ```
3. Install the dependencies:
   ```bash
   npm install
   ```

### Running the Server

1. Start the server:
   ```bash
   node index.js
   ```
2. The API will be running at `http://localhost:3000`.

### Testing the API

Use an API testing tool like [Postman](https://www.postman.com/) to test the endpoints.

### Deployment

1. Deploy the application to [Render](https://render.com/).
2. Follow Render’s documentation to connect your GitHub repository and deploy your Node.js application.

---
