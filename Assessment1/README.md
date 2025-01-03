# Todo App

A simple Flask-based web application to manage a to-do list. The application supports adding, deleting, and viewing tasks. It has been deployed on an AWS EC2 instance with basic security configurations.

## Features
- Add, view, and delete tasks.
- Accessible through a public URL.
- Secured with Nginx and self-signed certificates.

## Technologies Used
- Python
- Flask
- Gunicorn
- Nginx
- AWS EC2

## Prerequisites
- Python 3.x
- pip (Python package manager)
- Git

## Setup and Running Locally

1. Clone the repository:
   ```bash
   git clone https://github.com/Tejaswinikilaru/Web-app.git
   cd Web-app
   
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   
3. Run the application:
   ```bash
   python3 app.py
   
   
   
  **Open the app in your browser**:  http://localhost:5000
  
## Deployment Instructions
Steps to deploy the app on AWS EC2 instance:

## **Step1**: Create an Ec2 instance

Log into your AWS Management Console.

Launch a new EC2 instance using an Ubuntu image (e.g., t2.micro for free-tier).

Configure security groups to allow inbound traffic on port 22 (SSH), 80 (HTTP), and 443 (HTTPS), custom port (5000).

Create a key pair and save it to your local machine. This will be used for SSH access




## **Step 2** SSH into the EC2 Instance:
**ssh -i privatekey.pem ubuntu@your-ec2-public-ip**
																					



## **Step 3:** Install dependencies on EC2

Install Python and pip:

Update and install required packages:
**sudo apt update
sudo apt install python3-pip nginx -y**

Clone the repository and set up a virtual environment and install flask



## **Step 4:** Transfer your application code
Use scp to copy your project folder to your EC2 instance:
 **scp -i your-keypair.pem -r /path/to/your/application ubuntu@<your-ec2-public-ip>:/home/ubuntu/** 


## **Step 5:** 
Configure Gunicorn and Nginx.

## **Step 6:**
 Set up HTTPS with a self-signed certificate.


## Making the application persistent
 create a systemd service for Gunicorn

## Security configurations
- Self-signed certificates for HTTPS.
- Nginx as a reverse proxy for better performance and security.

## Challenges Faced
Challenge: Flask installation conflicts.

Solution: Used a virtual environment to isolate dependencies.

## Future Improvements
1.Implement HTTPS using Let's Encrypt with a domain.

2.Add more features to the application.

## Public URL
1)**Primary Access Point** :(URL with https and without specifying a port (shows warning because used self signed certificate))
Access the app here : https://18.144.155.169/

2)**Other Access point**:
Access the app here : http://18.144.155.169:5000
