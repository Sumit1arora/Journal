# Journal

A secure Spring Boot backend for managing personal journal entries with user authentication and role-based access.

## About

The Journal project is a robust Spring Boot application designed to provide a secure backend for a personal journaling system. It leverages Spring Security for authentication and authorization, allowing users to manage their journal entries with role-based access control. Data is persisted using MongoDB, ensuring efficient storage and retrieval of journal content.

## Features

- **User Management**: Secure registration for new users and creation of admin accounts.
- **Authentication & Authorization**: Built-in Spring Security with JWT (implied by typical Spring Security usage for REST APIs, though not explicitly seen as JWT in config, basic auth is configured) and role-based access control (USER, ADMIN).
- **Journal Entry Management**: Comprehensive CRUD operations for personal journal entries.
- **MongoDB Integration**: Seamless data persistence using Spring Data MongoDB.
- **Transactional Operations**: Ensures data consistency for complex operations involving users and their journal entries.
- **RESTful API**: Provides a well-structured set of endpoints for client interaction.

## Tech Stack

- **Backend**: Java 17, Spring Boot 3.x
- **Frameworks**: Spring Web, Spring Security, Spring Data MongoDB
- **Database**: MongoDB
- **Build Tool**: Maven
- **Utilities**: Lombok

## Installation

To get a local copy up and running, follow these simple steps.

### Prerequisites
Make sure you have the following installed:
*   Java Development Kit (JDK) 17 or higher
*   Apache Maven 3.x
*   MongoDB instance (local or remote)

### Steps
1.  **Clone the repository**
    ```bash
git clone https://github.com/Sumit1arora/Journal
cd Journal
    ```
2.  **Configure MongoDB**
    Ensure your MongoDB instance is running and configured correctly. By default, Spring Boot connects to `mongodb://localhost:27017/test`. You might need to update `application.properties` or `application.yml` for custom configurations (e.g., database name, credentials).

3.  **Build the project**
    ```bash
mvn clean install
    ```
4.  **Run the application**
    ```bash
mvn spring-boot:run
    ```
    The application will start on `http://localhost:8080` by default.

## Usage

Once the application is running, you can interact with it via its RESTful API. Below are common usage scenarios:

### 1. Register a new user
Before accessing protected endpoints, you need to create a user account. Send a `POST` request to the `/public/createuser` endpoint.

### 2. Authenticate
For protected endpoints (`/journal`, `/user`, `/admin`), you will need to authenticate using HTTP Basic authentication with the username and password of a registered user.

### 3. Manage Journal Entries
After authentication, you can use the `/journal` endpoints to create, retrieve, update, and delete your journal entries.

### 4. Admin Operations
Users with the `ADMIN` role can access the `/admin` endpoints to manage users (e.g., view all users, create new admin accounts).

## API Reference

The application exposes the following RESTful API endpoints:

| Method | Endpoint                    | Description                                        | Authentication | Roles       |
| :----- | :-------------------------- | :------------------------------------------------- | :------------- | :---------- |
| `POST` | `/public/createuser`        | Registers a new user account.                      | None           | None        |
| `GET`  | `/journal`                  | Retrieves all journal entries for the authenticated user. | Required       | `USER`, `ADMIN` |
| `POST` | `/journal`                  | Creates a new journal entry for the authenticated user. | Required       | `USER`, `ADMIN` |
| `GET`  | `/journal/id/{myId}`        | Retrieves a specific journal entry by ID for the authenticated user. | Required       | `USER`, `ADMIN` |
| `PUT`  | `/journal/id/{myId}`        | Updates an existing journal entry by ID for the authenticated user. | Required       | `USER`, `ADMIN` |
| `DELETE` | `/journal/id/{myId}`        | Deletes a specific journal entry by ID for the authenticated user. | Required       | `USER`, `ADMIN` |
| `PUT`  | `/user`                     | Updates the details of the authenticated user.     | Required       | `USER`, `ADMIN` |
| `DELETE` | `/user`                     | Deletes the authenticated user's account.          | Required       | `USER`, `ADMIN` |
| `GET`  | `/admin/all-users`          | Retrieves a list of all registered users.          | Required       | `ADMIN`     |
| `POST` | `/admin/create-admin`       | Creates a new user with `ADMIN` role.              | Required       | `ADMIN`     |

## Project Structure

```
.gitattributes/
.gitignore/
.mvn/
  └── wrapper
journal.log/
mvnw/
mvnw.cmd/
pom.xml/
src/
  ├── main
  └── test
```

## Contributing

Contributions are what make the open-source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement".
Don't forget to give the project a star! Thanks again!

1.  Fork the Project
2.  Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3.  Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4.  Push to the Branch (`git push origin feature/AmazingFeature`)
5.  Open a Pull Request

## License

License not specified.

