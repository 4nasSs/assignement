Assignment Project
This project is set up using Docker Compose, orchestrating a PostgreSQL database, a Spring Boot backend, and a React frontend.

Prerequisites
Before you begin, ensure you have the following installed on your system:

Docker: Install Docker Engine

Docker Compose: Docker Desktop typically includes Docker Compose. If not, you can install Docker Compose standalone.

Project Structure
This project expects the following directory structure:

.
├── assignment-backend/
│   ├── src/
│   │   └── main/
│   │       └── resources/
│   │           └── schema.sql
│   └── Dockerfile
├── assignment-frontend/
│   └── Dockerfile
└── docker-compose.yml

assignment-backend/: Contains the Spring Boot backend application, including its Dockerfile and the schema.sql for database initialization.

assignment-frontend/: Contains the React frontend application and its Dockerfile.

docker-compose.yml: Defines and configures the services for the application.

Getting Started
Follow these steps to get the project up and running:

Navigate to the project root:
Open your terminal or command prompt and navigate to the directory where your docker-compose.yml file is located.

cd path/to/your/project

Build and Run the Services:
Use Docker Compose to build the images and start all the services defined in docker-compose.yml. This command will also download the postgres:16-alpine image if you don't have it locally.

docker compose up --build

The --build flag ensures that your frontend and backend images are rebuilt, incorporating any recent changes in their respective Dockerfiles or source code.

The db service has a healthcheck defined, and the backend service is configured to start only when the db service is healthy, ensuring proper service startup order.

The schema.sql file located at ./assignment/src/main/resources/schema.sql will be automatically executed when the PostgreSQL container starts for the first time, initializing your database schema.

Verify Services (Optional):
You can check the status of your running containers:

docker compose ps

Accessing the Application
Once all services are up and running:

Frontend:
The React frontend will be accessible in your web browser at:
http://localhost:5173

Backend:
The Spring Boot backend API will be running and accessible at:
http://localhost:8080

PostgreSQL Database:
The PostgreSQL database is exposed on port 5432 on your host machine. You can connect to it using a database client with the following credentials:

Host: localhost

Port: 5432

Database Name: assignementdb

User: admin

Password: admin


Stopping the Services
To stop and remove the containers, networks, and volumes created by docker compose up:

docker compose down

To stop and remove only the containers and networks :

docker compose down --volumes
