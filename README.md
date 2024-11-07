# API Documentation for User and Author Management System

This documentation provides a detailed guide on how to interact with the **User and Author Management System API**. The system is designed to handle operations such as user registration, authentication, and the management of authors and books, including the creation and maintenance of book-author relationships. The API accepts JSON-formatted input and requires user authentication via tokens to ensure secure interactions.

Each section below outlines the structure of the JSON request payloads for different operations, making it easy for developers to understand and implement these endpoints in their applications.

## Introduction to the API Library 

#### Purpose: 
-   The purpose of this API Library is to simplify and streamline the management tasks of library administrators by providing a centralized system for managing books and monitoring users. It enables admins to efficiently     add, update, and delete book records, as well as track user activities and lending history. By automating routine tasks, the API reduces manual effort, ensures data consistency, and enhances the library’s operational     efficiency. With robust authentication and error-handling mechanisms, it secures all operations, preventing unauthorized access and protecting data integrity. This makes the API an essential tool for modern library       management.
  
#### Core Functions:

- Add, update, and delete book records.
- Monitor and manage library user activities.

#### Authentication:
- Supports various authentication methods such as :
   ##### 1. *API Keys*:   **Simple token-based method for access.**
   ##### 2. *OAuth*:      **More secure, token-based authentication for resource access.**
   ##### 3. *Basic Auth*: **Username and password-based authentication.**

#### Error Handling:
- Detailed error codes and structured response formats are provided for common error scenarios to assist in troubleshooting and improving user experience.

#### Access Tokens:
- Essential for secure authentication and authorization.
- Tokens are generated upon successful login and must be included in subsequent API calls.
- Allow API users to perform operations without exposing sensitive credentials, ensuring data security.

#### Security Emphasis:
- Proper token management helps protect user data and maintain the integrity of interactions within the system.

#### Documentation Purpose:
- This guide provides comprehensive details on using access tokens, performing CRUD operations, and handling authentication and errors to securely interact with the API and maintain reliable system functionality.


## CRUD Operations Overview

CRUD represents the fundamental operations required for persistent storage in any application involving data. Here's what each component of CRUD entails and how it applies to the User and Author Management System API:

# Create

### Purpose: 
- The Create operation is used to add new data or resources to the system. This could involve registering a new user, creating an author profile, adding a new book, or establishing a relationship between a book and an author.

### Example Endpoints:

  - POST /api/register – Registering a new user.
  - POST /api/authors – Creating an author profile.
  - POST /api/books – Adding a new book.
  - POST /api/book-author-relations – Creating a book-author relationship.
    
### Typical Response: 
- Returns a success message and the ID of the created resource.
  
# Read

### Purpose:
- The Read operation retrieves data from the system. This allows users to view existing information, such as user details, a list of all authors, books, or existing book-author relationships.

### Example Endpoints:
  
  - POST /api/authenticate – Authenticating a user (validates credentials and retrieves an authentication token).
  - GET /api/authors – Fetching a list of authors.
  - GET /api/books – Viewing a list of books.
  - GET /api/book-author-relations – Listing all book-author relationships.

### Typical Response:
- Provides a JSON array or object representing the requested data.
  
# Update

### Purpose: 
- The Update operation modifies existing data or resources in the system. This can involve updating user information, changing an author’s name, or editing book details.

### Example Endpoints:

  - PUT /api/authors/{author_id} – Updating an author's information.
  - PUT /api/books/{book_id} – Modifying book details.
  
### Typical Response: 
- Confirms that the resource was successfully updated with a message.
  
# Delete

### Purpose: 
- The Delete operation removes data or resources from the system. It is used for actions like deleting user accounts, removing author profiles, books, or breaking book-author relationships.

### Example Endpoints:

  - DELETE /api/authors/{author_id} – Deleting an author profile.
  - DELETE /api/books/{book_id} – Removing a book from the system.
  - DELETE /api/book-author-relations/{relation_id} – Deleting a book-author relationship.
  
### Typical Response: 
- A confirmation message indicating successful deletion of the specified resource.

# Endpoints

## 1. Register a New User (Create)
- **Method**: POST
- **Description**: This endpoint allows new users to create an account in the system by providing a username and password. It stores user credentials securely and sets up the profile for future authenticated interactions.
- **Endpoint**: (https://127.0.0.1/library2/public/user/register)
- **Request Body**:
  
```json
{
  "username": "clintagumo",
  "password": "password"
}
```
- **Response**:

```json
{
  "status": "success",
  "data": null
}
```

## 2. Authenticate a User (Read)
- **Method**: POST
- **Description**: This endpoint verifies user credentials (username and password) and, upon successful verification, returns an access token. This token is essential for secure access and must be used for any subsequent 
  API requests to ensure authenticated communication.
- **Endpoint**: (https://127.0.0.1/library2/public/user/auth)
- **Request Body**:

```json
{
  "username": "clintagumo",
  "password": "password"
}
```
- **Response**:

```json
{
  "status": "success",
  "access_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vbGlicmFyeS5vcmciLCJhdWQiOiJodHRwOi8vbGlicmFyeS5jb20iLCJpYXQiOjE3Mz2DbSA0fkS2royUvBHYeO1Hmf1zvev4HT0hsoOQBgQag",
  "data": null
}
```

## Error(Authentication Failed)

- **Method**: POST
- **Endpoint**: (https://127.0.0.1/library2/public/user/auth)
- **Request Body**:

```json
{
    "username": "clint",
    "password": "password123"
}
```
- **Response**:

```json
{
  "status": "fail",
  "data": {
  "title": "Authentication Failed"
  }
}
```
## 3. Create an Author (Create)
- **Method**: POST
- **Description**: This endpoint enables users to add new author profiles to the library system. It requires the user to provide the author's details and an access token for authentication, ensuring only authorized users 
  can create new entries.
- **Endpoint**:(https://127.0.0.1/library2/public/authors)

- **Request Body**:

```json
{
    "name": "cagumo",
    "userid": 110,
    "token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vbGlicmFyeS5vcmciLCJhdWQiOiJodHRwOi8vbGlicmFyeS5jb20iLCJpYXQiOjETczMDk3OTczOCwidXNlcmlkIjoiMTI0.k5GCuWhTeGqi3mu2vQwNuSmZw5WWuvFuOTJNla8gBNQ  "
}
```
- **Response**:
```json
{
  "status": "success",
  "data": null,
  "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vbGlicmF20iLCJpYXQiOjE3MzA5NzcxNTAsImV4cCI6MTczMDk4MDc1MCwidXNlcmlkIjoxMTB9.UnP8Bkhupcqi4Ur0Fz-Kbd4cjQQG6lWowmMkwSio-44"
}                                                                                                                                
```
## 4. Get All Authors (Read)
- **Method**: GET
- **Description**: This endpoint fetches a complete list of authors stored in the library database. It requires authentication to protect the integrity of the data and ensure only authorized users can access this 
  information.
- **Endpoint**: (https://127.0.0.1/library2/public/authors/get)
  
- **Request Body**:

```json
{
    "userid": 110,
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vbGlicmFyeS5vcmciLCJhdWQiOiJJpYXQiOjE3MzA5NzYyNTEsImV4cCI6MTczMDk3OTg1MSwidXNlcmlkIjoiMTIyIn0.o7puTINfaR2qhwemqrk4qgdM1LdPuDtBb4WIexSB2J8"
}

``` 
- **Response**:

```json
{
  "status": "success",
  "data": [
    {
      "authorid": "4",
      "name": "cha"
    },
    {
      "authorid": "5",
      "name": "Author E"
    },
    {
      "authorid": "6",
      "name": "Author F"
    },
    {
      "authorid": "7",
      "name": "Author G"
    },
    {
      "authorid": "8",
      "name": "Author H"
    },
    {
      "authorid": "109",
      "name": "cagumo"
    },
    {
      "authorid": "110",
      "name": "cagumo"
    }
  ],
      "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.LCJhdWQiOiJodHRwOi8vbGlicmFyeS5jb20iLCJpYXQiOjE3MzA5NzcyNjcsImV4cCI6MTczMDk4MDg2NywidXNlcmlkIjoxMTB9.K- S2K_hLvH8lGJw_YrMigRHUe3UdeoUROpV2fLxruSg"
}
``` 

## 5. Update an Author (Update)
- **Method**: PUT
- **Description**: This endpoint allows users to modify the details of an existing author profile. Users must provide the updated information, the author’s ID, and an access token, ensuring that only authorized updates 
  are permitted.
- **Endpoint**: (https://127.0.0.1/library2/public/authors/update/1)
- **Request Body**:

```json
{
    "name": "Clint",
    "userid": 110,
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vbGlicmFyeS5vcjb20iLCJpYXQiOjE3MzA5NzYzODcsImV4cCI6MTczMDk3OTk4NywidXNlcmlkIjoiMTIyIn0-2DbSA0fkS2royUvBHYeO1Hmf1zvev4HT0hsoOQBgQag"
}
``` 
- **Response**:

```json
{
  "status": "success",
  "data": null,
  "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.vbGlicmFyeS5vcmciLCJhdWQiOiJodHRwOi8vbGlicmFyeS5jb20iLCJpYXQiOjE3MzA5NzY0MTcsImV4cCI6MTczMDk4MDAxNywidXNlcmlkIjoxMTB9-bvUKMi_Jq7SFLn8ssOGD6k91KyE0"
}
```
## Updated Author(7)

- **Response**:
```json
{
  "status": "success",
  "data": [
    {
      "authorid": "4",
      "name": "cha"
    },
    {
      "authorid": "5",
      "name": "Author E"
    },
    {
      "authorid": "6",
      "name": "Author F"
    },
    {
      "authorid": "7",
      "name": "Clintcutemo"
    },
    {

    {
      "authorid": "110",
      "name": "cagumo"
    }
  ],
  "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJvbGlicmFyeS5jb20iLCJpYXQiOjE3MzA5Nzc5MTYsImV4cCI6MTczMDk4MTUxNiwidXNlcmlkIjoxMTB9-Qqb6u00Q4px8JAV1MncYt3IXoXecz9sPoGqK-bW2HDQ"
}
```

## 6. Delete an Author (Delete)
- **Method**: DELETE
- **Description**: This endpoint enables users to remove an author profile from the system. The user must provide the author’s ID and an authentication token to confirm the deletion, preventing unauthorized removals.
- **Endpoint**:(https://127.0.0.1/library2/public/authors/delete/3)
  
- **Request Body**:

```json
{
    "userid": 110,
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vbGlicmFyeS5vcmciLCJhdWQiOiJodHRwOi8vbGlicmFyeS5jb20iLCJpYXQiOjE3MzA5NzgyOTQsImV4cCI6MTczMDk4MTg5NCwidXNlcmlkIjoiMTIy- L6eRDPvzfSJHD4acke00aSA"
}
``` 
- **Response**:

```json
{
  "status": "success",
  "data": null,
  "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MimciLCJhdWQiOiJicmFyeS5jb20iLCJpYXQiOjE3MzA5NzgzMzAsImV4cCI6MTczMDk4MTkzMCwidXNlcmlkIjoxMTB9-RT_a9J0a8wW1LJV9NViF4zazENQDZYPSJywRIgggReI"
}
```
## Deleted An Author (# 7)

```json
{
  "status": "success",
  "data": [
    {
      "authorid": "4",
      "name": "cha"
    },
    {
      "authorid": "5",
      "name": "Author E"
    },
    {
      "authorid": "6",
      "name": "Author F"
    },
    {
      "authorid": "8",
      "name": "Author H"
    },
    {
      "authorid": "9",
      "name": "Author I"
    },
  ],
  "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vbvbGlicmFyeS5jb20iLCJpYXQiOjE3MzA5Nzg1MjEsImV4cCI6MTczMDk4MjEyMSwidXNlcmlkIjoxMTB9-xQHfINps8ZWzvalmKKsSWCyJpB71GoUBT3B0Bf5KfCc"
}
```

## 7. Create A Book (Create)
- **Method**: POST
- **Description**: This endpoint allows users to add new book entries to the system by providing the book’s title and linking it to an existing author. Authentication is required to ensure only authorized users can 
  create new book records.
- **Endpoint**: (https://127.0.0.1/library2/public/books)
  
- **Request Body**:

```json
{
    "title": "The Vampire",
    "author_id": 1,
    "userid": 110,
    "token": 
    "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vbGlicmFyeS5vcmciLCJhdWQiOiJodHRwOi8vbGlicmFyeS5jb20iLCJpYXQiOjE3Mjc2NjcwMDMsImV4cCI6MTcyNzY3MDYwMywiZGF0YSI6eyJ1c2VyaWQiOjEwNn19.sJd4JGMi18Y0qq1IHr9ujrkKI8E"
}
```
- **Response**:

```json
{
    "message": "Book created successfully.",
    "book_id": 1
}
```
## 8. Get All Books (Read)
- **Method**: GET
- **Description**: This endpoint retrieves a comprehensive list of all books available in the system. It requires an authentication token, ensuring that only authorized users can access the database.
- **Endpoint**:(https://127.0.0.1/library2/public/books/get)
  
- **Request Body**:

```json
{
    "userid": 110,
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vbGlicmFyeS5vcmciLCJhdWQiOiJodHRwOi8vbGlicmFyeS5jb20iLCJpYXQiOjE3Mjc2NjcwMDMsImV4cCI6MTcyNzY3MDYwMywiZGF0YSI6eyJ1c2VyaWQiOjEwNn19.-SEGOTA6Smk_b8P-          sJd4JGMi18Y0qq1IHr9ujrkKI8E"
}
```
- **Response**:

```json
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
```

## 9.Update A Book (Update)
- **Method**: PUT
- **Description**: This endpoint lets users modify the details of an existing book record, such as its title or associated author. The request must include the book's ID, updated details, and an access token for secure 
  authorization.
- **Endpoint**: (https://127.0.0.1/library2/public/books/update/5)
  
- **Request Body**:

```json
{
    "title": "Disney",
    "author_id": 1,
    "userid": 1,
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vbGlicmFyeS5vcmciLCJhdWQiOiJodHRwOi8vbGlicmFyeS5jb20iLCJpYXQiOjE3Mjc2NjcwMDMsImV4cCI6MTcyNzY3MDYwMywiZGF0YSI6eyJ1c2VyaWQiOjEwNn19.-SEGOTA6Smk_b8P-          sJd4JGMi18Y0qq1IHr9ujrkKI8E"
}
```
- **Response**:

```json
{
    "message": "Book updated successfully."
}
```
## 10. Delete A Book (Delete)
- **Method**: DELETE
- **Description**: This endpoint allows users to delete a book entry from the system. It requires the book’s ID and a valid access token to ensure that only authorized users can perform deletions.
- **Endpoint**:(https://127.0.0.1/library2/public/books/delete/3)

- **Request Body**:

```json
{
    "userid": 110,
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vbGlicmFyeS5vcmciLCJhdWQiOiJodHRwOi8vbGlicmFyeS5jb20iLCJpYXQiOjE3Mjc2NjY5NjIsImV4cCI6MTcyNzY3MDU2MiwiZGF0YSI6eyJ1c2VyaWQiOjEwNn19.UN8mB6zOCvzM5y9JI-        ogggW9edwY5WqfoQLu3C5XXqg"
}
```
- **Response**:

```json
{
    "message": "Book deleted successfully."
}
```
## 11. Create Book-Authors Relations (Create)
- **Method**: POST
- **Description**: This endpoint enables users to create a relationship between a book and an author, linking them in the database. An access token is needed for authentication, ensuring only authorized users can 
  establish these relationships.
- **Endpoint**: (https://127.0.0.1/library2/public/books_authors)
  
- **Request Body**:

```json
{
    "book_id": 1,
    "author_id": 1,
    "userid": 110,
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vbGlicmFyeS5vcmciLCJhdWQiOiJodHRwOi8vbGlicmFyeS5jb20iLCJpYXQiOjE3Mjc2NjY5NjIsImV4cCI6MTcyNzY3MDU2MiwiZGF0YSI6eyJ1c2VyaWQiOjEwNn19.UN8mB6zOCvzM5y9JI-        ogggW9edwY5WqfoQLu3C5XXqg"
}
```
- **Response**:

```json
{
    "message": "Book-author relation created successfully."
}
```
## 12. Get All Book Relations (Read)
- **Method**: GET
- **Description**: This endpoint retrieves all existing relationships between books and authors from the database. Authentication is required to access this information, maintaining the security and integrity of data.
- **Endpoint**: (https://127.0.0.1/library2/public/books_authors/get)

- **Request Body**:

```json
{
    "userid": 110,
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vbGlicmFyeS5vcmciLCJhdWQiOiJodHRwOi8vbGlicmFyeS5jb20iLCJpYXQiOjE3Mjc2NjY5NjIsImV4cCI6MTcyNzY3MDU2MiwiZGF0YSI6eyJ1c2VyaWQiOjEwNn19.UN8mB6zOCvzM5y9JI-        ogggW9edwY5WqfoQLu3C5XXqg"
}
```
- **Response**:

```json
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
```
## 13. Delete Book-Author Relations (Delete)
- **Method**: DELETE
- **Description**: This endpoint allows users to remove a specific relationship between a book and an author. The request requires an access token and the relevant IDs, ensuring that only authorized users can manage 
  these associations.
- **Endpoint**: (https://127.0.0.1/library2/public/books_authors/delete/1)
  
- **Request Body**:

```json
{
    "userid": 110,
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vbGlicmFyeS5vcmciLCJhdWQiOiJodHRwOi8vbGlicmFyeS5jb20iLCJpYXQiOjE3Mjc2NjY5NjIsImV4cCI6MTcyNzY3MDU2MiwiZGF0YSI6eyJ1c2VyaWQiOjEwNn19.UN8mB6zOCvzM5y9JI-        ogggW9edwY5WqfoQLu3C5XXqg"
}
```
- **Response**:

```json
{
    "message": "Book-author relation deleted successfully."
}
```

# Authored By
```json
Clint Darryn B. Agumo
```

