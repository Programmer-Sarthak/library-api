# In-Memory Library API - Fresher Hiring Challenge

## 1. Project Title & Goal
This is a Spring Boot REST API that manages a book inventory using strictly in-memory storage. It allows users to add, retrieve, search, and delete books without an external database, fulfilling the requirement for a solution that runs locally without external dependencies.

## 2. Setup Instructions
To run this project locally, follow these steps:

1.  **Clone the repository:**
    ```bash
    git clone <YOUR_GITHUB_REPO_LINK_HERE>
    ```
2.  **Navigate to the project directory:**
    ```bash
    cd library-api
    ```
3.  **Run the application:**
   * **Using Maven Wrapper (Windows):**
       ```bash
       .\mvnw spring-boot:run
       ```
   * **Using Maven Wrapper (Mac/Linux):**
       ```bash
       ./mvnw spring-boot:run
       ```
4.  The server will start at `http://localhost:8080`.

## 3. The Logic (How I thought)
**Why did I choose this approach?**
I chose **Spring Boot** because it is the industry standard for building robust REST APIs. For the storage layer, I utilized a static `ArrayList` in Java to strictly adhere to the "In-Memory" constraint. This allows for O(1) complexity for adding items and flexible filtering using Java Streams for the search functionality.

**What was the hardest bug I faced?**
The hardest challenge was ensuring the "Search by Year" feature worked robustly. Specifically, handling cases where no books matched the query. I resolved this by using Java Streams `filter()` and `collect(Collectors.toList())`, ensuring the API returns a proper empty JSON array `[]` rather than a null response or error when no matches are found.

## 4. Output Screenshots
Below are the proofs of the API working successfully.

**Screenshot 1: Successful GET Request (Search)**
![Search Proof](ScreenShots%20(Postmen)/screenshot%201.png)

**Screenshot 2: Successful POST Request (Add Book)**
![Add Book Proof](ScreenShots%20(Postmen)/screenshot%202.png)

*(Note: The above images show the Postman response returning a 200 OK status)*

## 5. Future Improvements
If I had 2 more days to work on this, I would add:
1.  **Input Validation:** Implement `@Valid` annotations to prevent invalid data (e.g., negative years).
2.  **Unit Testing:** Add JUnit tests to automate the verification of the controller logic.
3.  **Global Exception Handling:** Create a specific `@ControllerAdvice` to provide cleaner error messages for 404 Not Found cases.