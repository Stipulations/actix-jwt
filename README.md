# JWT Authentication with Actix-Web and Rusqlite

This is a simple web application built with Rust's Actix-Web framework and the Rusqlite database. It demonstrates how to implement JWT (JSON Web Token) authentication for user registration, login, and access to protected routes.

## Features

- User registration with username and password
- User login with JWT token generation
- Protected route accessible only with a valid JWT token
- Unprotected route accessible without authentication

### ToDo

- **Password Hashing:**  
  Switch to using `bcrypt` for hashing passwords. Update the registration and login processes to work with hashed passwords.

- **Secret Key Management:**  
  Move the JWT secret key to a .env file and adjust the app to pull it in securely.

- **Async DB Operations:**  
  Use `tokio::task::spawn_blocking` to handle SQLite operations without blocking.

- **Role-Based Access:**  
  Set up roles like `Admin` and `User`, store them in the database, and make sure the JWT includes role info for access control.

- **Error Handling:**  
  Clean up error messages to make them clearer for users and more useful for debugging.


## Getting Started

### Prerequisites

- Rust (latest stable version)
- Cargo (Rust's package manager)

### Installation

1. Clone the repository:

```bash
git clone https://github.com/Stipulations/actix-jwt.git
```

2. Navigate to the project directory:

```bash
cd actix-jwt
```

3. Build the project:

```bash
cargo build
```

### Running the Application

To run the application, use the following command:

```bash
cargo run
```

The application will start running on `http://127.0.0.1:8080`.

## Usage

### Register a New User

Send a POST request to `http://127.0.0.1:8080/register` with the following JSON payload:

```json
{
  "username": "your_username",
  "password": "your_password"
}
```

### Login

Send a POST request to `http://127.0.0.1:8080/login` with the same JSON payload as above. If the credentials are valid, you will receive a JWT token in the response.

### Access Protected Route

To access the protected route at `http://127.0.0.1:8080/protected`, include the JWT token in the `jwt` header of your request.

### Access Unprotected Route

The unprotected route at `http://127.0.0.1:8080/unprotected` can be accessed without any authentication.

## Contributing

Contributions are welcome! If you find any issues or have suggestions for improvement, please open an issue or submit a pull request.