# Python Application with Docker

This project demonstrates a simple Python application running in a containerized environment using Docker. The setup uses best practices, including a multi-stage Docker build and a non-root user for enhanced security.

----------

## Features

-   **Non-root user:** Improves container security by avoiding the use of the root user.
-   **Multi-stage build:** Reduces the final image size by separating the build and runtime stages.
-   **Port mapping:** Exposes the application on port `8000` for accessibility.

----------

## Prerequisites

1.  Docker installed on your local machine or Ec2 instance.
2.  A user with sudo privileges (if not using the root account).

----------

## Steps to Run the Application

### 1. Clone the Repository

Clone the GitHub repository to your local machine:

`git clone https://github.com/Tejaswinikilaru/Web-app.git`
 
 `cd Web-app/Assessment2`

### 2. Add User to Docker Group (Optional)

To run Docker without using `sudo`:

`sudo usermod -aG docker $USER
newgrp docker` 

Log out and back in to apply the changes.

### 3. Build the Docker Image

Build the Docker image using the provided `Dockerfile`:



`docker build -t my-python-app:1.0.0 .` 

### 4. Run the Container

Run the container in detached mode:


`docker run -d -p 8000:8000 --restart always my-python-app:1.0.0` 

### 5. Access the Application

-   **Locally:** Visit http://localhost:8000 on your browser.
    
-   **Remotely:** Use your EC2 public IP or DNS. For example:
    
    
    `http://<your-ec2-public-ip>:8000` 

## Stopping the Container

To stop the running container:

1.  List the running containers:
    
   
    
    `docker ps` 
    
2.  Stop the container using its `CONTAINER ID`:
    
   
    
    `docker stop <CONTAINER_ID>` 
    

----------

## Troubleshooting

### Port 8000 Already in Use

If port `8000` is already allocated:

1.  Identify the process using the port:
   
    
    `sudo lsof -i:8000` 
    
2.  Kill the process:
    
    
    `sudo kill -9 <PID>` 
    
3.  Restart the container with:

    
    `docker run -d -p 8000:8000 --restart always my-python-app:1.0.0` 
    

### Docker Permission Denied

If you encounter a "permission denied" error while running Docker commands:

1.  Add your user to the Docker group (see [Step 2](#2-add-user-to-docker-group-optional)).
    
2.  Ensure the Docker service is running:
    
  
    
    `sudo systemctl start docker` 
    

----------

## Security Considerations

1.  **Non-Root User:** The application runs as a non-root user inside the container to minimize security risks.
2.  **Port Restrictions:** Ensure only necessary ports (e.g., `8000`) are open in the EC2 security group.
3.  **Access Control:** Restrict inbound traffic to trusted IP ranges in the EC2 security group to prevent unauthorized access.

----------

## Screenshot

Refer the docs folder 
