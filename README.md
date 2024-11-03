# API Documentation for User and Author Management System

This documentation provides a detailed guide on how to interact with the **User and Author Management System API**. The system is designed to handle operations such as user registration, authentication, and the management of authors and books, including the creation and maintenance of book-author relationships. The API accepts JSON-formatted input and requires user authentication via tokens to ensure secure interactions.

Each section below outlines the structure of the JSON request payloads for different operations, making it easy for developers to understand and implement these endpoints in their applications.

## Introduction

Access tokens are essential for secure authentication and authorization in web applications, allowing users to perform operations on APIs without exposing sensitive credentials. These tokens are generated upon successful login and must be included in subsequent API requests to prove the user's identity and permissions. This API documentation outlines how to use access tokens for secure interactions with the User and Author Management System, enabling operations such as creating, reading, updating, and deleting resources. Proper handling of access tokens ensures data security and protects user information during API communications.

## CRUD Operations Overview

CRUD represents the fundamental operations required for persistent storage in any application involving data. Here's what each component of CRUD entails and how it applies to the User and Author Management System API:

### Create
- Purpose: The Create operation is used to add new data or resources to the system. This could involve registering a new user, creating an author profile, adding a new book, or establishing a relationship between a book and an author.
- Example Endpoints:
  - POST /api/register – Registering a new user.
  - POST /api/authors – Creating an author profile.
  - POST /api/books – Adding a new book.
  - POST /api/book-author-relations – Creating a book-author relationship.
- Typical Response: Returns a success message and the ID of the created resource.
  
### Read
- Purpose: The Read operation retrieves data from the system. This allows users to view existing information, such as user details, a list of all authors, books, or existing book-author relationships.
- Example Endpoints:
  - POST /api/authenticate – Authenticating a user (validates credentials and retrieves an authentication token).
  - GET /api/authors – Fetching a list of authors.
  - GET /api/books – Viewing a list of books.
  - GET /api/book-author-relations – Listing all book-author relationships.
- Typical Response: Provides a JSON array or object representing the requested data.
  
### Update
- Purpose: The Update operation modifies existing data or resources in the system. This can involve updating user information, changing an author’s name, or editing book details.
- Example Endpoints:
  - PUT /api/authors/{author_id} – Updating an author's information.
  - PUT /api/books/{book_id} – Modifying book details.
- Typical Response: Confirms that the resource was successfully updated with a message.
  
### Delete
- Purpose: The Delete operation removes data or resources from the system. It is used for actions like deleting user accounts, removing author profiles, books, or breaking book-author relationships.
- Example Endpoints:
  - DELETE /api/authors/{author_id} – Deleting an author profile.
  - DELETE /api/books/{book_id} – Removing a book from the system.
  - DELETE /api/book-author-relations/{relation_id} – Deleting a book-author relationship.
- Typical Response: A confirmation message indicating successful deletion of the specified resource.

## Endpoints

## 1. Register a New User (Create)
- Method: POST
- Endpoint: (https://127.0.0.1/library2/public/user/register)
- Request Body:
  
```json
{
  "username": "clint",
  "password": "password"
}
```
- Response:

```json
{
  "status": "success",
  "data": null
}
```

## 2. Authenticate a User (Read)
- Method: POST
- Endpoint: (https://127.0.0.1/library2/public/user/auth)
- Request Body:

```json
{
    "username": "clint",
    "password": "password123"
}
```
- Response:

```json
{
  "status": "fail",
  "data": {
  "title": "Authentication Failed"
  }
}
```
- Method: POST
- Endpoint: (https://127.0.0.1/library2/public/user/auth)
- Request Body:

```json
{
    "username": "clint",
    "password": "password123"
}
```
- Response:
```json
{
  "status": "success",
  "Access_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vbGlicmFyeS5vcmciLCJhdWQiOiJodHRwOi8vbGlicmFyeS5jb20iLCJpYXQiOjE3Mjc2NjY2NjYsImV4cCI6MTczMDI1ODY2NiwiZGF0YSI6eyJ1c2VyaWQiOjEwNn19.9o830kVZ8iSxAYCgxDu_G7D_K5IXaBlKjBEvRR90mi8"
  "data": null
}
```
## 3. Create an Author (Create)
- Method: POST
- Endpoint:(https://127.0.0.1/library2/public/authors)
- Request Body:
{
    "name": "clintcute",
    "userid": 110,
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vbGlicmFyeS5vcmciLCJhdWQiOiJodHRwOi8vbGlicmFyeS5jb20iLCJpYXQiOjE3Mjc2NjcwMDMsImV4cCI6MTcyNzY3MDYwMywiZGF0YSI6eyJ1c2VyaWQiOjEwNn19.-SEGOTA6Smk_b8P-sJd4JGMi18Y0qq1IHr9ujrkKI8E"
}
- Response:
{
    "message": "Author created successfully.",
    "author_id": 1
} 
## 4. Get All Authors (Read)
- Method: GET
- Endpoint: (https://127.0.0.1/library2/public/authors/get)
- Request Body:
{
    "userid": 110,
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vbGlicmFyeS5vcmciLCJhdWQiOiJodHRwOi8vbGlicmFyeS5jb20iLCJpYXQiOjE3Mjc2NjcwMDMsImV4cCI6MTcyNzY3MDYwMywiZGF0YSI6eyJ1c2VyaWQiOjEwNn19.-SEGOTA6Smk_b8P-sJd4JGMi18Y0qq1IHr9ujrkKI8E"
} 
- Response:
[
  {
    "author_id": 1,
    "name": "Clint Agumo"
  },
  {
    "author_id": 2,
    "name": "Cha Nudas"
  }
]

## 5. Update an Author (Update)
- Method: PUT
- Endpoint: (https://127.0.0.1/library2/public/authors/update/2)
- Request Body:
{
    "name": "Clint Cute",
    "userid": 110,
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vbGlicmFyeS5vcmciLCJhdWQiOiJodHRwOi8vbGlicmFyeS5jb20iLCJpYXQiOjE3Mjc2NjcwMDMsImV4cCI6MTcyNzY3MDYwMywiZGF0YSI6eyJ1c2VyaWQiOjEwNn19.-SEGOTA6Smk_b8P-sJd4JGMi18Y0qq1IHr9ujrkKI8E"
}
- Response:
{
    "message": "Author updated successfully."
}

## 6. Delete an Author (Delete)
- Method: DELETE
- Endpoint:(https://127.0.0.1/library2/public/authors/delete/3)
- Request Body:
{
    "userid": 110,
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vbGlicmFyeS5vcmciLCJhdWQiOiJodHRwOi8vbGlicmFyeS5jb20iLCJpYXQiOjE3Mjc2NjcwMDMsImV4cCI6MTcyNzY3MDYwMywiZGF0YSI6eyJ1c2VyaWQiOjEwNn19.-SEGOTA6Smk_b8P-sJd4JGMi18Y0qq1IHr9ujrkKI8E"
}
- Response:
{
    "message": "Author deleted successfully."
}

## 7. Create A Book (Create)
- Method: POST
- Endpoint: (https://127.0.0.1/library2/public/books)
- Request Body:
{
    "title": "The Vampire",
    "author_id": 1,
    "userid": 110,
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vbGlicmFyeS5vcmciLCJhdWQiOiJodHRwOi8vbGlicmFyeS5jb20iLCJpYXQiOjE3Mjc2NjcwMDMsImV4cCI6MTcyNzY3MDYwMywiZGF0YSI6eyJ1c2VyaWQiOjEwNn19.-SEGOTA6Smk_b8P-sJd4JGMi18Y0qq1IHr9ujrkKI8E"
}
- Response:
{
    "message": "Book created successfully.",
    "book_id": 1
}

## 8. Get All Books (Read)
- Method: GET
- Endpoint:(https://127.0.0.1/library2/public/books/get)
- Request Body:
{
    "userid": 110,
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vbGlicmFyeS5vcmciLCJhdWQiOiJodHRwOi8vbGlicmFyeS5jb20iLCJpYXQiOjE3Mjc2NjcwMDMsImV4cCI6MTcyNzY3MDYwMywiZGF0YSI6eyJ1c2VyaWQiOjEwNn19.-SEGOTA6Smk_b8P-sJd4JGMi18Y0qq1IHr9ujrkKI8E"
}
- Response:
[
  {
    "book_id": 1,
    "title": "The Vampire",
    "author_id": 1
  },
  {
    "book_id": 2,
    "title": "The Man",
    "author_id": 2
  }
]

## 9.Update A Book (Update)
- Method: PUT
- Endpoint: (https://127.0.0.1/library2/public/books/update/5)
- Request Body:
{
    "title": "Disney",
    "author_id": 1,
    "userid": 1,
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vbGlicmFyeS5vcmciLCJhdWQiOiJodHRwOi8vbGlicmFyeS5jb20iLCJpYXQiOjE3Mjc2NjcwMDMsImV4cCI6MTcyNzY3MDYwMywiZGF0YSI6eyJ1c2VyaWQiOjEwNn19.-SEGOTA6Smk_b8P-sJd4JGMi18Y0qq1IHr9ujrkKI8E"
}
- Response:
{
    "message": "Book updated successfully."
}

## 10. Delete A Book (Delete)
- Method: DELETE
- Endpoint:(https://127.0.0.1/library2/public/books/delete/3)
- Request Body:
{
    "userid": 110,
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vbGlicmFyeS5vcmciLCJhdWQiOiJodHRwOi8vbGlicmFyeS5jb20iLCJpYXQiOjE3Mjc2NjY5NjIsImV4cCI6MTcyNzY3MDU2MiwiZGF0YSI6eyJ1c2VyaWQiOjEwNn19.UN8mB6zOCvzM5y9JI-ogggW9edwY5WqfoQLu3C5XXqg"
}
- Response:
{
    "message": "Book deleted successfully."
}

## 11. Create Book-Authors Relations (Create)
- Method: POST
- Endpoint: (https://127.0.0.1/library2/public/books_authors)
- Request Body:
{
    "book_id": 1,
    "author_id": 1,
    "userid": 110,
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vbGlicmFyeS5vcmciLCJhdWQiOiJodHRwOi8vbGlicmFyeS5jb20iLCJpYXQiOjE3Mjc2NjY5NjIsImV4cCI6MTcyNzY3MDU2MiwiZGF0YSI6eyJ1c2VyaWQiOjEwNn19.UN8mB6zOCvzM5y9JI-ogggW9edwY5WqfoQLu3C5XXqg"
}
- Response:
{
    "message": "Book-author relation created successfully."
}

## 12. Get All Book Relations (Read)
- Method: GET
- Endpoint: (https://127.0.0.1/library2/public/books_authors/get)
- Request Body:
{
    "userid": 110,
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vbGlicmFyeS5vcmciLCJhdWQiOiJodHRwOi8vbGlicmFyeS5jb20iLCJpYXQiOjE3Mjc2NjY5NjIsImV4cCI6MTcyNzY3MDU2MiwiZGF0YSI6eyJ1c2VyaWQiOjEwNn19.UN8mB6zOCvzM5y9JI-ogggW9edwY5WqfoQLu3C5XXqg"
}
- Response:
[
    {
        "relation_id": 1,
        "book_id": 1,
        "author_id": 1
    },
    {
        "relation_id": 2,
        "book_id": 2,
        "author_id": 2
    }
]

## 13. Delete Book-Author Relations (Delete)
- Method: DELETE
- Endpoint: (https://127.0.0.1/library2/public/books_authors/delete/1)
- Request Body:
{
    "userid": 110,
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vbGlicmFyeS5vcmciLCJhdWQiOiJodHRwOi8vbGlicmFyeS5jb20iLCJpYXQiOjE3Mjc2NjY5NjIsImV4cCI6MTcyNzY3MDU2MiwiZGF0YSI6eyJ1c2VyaWQiOjEwNn19.UN8mB6zOCvzM5y9JI-ogggW9edwY5WqfoQLu3C5XXqg"
}
- Response:
{
    "message": "Book-author relation deleted successfully."
}

# Author 
Clint Darryn B. Agumo

