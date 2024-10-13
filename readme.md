# Kifi Stammbaum

This is the readme file for the Kifi Stammbaum project. It provides a concise preoperational documentation and best practice layer structure for the database, backend, frontend, and authentication.

## Project Structure

This is the readme file for the Kifi Stammbaum project. It provides a concise preoperational documentation and best practice layer structure for the database, backend, frontend, and authentication.

## Project Structure

### Database: MySQL
- Best Practice Layer Structure:
    - Tables: Organize data into tables based on entities (e.g., Persons, Relationships)
    - Relationships: Define appropriate relationships between tables using foreign keys
    - Indexes: Create indexes for faster data retrieval
    - Views: Utilize views for complex queries or data transformations
    - Stored Procedures: Implement stored procedures for reusable database logic
    - Transactions: Use transactions to ensure data consistency and integrity
    - #TODO how to cope with the situation that several users may want to read and write at the same time?
    - #TODO how to backup data? (assuming users regularly add members and relationships)

### Authentication: Keycloak
- Best Practice Layer Structure:
    - Realm: Create a realm to manage users, roles, and permissions
    - Clients: Configure clients for frontend and backend applications
    - Roles: Define roles with specific permissions for fine-grained access control
    - User Federation: Integrate with external identity providers if needed
    - Multifactor Authentication: Enable additional security measures like OTP or biometrics

### Backend: Node.js
- Best Practice Layer Structure:
    - Entities: Define entity models representing database tables
    - Endpoints: Implement RESTful endpoints for CRUD operations
    - Business Logic: Implement logic for validating birth dates and other business rules
    - Error Handling: Handle errors gracefully and provide meaningful error messages
    - Testing: Write unit tests to ensure code quality and reliability

### Frontend: React.js
- Best Practice Layer Structure:
    - Components: Organize UI components based on their functionality
    - State Management: Use state management libraries like Redux or MobX
    - Routing: Implement client-side routing for better user experience
    - API Integration: Communicate with backend APIs using libraries like Axios
    - Responsive Design: Ensure the application is responsive and works well on different devices

## Recommended Folder Structure

```
- backend/
    - src/
        - controllers/ : Contains the controller files responsible for handling the business logic and request/response handling.
        - models/ : Contains the model files representing the database tables and defining the data structure.
        - routes/ : Contains the route files defining the API endpoints and their corresponding controller methods.
        - utils/ : Contains utility files with reusable functions or helper methods.
        - tests/ : Contains the unit tests for the backend code.

- frontend/
    - src/
        - components/ : Contains the UI components responsible for rendering the user interface.
        - containers/ : Contains the container components that connect the UI components to the application state.
        - services/ : Contains the service files responsible for making API calls and handling data from the backend.
        - utils/ : Contains utility files with reusable functions or helper methods.
        - tests/ : Contains the unit tests for the frontend code.

- database/
    - migrations/ : Contains the database migration files that define the changes to the database schema.
    - seeds/ : Contains the seed files that populate the database with initial data.

- authentication/
    - config/ : Contains the configuration files for the authentication system.
    - middleware/ : Contains the middleware files responsible for handling authentication and authorization.
    - controllers/ : Contains the controller files responsible for handling authentication-related logic.
    - models/ : Contains the model files representing the authentication entities and defining the data structure.
    - routes/ : Contains the route files defining the authentication API endpoints.
    - tests/ : Contains the unit tests for the authentication code.
```

Please note that this folder structure is recommended for organizing the different components of the project. You can adjust it based on your specific needs and preferences.

## Setting Up the Components

To set up the different components of the Kifi Stammbaum project, follow these steps:

### Database: MySQL

1. Install MySQL on your machine. You can download it from the official MySQL website.

2. Create a new database for the project. You can use the MySQL command line or a GUI tool like MySQL Workbench.

3. Update the database connection configuration in the backend code. Open the `backend/src/config/database.js` file and replace the placeholder values with your MySQL database credentials.

4. Run the database migrations to create the necessary tables. In the terminal, navigate to the `backend` folder and run the following command:

    ```
    npm run migrate
    ```

### Authentication: Keycloak

1. Install Keycloak on your machine. You can download it from the official Keycloak website.

2. Start the Keycloak server and create a new realm for the project. Refer to the Keycloak documentation for detailed instructions on how to set up a realm.

3. Configure the Keycloak client for the frontend and backend applications. Open the Keycloak admin console, navigate to the realm settings, and create two clients: one for the frontend and one for the backend. Make sure to set the appropriate redirect URIs and client credentials.

4. Update the Keycloak configuration in the backend code. Open the `backend/src/config/keycloak.js` file and replace the placeholder values with your Keycloak realm URL and client credentials.

### Backend: Node.js

1. Install Node.js on your machine. You can download it from the official Node.js website.

2. Navigate to the `backend` folder in the terminal.

3. Install the required dependencies by running the following command:

    ```
    npm install
    ```

4. Start the backend server by running the following command:

    ```
    npm start
    ```

### Frontend: React.js

1. Install Node.js on your machine if you haven't already.

2. Navigate to the `frontend` folder in the terminal.

3. Install the required dependencies by running the following command:

    ```
    npm install
    ```

4. Start the frontend development server by running the following command:

    ```
    npm start
    ```

5. Open your web browser and navigate to `http://localhost:3000` to access the Kifi Stammbaum application.

That's it! You have successfully set up the different components of the Kifi Stammbaum project. Feel free to explore the code and make any necessary modifications to fit your specific requirements.

## Security

Ensuring the security of your Kifi Stammbaum project is crucial to protect sensitive data and prevent unauthorized access. Here are the key security features that must be implemented for each component:

### Database: MySQL
- Input Validation: Implement proper input validation to prevent SQL injection attacks. Use parameterized queries or prepared statements to sanitize user input.
- Access Control: Set up appropriate user roles and permissions to restrict access to sensitive data and operations.
- Encryption: Encrypt sensitive data stored in the database, such as passwords or personal information, using strong encryption algorithms.

### Authentication: Keycloak
- Secure Communication: Enable HTTPS to encrypt the communication between the Keycloak server and the clients.
- Password Policies: Enforce strong password policies, such as minimum length, complexity requirements, and password expiration.
- Two-Factor Authentication: Implement two-factor authentication to add an extra layer of security for user accounts.
- Brute Force Protection: Implement mechanisms to detect and prevent brute force attacks, such as account lockouts or CAPTCHA challenges.

### Backend: Node.js
- Input Sanitization: Validate and sanitize user input to prevent common security vulnerabilities like cross-site scripting (XSS) or command injection.
- Authentication Middleware: Implement authentication middleware to verify the identity of incoming requests and restrict access to protected endpoints.
- Authorization: Implement role-based access control (RBAC) to ensure that only authorized users can perform certain actions.
- Error Handling: Handle errors securely by not revealing sensitive information in error messages.

### Frontend: React.js
- Input Validation: Implement client-side input validation to prevent malicious input from being submitted to the backend.
- Cross-Site Scripting (XSS) Prevention: Use proper encoding and sanitization techniques to prevent XSS attacks.
- Content Security Policy (CSP): Implement a strict CSP to restrict the types of content that can be loaded by the application.
- Secure Storage: Store sensitive data, such as access tokens or user credentials, securely using techniques like encryption or secure cookies.

Remember to regularly update your dependencies, apply security patches, and follow security best practices to keep your Kifi Stammbaum project secure.

## Folder Structure

The folder structure for your project should be as follows:

```
- backend/
    - src/
        - controllers/ : Contains the controller files responsible for handling the business logic and request/response handling.
        - models/ : Contains the model files representing the database tables and defining the data structure.
        - routes/ : Contains the route files defining the API endpoints and their corresponding controller methods.
        - utils/ : Contains utility files with reusable functions or helper methods.
        - tests/ : Contains the unit tests for the backend code.

- frontend/
    - src/
        - components/ : Contains the UI components responsible for rendering the user interface.
        - containers/ : Contains the container components that connect the UI components to the application state.
        - services/ : Contains the service files responsible for making API calls and handling data from the backend.
        - utils/ : Contains utility files with reusable functions or helper methods.
        - tests/ : Contains the unit tests for the frontend code.

- database/
    - migrations/ : Contains the database migration files that define the changes to the database schema.
    - seeds/ : Contains the seed files that populate the database with initial data.

- authentication/
    - config/ : Contains the configuration files for the authentication system.
    - middleware/ : Contains the middleware files responsible for handling authentication and authorization.
    - controllers/ : Contains the controller files responsible for handling authentication-related logic.
    - models/ : Contains the model files representing the authentication entities and defining the data structure.
    - routes/ : Contains the route files defining the authentication API endpoints.
    - tests/ : Contains the unit tests for the authentication code.
```

Please make sure to place your existing files and folders in the appropriate locations within this folder structure.

## Database SQL Files

To include your existing SQL files in the project, follow these steps:

1. Copy your SQL files into the `database/migrations` folder.

2. Make sure the SQL files follow the naming convention required by your database migration tool. For example, if you are using Knex.js, the files should be named in the format `YYYYMMDDHHmmss_migration_name.js` or `YYYYMMDDHHmmss_migration_name.sql`.

3. Run the database migrations to apply the changes defined in your SQL files. In the terminal, navigate to the `backend` folder and run the following command:

    ```
    npm run migrate
    ```

This will execute the SQL files and update your database schema accordingly.

That's it! Your existing SQL files are now included in the project and will be applied when running the database migrations.

