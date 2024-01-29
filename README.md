# Java-Development-Assignment

Project Structure-
customer-management-app/
|-- backend/
|   |-- src/
|   |   |-- main/
|   |   |   |-- java/
|   |   |   |   |-- com/
|   |   |   |   |   |-- example/
|   |   |   |   |   |   |-- CustomerApplication.java
|   |   |   |   |   |   |-- config/
|   |   |   |   |   |   |   |-- JwtTokenUtil.java
|   |   |   |   |   |   |   |-- WebSecurityConfig.java
|   |   |   |   |   |   |-- controller/
|   |   |   |   |   |   |   |-- CustomerController.java
|   |   |   |   |   |   |-- model/
|   |   |   |   |   |   |   |-- Customer.java
|   |   |   |   |   |   |-- repository/
|   |   |   |   |   |   |   |-- CustomerRepository.java
|   |   |   |   |   |   |-- service/
|   |   |   |   |   |   |   |-- CustomerService.java
|   |   |   |   |   |   |   |-- CustomerServiceImpl.java
|   |   |   |   |   |-- resources/
|   |   |   |   |   |   |-- application.properties
|-- frontend/
|   |-- index.html
|   |-- styles.css
|   |-- script.js
|-- README.md

Backend (Spring Boot)
Customer.java: Entity class representing the customer.
// Customer.java
import javax.persistence.Entity;
import javax.persistence.GeneratedValue;
import javax.persistence.GenerationType;
import javax.persistence.Id;

@Entity
public class Customer {
    // Fields representing customer attributes
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String firstName;
    private String lastName;
    private String street;
    private String address;
    private String city;
    private String state;
    private String email;
    private String phone;

    // Default constructor
    public Customer() {
        // Default constructor required by JPA
    }

    // Parameterized constructor
    public Customer(String firstName, String lastName, String street, String address, 
                    String city, String state, String email, String phone) {
        this.firstName = firstName;
        this.lastName = lastName;
        this.street = street;
        this.address = address;
        this.city = city;
        this.state = state;
        this.email = email;
        this.phone = phone;
    }

    // Getter and setter methods for each field

    public Long getId() {
        return id;
    }

    public void setId(Long id) {
        this.id = id;
    }

    public String getFirstName() {
        return firstName;
    }

    public void setFirstName(String firstName) {
        this.firstName = firstName;
    }

    public String getLastName() {
        return lastName;
    }

    public void setLastName(String lastName) {
        this.lastName = lastName;
    }

    public String getStreet() {
        return street;
    }

    public void setStreet(String street) {
        this.street = street;
    }

    public String getAddress() {
        return address;
    }

    public void setAddress(String address) {
        this.address = address;
    }

    public String getCity() {
        return city;
    }

    public void setCity(String city) {
        this.city = city;
    }

    public String getState() {
        return state;
    }

    public void setState(String state) {
        this.state = state;
    }

    public String getEmail() {
        return email;
    }

    public void setEmail(String email) {
        this.email = email;
    }

    public String getPhone() {
        return phone;
    }

    public void setPhone(String phone) {
        this.phone = phone;
    }
}


CustomerRepository.java: Repository interface for CRUD operations.
// CustomerRepository.java
public interface CustomerRepository extends JpaRepository<Customer, Long> {
    // Custom queries if needed
}

CustomerService.java and CustomerServiceImpl.java: Service interface and its implementation.
// CustomerService.java
public interface CustomerService {
    // CRUD methods
}
// CustomerServiceImpl.java
@Service
public class CustomerServiceImpl implements CustomerService {
    // Implement CRUD methods
}

CustomerController.java: REST API endpoints.
// CustomerController.java
@RestController
@RequestMapping("/api/customers")
public class CustomerController {
    // Implement CRUD endpoints
}

JwtTokenUtil.java and WebSecurityConfig.java: JWT token utility and security configuration.
// JwtTokenUtil.java
public class JwtTokenUtil {
    // Token-related methods
}
// WebSecurityConfig.java
@EnableWebSecurity
public class WebSecurityConfig extends WebSecurityConfigurerAdapter {
    // Security configuration
}

Frontend (HTML, CSS, JS)
index.html: Basic structure for login, customer list, and add customer screens.
<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Customer Management App</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <!-- Login Screen -->
    <div id="loginScreen">
        <!-- Your login form here -->
    </div>

    <!-- Customer List Screen -->
    <div id="customerListScreen">
        <!-- Your customer list table here -->
        <!-- Add sync button -->
    </div>

    <!-- Add Customer Screen -->
    <div id="addCustomerScreen">
        <!-- Your add customer form here -->
    </div>

    <script src="script.js"></script>
</body>
</html>

styles.css: Basic styling for the screens.
/* styles.css */
/* Global styles */
body {
    font-family: 'Arial', sans-serif;
}

/* Login Screen styles */
#loginScreen {
    text-align: center;
    margin-top: 50px;
}

#loginScreen input {
    margin-bottom: 10px;
    padding: 5px;
}

#loginScreen button {
    padding: 8px 15px;
    background-color: #4caf50;
    color: #fff;
    border: none;
    cursor: pointer;
}

/* Customer List Screen styles */
#customerListScreen {
    margin-top: 20px;
}

#customerListScreen table {
    width: 100%;
    border-collapse: collapse;
    margin-bottom: 20px;
}

#customerListScreen th, #customerListScreen td {
    border: 1px solid #ddd;
    padding: 8px;
    text-align: left;
}

#customerListScreen th {
    background-color: #4caf50;
    color: #fff;
}

#customerListScreen button {
    background-color: #3498db;
    color: #fff;
    padding: 5px 10px;
    margin-right: 5px;
    cursor: pointer;
}

/* Add Customer Screen styles */
#addCustomerScreen {
    margin-top: 20px;
}

#addCustomerScreen form {
    display: flex;
    flex-direction: column;
    max-width: 300px;
}

#addCustomerScreen input, #addCustomerScreen select {
    margin-bottom: 10px;
    padding: 8px;
}

#addCustomerScreen button {
    background-color: #3498db;
    color: #fff;
    padding: 8px 15px;
    border: none;
    cursor: pointer;
}

script.js: JavaScript code for handling UI interactions.
// script.js
// JavaScript code here

document.addEventListener('DOMContentLoaded', function () {
    // Add event listener for login form submission
    const loginForm = document.getElementById('loginForm');
    if (loginForm) {
        loginForm.addEventListener('submit', function (event) {
            event.preventDefault();

            // Fetch user credentials from the form
            const loginId = document.getElementById('loginId').value;
            const password = document.getElementById('password').value;

            // Perform authentication API call
            authenticateUser(loginId, password);
        });
    }

    // Add event listener for sync button click
    const syncButton = document.getElementById('syncButton');
    if (syncButton) {
        syncButton.addEventListener('click', function () {
            // Perform synchronization API call
            syncCustomerData();
        });
    }

    // Add event listener for add customer form submission
    const addCustomerForm = document.getElementById('addCustomerForm');
    if (addCustomerForm) {
        addCustomerForm.addEventListener('submit', function (event) {
            event.preventDefault();

            // Fetch customer data from the form
            const firstName = document.getElementById('firstName').value;
            const lastName = document.getElementById('lastName').value;
            // ... (fetch other fields)

            // Perform add customer API call
            addCustomer(firstName, lastName, /* other fields */);
        });
    }
});

// Function to authenticate the user
function authenticateUser(loginId, password) {
    // Perform authentication API call using fetch or XMLHttpRequest
    // Include necessary headers and handle the response
    // Update UI based on authentication success or failure
}

// Function to synchronize customer data
function syncCustomerData() {
    // Perform synchronization API call using fetch or XMLHttpRequest
    // Include necessary headers and handle the response
    // Update UI based on synchronization success or failure
}

// Function to add a new customer
function addCustomer(firstName, lastName, /* other fields */) {
    // Perform add customer API call using fetch or XMLHttpRequest
    // Include necessary headers and handle the response
    // Update UI based on add customer success or failure
}

README.md file for your project:
# Customer Management App

This is a simple CRUD (Create, Read, Update, Delete) application for managing customer information. The application is built using Spring Boot for the backend, MySQL for the database, and HTML/CSS/JS for the frontend.

## Features

- User authentication using JWT (JSON Web Token)
- CRUD operations on customer data
- Pagination, sorting, and searching functionality
- Synchronization with a remote API for customer data updates

## Getting Started

### Prerequisites

Before you begin, ensure you have the following installed:

- [Java Development Kit (JDK)](https://www.oracle.com/java/technologies/javase-downloads.html)
- [MySQL](https://www.mysql.com/)
- [Node.js](https://nodejs.org/)
- [npm](https://www.npmjs.com/)

### Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/your-username/customer-management-app.git

Set up the database:

Create a MySQL database and update the application.properties file in the backend/src/main/resources directory with the database configuration.
Build and run the backend:
cd backend
./mvnw spring-boot:run

The backend server will start on http://localhost:8080.

Install frontend dependencies:
cd frontend
npm install

Run the frontend:
npm start
The frontend will be accessible at http://localhost:3000.
Access the application in your web browser:

Open http://localhost:3000 to use the customer management app.

API Documentation
Authentication API:

Path: /api/authenticate
Method: POST
Body:
{
  "login_id": "your_username",
  "password": "your_password"
}

Customer API:

Path: /api/customers

Methods: GET, POST, PUT, DELETE

Headers: Authorization: Bearer your_jwt_token

Get Customer List:

Path: /api/customers
Method: GET
Add a Customer:

Path: /api/customers
Method: POST
Body:
{
  "first_name": "Jane",
  "last_name": "Doe",
  "street": "Elvnu Street",
  "address": "H no 2",
  "city": "Delhi",
  "state": "Delhi",
  "email": "sam@gmail.com",
  "phone": "12345678"
}

Update a Customer:

Path: /api/customers/{id}
Method: PUT
Body:

{
  // Updated customer data
}

Delete a Customer:

Path: /api/customers/{id}
Method: DELETE

Synchronization
To synchronize customer data with the remote API, use the sync button on the customer list screen.
