# Vehicle Rental API Integration Using BLoC

## Overview
This project focuses on integrating a **vehicle rental system** using the **BLoC architecture** in Flutter. Users can **add** a rental vehicle, **fetch** all rental vehicles, **update** vehicle details, and **delete** a vehicle through API calls.

---

## API Endpoints

### 1. Add a Vehicle (POST)
**Endpoint:**  
`http://45.159.221.50:8868/api/add-vehicle`

**Request Body:**
```json
{
  "brand": "Toyota",
  "model": "Corolla",
  "description": "A reliable sedan",
  "rentPrice": 15000,
  "mileage": 25,
  "photos": [
    "https://mir-s3-cdn-cf.behance.net/project_modules/1400/225c5367179339.5b30effb80541.jpg"
  ],
  "vehicleColor": "Blue",
  "gearType": "Automatic",
  "fuelType": "Petrol",
  "noOfSeats": 4,
  "rating": 4.5,
  "noOfDoors": 4,
  "ownerName": "Hunais",
  "ownerPhoneNumber": "6238814407",
  "ownerPlace": "Vailathur",
  "ownerProfilePhoto": "https://expertphotography.b-cdn.net/wp-content/uploads/2020/08/profile-photos-4.jpg",
  "location": { 
    "type": "Point", 
    "coordinates": [10.953600306199496, 75.94535350322334] 
  },
  "available": true
}
```

---

### 2. Get All Vehicles (GET)
**Endpoint:**  
`http://45.159.221.50:8868/api/get-vehicles`

---

### 3. Update a Vehicle (PUT)
**Endpoint:**  
`http://45.159.221.50:8868/api/update-vehicle/{vehicle_id}`

**Request Body:**
```json
{
  "brand": "Honda",
  "model": "Civic",
  "description": "A compact car",
  "rentPrice": 5500,
  "available": false
}
```

---

### 4. Delete a Vehicle (DELETE)
**Endpoint:**  
`http://45.159.221.50:8868/api/delete-vehicle/{vehicle_id}`

---

## Task
### Implement a Vehicle Rental System Using BLoC

Your task is to build a **Vehicle Rental Feature** using Flutter and BLoC that supports the following:
1. **Fetch all rental vehicles** and display them in a list.
2. **Allow users to add a vehicle** by entering details such as brand, model, rent price, etc.
3. **Enable users to update vehicle details** such as price, description, and availability.
4. **Provide users with an option to delete a vehicle.**

---

## Steps to Implement

### 1. Define BLoC Events & States
- Create a `VehicleEvent` class to handle different API operations (`AddVehicle`, `FetchVehicles`, `UpdateVehicle`, `DeleteVehicle`).
- Create a `VehicleState` class to represent states like **loading**, **success**, and **failure**.

### 2. Create a Repository Layer
- Implement a `VehicleRepository` class that interacts with the API.
- Use the `http` package to perform **GET, POST, PUT, and DELETE** requests.

### 3. Implement VehicleBloc
- Develop a `VehicleBloc` class to manage state changes.
- Handle API calls and emit different states based on success or failure.

### 4. Build the Flutter UI
- Use `BlocBuilder` to display the vehicle list.
- Use `BlocListener` to handle API responses such as **success messages** or **errors**.
- Implement buttons for **adding, updating, and deleting** a vehicle.

---

## Challenge
### Optimize API Calls & State Management
- Implement **caching** strategies to reduce unnecessary API calls.
- Use **debouncing** for handling user input efficiently.
- Ensure **error handling** and **loading indicators** are properly displayed.

---
