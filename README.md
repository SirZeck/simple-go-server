# Simple Go REST API with In-Memory User Cache

This project is a basic RESTful API built in Go (Golang) for managing user data. It leverages an in-memory cache to efficiently store and retrieve user information.

## Features

- **CRUD Operations:**
    - Create users (`POST /user`)
    - Read users (`GET /user/{id}`)
    - Delete users (`DELETE /user/{id}`)
    - *(Note: Update is not implemented in this example)*
- **In-Memory Cache:** Utilizes a map to store user data for fast access.
- **Concurrency Safe:**  Employs a read-write mutex (`sync.RWMutex`) to handle concurrent access and prevent race conditions.
- **JSON Responses:**  Communicates with clients using JSON formatted data.
- **Basic Error Handling:** Includes preliminary checks for invalid requests (e.g., missing ID, malformed JSON).

## API Endpoints

| Method | Endpoint       | Description             | Request Body (JSON)         | Response (JSON)             |
| ------ | ------------- | ----------------------- | -------------------------- | -------------------------- |
| POST   | `/user`        | Create a new user       | `{ "name": "John Doe" }`   | 204 No Content              |
| GET    | `/user/{id}`   | Retrieve a user by ID   |                            | `{ "name": "John Doe" }`   |
| DELETE | `/user/{id}`   | Delete a user by ID   |                            | 204 No Content              |

## Getting Started

### Prerequisites

- Go (Golang) must be installed on your system.

### Installation & Usage

1. **Clone:** Clone this repository to your local machine.
2. **Build:**  Navigate to the project directory and run `go build`. This will compile the Go code into an executable.
3. **Run:** Execute the compiled binary (e.g., `./your-executable-name`). The server will start listening on `http://localhost:8080`.
4. **Interact:** Use tools like `curl`, `httpie`, or Postman to send requests to the API endpoints.

### Examples (using `curl`)

```bash
# Create a user
curl -X POST -H "Content-Type: application/json" -d '{"name": "Alice Johnson"}' http://localhost:8080/user

# Get a user (replace {id} with the actual user ID)
curl http://localhost:8080/user/{id} 

# Delete a user
curl -X DELETE http://localhost:8080/user/{id}
```

## Limitations

- **Data Volatility:** User data is stored only in memory. When the server shuts down, all data is lost.
- **Simplified Error Handling:** Error responses could be more informative and granular.
- **Missing Update:**  There's no functionality to modify existing user data.

## Potential Enhancements

- **Persistent Storage:** Integrate a database (e.g., SQLite, PostgreSQL) to save user data permanently.
- **Update Endpoint:** Implement a `PUT` or `PATCH` endpoint to allow modifying user details.
- **Authentication/Authorization:** Add security mechanisms to protect user data.
- **Advanced Error Handling:** Provide clearer error messages and consider using standard HTTP status codes more comprehensively.

## Contributing

Contributions are welcome! Feel free to fork this repository, suggest improvements, and submit pull requests.