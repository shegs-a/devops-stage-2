# Full-Stack FastAPI and React Template

Welcome to the Full-Stack FastAPI and React template repository. This repository serves as a demo application for interns, showcasing how to set up and run a full-stack application with a FastAPI backend and a ReactJS frontend using ChakraUI.

## Project Structure

The repository is organized into two main directories:

- **frontend**: Contains the ReactJS application.
- **backend**: Contains the FastAPI application and PostgreSQL database integration.

Each directory has its own README file with detailed instructions specific to that part of the application.

## Getting Started

To get started with this template, please follow the instructions in the respective directories:

- [Frontend README](./frontend/README.md)
- [Backend README](./backend/README.md)

## Setting up Nginx Proxy Manager

### Prerequisites
- Docker installed on your machine

### Steps
1. Clone this repository to your local machine.

2. Navigate to the root directory of the repository where the `docker-compose.yml` file is located.

3. Run the following command to start the services:
   ```bash
   docker-compose up -d
   ```

4. Access the Nginx Proxy Manager web interface by visiting `http://your_server_ip:8090` in your browser.

5. Log in with the default credentials:
   - Username: `admin@example.com`
   - Password: `changeme`

6. Change the admin password and configure Nginx Proxy Manager as needed.

7. Now add the domains and services you want to reverse proxy and SSL terminate to Nginx Proxy Manager.

8. For the frontend application, you will need to add a New Proxy Host with the following settings:
   - Name: `frontend`
   - Scheme: `http`
   - Forward Hostname / IP: `your_frontend_docker_ip` # Replace with the IP address of the frontend container
   - Forward Port: `80`

9. For the backend application, you will need to add a New Proxy Host with the following settings:
   - Name: `backend`
   - Scheme: `http`
   - Forward Hostname / IP: `your_backend_docker_ip` # Replace with the IP address of the backend container
   - Forward Port: `80`

## Setting up Adminer
Access Adminer by visiting `http://your_server_ip:8080` in your browser to manage your PostgreSQL database.

For more detailed information on setting up the frontend and backend applications, refer to the respective README files in the `frontend` and `backend` directories:
- [Frontend README](./frontend/README.md)
- [Backend README](./backend/README.md)
