# Spring Boot JWT Authentication API Documentation

## Overview
This Spring Boot JWT Authentication API provides endpoints for user registration and authentication using JSON Web Tokens (JWT). It allows users to register, authenticate, and receive JWT tokens for accessing protected resources within the system.

## Architecture and Flow
<img width="606" alt="jwtservicee" src="https://github.com/Jonathanpangkey/jwtauth_springboot/assets/102292312/3c646c86-c4f3-4628-8654-8ea3d201788c">
<br/> <br/>
In this application architecture, the JwtAuthenticationFilter intercepts incoming HTTP requests to extract and validate JWT tokens, setting up Spring Security's authentication context if valid. JwtService provides methods for JWT token generation, parsing, and validation. The UserDetailsService interface retrieves user details for authentication, while the AuthenticationController exposes HTTP endpoints for user registration and authentication, delegating processing to the AuthenticationService, which handles business logic for user registration, password encoding, database interactions, and JWT token generation. The Controller layer receives incoming requests and maps them to service methods, while the Service layer orchestrates interactions between components, performing validation and enforcing business rules. Finally, the Servlet Container hosts and manages servlets, filters, and listeners, routing requests to the appropriate components based on the request URL, ensuring a secure and efficient flow of data throughout the application.

## Data Models
- **User:**
  - Firstname: String
  - Lastname: String
  - Email: String
  - Password: String (encoded)
  - Role: Enum (USER, ADMIN)

## Endpoints Overview

The application provides the following endpoints for user registration and authentication:

1. **User Registration Endpoint**
   - URL: `/api/v1/auth/register`
   - Method: `POST`
   - Description: Registers a new user with the provided details.
   - Request Body:
     ```json
     {
       "firstname": "string",
       "lastname": "string",
       "email": "string",
       "password": "string"
     }
     ```
   - Response:
     ```json
     {
       "token": "string"
     }
     ```

2. **User Authentication Endpoint**
   - URL: `/api/v1/auth/authenticate`
   - Method: `POST`
   - Description: Authenticates a user with the provided credentials.
   - Request Body:
     ```json
     {
       "email": "string",
       "password": "string"
     }
     ```
   - Response:
     ```json
     {
       "token": "string"
     }
     ```
3. **Demo Endpoint**
   - URL: `/api/v1/demo-controller`
   - Method: `GET`
   - Description: A demo endpoint for testing purposes.


## Clone
If you want to use or modify this app:

1. Clone the project repository.
2. Ensure that PostgreSQL is installed and running.
3. Update the database configuration in `application.properties` file if necessary.
4. Run the application with your favorite IDE (preferred IntelliJ IDEA)
5. Test the application with testing tools like postman or by sending HTTP requests directly from your client application.

