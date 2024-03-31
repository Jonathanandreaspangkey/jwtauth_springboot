# Spring Boot JWT Authentication API Documentation

## Overview
This Spring Boot JWT Authentication API provides endpoints for user registration and authentication using JSON Web Tokens (JWT). It allows users to register, authenticate, and receive JWT tokens for accessing protected resources within the system.

## Architecture and Flow
<img width="606" alt="jwtservicee" src="https://github.com/Jonathanpangkey/jwtauth_springboot/assets/102292312/3c646c86-c4f3-4628-8654-8ea3d201788c">
<br /> <br />
In a Spring application, the JWT authentication filter is the initial point of execution. It validates the JWT token, starting by checking if the token is present. If missing, it sends a 403 response. Next, it fetches user details from the database based on the token's subject (user email). If the user doesn't exist, it returns a 403; otherwise, it proceeds to validate the token against the user. If the token is invalid (expired or not for that user), it sends a 403; otherwise, it updates the security context holder, marking the user as authenticated. This allows subsequent filters to recognize the authenticated user. Finally, the request is dispatched to the controller for further processing, such as accessing services or databases, and generating a response. This flow ensures secure authentication and access control within the application.

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

