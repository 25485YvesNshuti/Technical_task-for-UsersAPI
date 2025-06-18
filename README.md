![get user ](https://github.com/user-attachments/assets/89348ee8-adb7-441f-9153-00bf2b70fd66)# User API - Full CRUD

A simple REST API for user management built with Java, Spring Boot, and Maven.  
**Data is stored in-memory.**

---

## Table of Contents

- [Features](#features)
- [Project Setup](#project-setup)
  - [Maven Dependencies](#maven-dependencies)
  - [How to Run](#how-to-run)
- [API Endpoints](#api-endpoints)
  - [Create User](#create-user)
  - [Get User by ID](#get-user-by-id)
  - [Get All Users](#get-all-users)
  - [Update User](#update-user)
  - [Delete User](#delete-user)
- [Example curl Commands](#example-curl-commands)
- [Notes](#notes)

---

## Features

- Create user
- Get user by ID
- List all users
- Update user
- Delete user

---

## Project Setup

### 1. Prerequisites

- **Java 17** or higher installed
- **Maven** installed (check with `mvn -v`)
- (Optional) [Lombok plugin](https://projectlombok.org/setup/) for your IDE (recommended)

### 2. Clone the Repository

```bash
git clone https://github.com/
```

### 3. Maven Dependencies

Your `pom.xml` should include the following essential dependencies:

```xml
<dependencies>
    <!-- Spring Boot Web -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>
    <!-- Lombok (for less boilerplate code) -->
    <dependency>
        <groupId>org.projectlombok</groupId>
        <artifactId>lombok</artifactId>
        <optional>true</optional>
    </dependency>
    <!-- Spring Boot DevTools (optional for fast reloads) -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-devtools</artifactId>
        <scope>runtime</scope>
        <optional>true</optional>
    </dependency>
    <!-- Spring Boot Test (optional, for unit tests) -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-test</artifactId>
        <scope>test</scope>
    </dependency>
</dependencies>
```
**Note:** Spring Boot version `3.5.0` and Java version `17` should be set in your `<parent>` and `<properties>` sections.

---

### 4. How to Run

1. **Build and start the application**  
   ```bash
   mvn spring-boot:run
   ```
   or build JAR and run:
   ```bash
   mvn clean package
   java -jar target/user_api-0.0.1-SNAPSHOT.jar
   ```

2. The app will start at:  
   `http://localhost:8080`

---

## User Fields

- `firstname` (String, required)
- `lname` (String, required)
- `age` (int, required, must be positive)
- `location` (String, required)
- `email` (String, required)
- `id` (String, auto-generated UUID)

---

## API Endpoints

### Create User

- **POST** `/users`
- **Body:**
  ```json
  {
    "firstname": "John",
    "lname": "Doe",
    "age": 25,
    "location": "Kigali",
    "email": "john@example.com"
  }
  ```
- **Success:** `201 Created`, returns user object
- **Error:** `400 Bad Request`, returns `{ "error": "..."}`
![create new user ](https://github.com/user-attachments/assets/43d41f6d-c0ba-4928-91ba-aefdbde6839f)

---

### Get User by ID

- **GET** `/users/{id}`
- **Success:** `200 OK`, returns user object
- **Error:** `404 Not Found`, returns `{ "error": "User not found."}`
![get user by ID](https://github.com/user-attachments/assets/6330730b-e47e-4d24-a410-395b97088a66)

---

### Get All Users

- **GET** `/users`
- **Success:** `200 OK`, returns array of user objects
![get user ](https://github.com/user-attachments/assets/6773110d-5c82-49be-9c09-fddb7fe2bb57)

---

### Update User

- **PUT** `/users/{id}`
- **Body:** (all fields required)
  ```json
  {
    "firstname": "Jane",
    "lname": "Smith",
    "age": 30,
    "location": "Musanze",
    "email": "jane@example.com"
  }
  ```
- **Success:** `200 OK`, returns updated user
- **Error:** `400 Bad Request` or `404 Not Found`
![update user by ID](https://github.com/user-attachments/assets/a0967fef-3088-47ef-a623-13028733d6b8)

---

### Delete User

- **DELETE** `/users/{id}`
- **Success:** `200 OK`, `{ "message": "User deleted successfully." }`
- **Error:** `404 Not Found`, `{ "error": "User not found."}`

---

## Example curl Commands

### Create User
```bash
curl -X POST http://localhost:8080/users \
  -H "Content-Type: application/json" \
  -d '{"firstname":"John","lname":"Doe","age":25,"location":"Kigali","email":"john@example.com"}'
```


### Get All Users
```bash
curl http://localhost:8080/users
```


### Get User by ID
```bash
curl http://localhost:8080/users/<user-id>
```


### Update User
```bash
curl -X PUT http://localhost:8080/users/<user-id> \
  -H "Content-Type: application/json" \
  -d '{"firstname":"Nshuti","lname":"yves","age":30,"location":"Musanze","email":"jane@example.com"}'
```


### Delete User
```bash
curl -X DELETE http://localhost:8080/users/<user-id>
```

---

## Notes

- **All data is stored in-memory** (it will be lost if the server restarts).
- No authentication or database is implemented as per the assignment instructions.
- For development, [Lombok](https://projectlombok.org/) is used to reduce boilerplate code.
- For any issues, ensure your Java and Maven versions are compatible.

---

## License

This project is provided for technical assignment and learning purposes.
