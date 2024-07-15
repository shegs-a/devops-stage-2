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

## Deploying to a Cloud Production Server (e.g. Digital Ocean, AWS, GCP etc.)

### Prerequisites
- a cloud provider account.
- a linux server with a public IP address.
- A domain name with an SSL certificate.
- Inbound ports 80, 81, 443, 8080, 8090 open on your server for incoming traffic.

### Steps
1. Go to your DNS provider and add a A record for your domain name with the IP address of your server.

2. Afterward you can go ahead to SSH into your server and install Git. Ensure that you are running the git installation as the root user. You can use the following command to install Git:
   ```bash
   sudo apt-get update
   sudo apt-get install git
   ```

2. Clone this repository to your server.

3. Install Docker on your server. You can follow the official Docker documentation for the specific operating system you are using for your cloud server.

4. Install Docker Compose on your server. You can follow the official Docker Compose documentation for the specific operating system you are using for your cloud server. 

5. Change directory to the root directory of the repository and edit the `backend/.env.prod` file with your custom domain name and other settings.

6. Also edit the `frontend/.env.prod` file to reflect your custom domain name. 

7. Run the following command to build the Docker images and start the services:
   ```bash
   docker-compose -f docker-compose.prod.yml up -d
   ```

8. Access the Nginx Proxy Manager web interface by visiting `http://your_cusomt_domain_name:8090` in your browser. 

9. Use the default credentials for the Nginx Proxy Manager to log in:
   - Username: `admin@example.com`
   - Password: `changeme`

10. Setup an SSL certificate for your domain name using the Let's Encrypt service. Naviagte to the `SSL` tab and follow the instructions to generate a new SSL certificate for your domain name.

11. Once the SSL certificate is generated, add new proxy hosts for your domain name in the Nginx Proxy Manager. For the frontend application, you will need to add a New Proxy Host with the following settings:
   - Domain Name: `your-custom-domain-name`
   - Scheme: `http`
   - Forward Hostname / IP: `your_frontend_docker_ip` # Replace with the IP address of the frontend container
   - Forward Port: `5173` 

12. To ensuure that the frontend and backend applications are running on the same port, you will need to add custom locations to the new proxy host you just created. Navigate to the `Custom locations` tab and add the following custom locations: 
   - Location: `/api`   
   - Scheme: `http`
   - Forward Hostname / IP: `your_backend_docker_container_name` # Replace with the name of the backend container
   - Forward Port: `8000`
   Do this for the `backend/docs` and `backend/redocs` custom locations as well.

13. Your application should now be fully configured and running on your server. You can access the frontend application by visiting `http://your-custom-domain-name` in your browser.