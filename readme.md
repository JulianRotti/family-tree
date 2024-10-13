# Family Tree Project

This project consists of three main components: a React.js frontend, a Node.js backend, and a MySQL database. The following steps will guide you through setting up and running the project.

## 1. Keycloak Setup

### Prerequisites
- Install Docker and Docker Compose.

### Steps to Start Keycloak
1. Run Keycloak in Docker using the provided Docker Compose file:
   ```bash
   docker-compose up
   ```

2. Once the Keycloak server is running, log in to the Keycloak Admin Console:
   - URL: `http://localhost:8080`
   - Username: `admin`
   - Password: `admin`

3. Inside the Keycloak Admin Console:
   - **Create a new Realm** named `family-tree`.
   - Inside this Realm, **create a new client** with the following configuration:
     - **Client ID**: `family-tree-frontend`
     - **Client Protocol**: `openid-connect`
     - **Access Type**: `public`

4. **Create user roles**:
   - Go to the "Roles" tab under the created Realm and add the following roles:
     - `editor`
     - `viewer`

5. **Add users**:
   - Under "Users," create users and assign them the appropriate roles (`editor` and `viewer`).

Once Keycloak is set up, it will be ready for integration with the frontend.

## 2. Backend Setup (family-tree-backend)

The backend is a Node.js application with a layered architecture:

- **Models**: Define the data structures and schemas.
- **Services**: Contain the business logic and interact with models.
- **Controllers**: Handle HTTP requests and responses.
- **Middleware**: Functions that run before requests reach the controllers (e.g., authentication).
- **Routes**: Define the API endpoints and link them to controllers.

### Running the Backend
1. Navigate to the `family-tree-backend` folder:
   ```bash
   cd family-tree-backend
   ```
2. Install dependencies and start the backend:
   ```bash
   npm install
   npm start
   ```

## 3. Frontend Setup (family-tree-frontend)

The frontend is a React.js application with the following layers:

- **Components**: Reusable UI elements and building blocks.
- **Contexts**: Global state management using React context.
- **Hooks**: Custom logic to reuse functionality across components.
- **Pages**: Views for different routes in the application.
- **Routes**: Define the client-side routing of the application.
- **Services**: Handle API calls and communication with the backend.
- **Utils**: Helper functions and utilities used throughout the app.

### Environment Variables
The frontend relies on Keycloak for authentication. Make sure to create a `.env` file in the `family-tree-frontend` folder with the following content:

```bash
REACT_APP_KEYCLOAK_URL=http://localhost:8080
REACT_APP_KEYCLOAK_REALM=family-tree
REACT_APP_KEYCLOAK_CLIENT_ID=family-tree-frontend
```

These values should match the Keycloak configuration you set up earlier.

### Running the Frontend
1. Navigate to the `family-tree-frontend` folder:
   ```bash
   cd family-tree-frontend
   ```
2. Install dependencies and start the frontend:
   ```bash
   npm install
   npm start
   ```

## 4. Database Setup (family-tree-database)

The database is a MySQL instance. You need to install and run a MySQL server.

### Steps to Set Up the Database
1. Install MySQL and start the MySQL server.
2. Navigate to the `family-tree-database` folder.
3. Run the following scripts in your MySQL environment:
   ```sql
   source setup_dev_user.sql;
   source schema.sql;
   source seeds/fill_test_data.sql;
   ```