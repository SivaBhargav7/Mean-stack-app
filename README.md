MEAN Stack CI/CD Deployment

📌 Project Overview

This project demonstrates how to containerize and deploy a full-stack MEAN (MongoDB, Express, Angular, Node.js) application using Docker, Docker Compose, and GitHub Actions.
The goal was to set up an automated CI/CD pipeline that builds Docker images, pushes them to Docker Hub, and deploys the updated application on an AWS EC2 instance.

🛠️ Project Setup & Containerization

The application consists of two parts: frontend (Angular) and backend (Express/Node).

I created separate Dockerfiles inside the frontend/ and backend/ folders.

A docker-compose.yml file was added at the root of the project to orchestrate:

Frontend container

Backend container

MongoDB (using the official image)

Nginx was configured as a reverse proxy so that the entire application is accessible via port 80.

🔑 GitHub Secrets Configuration

To allow GitHub Actions to deploy the app securely, I created repository secrets under
Settings → Secrets and variables → Actions.
The following secrets were configured:

DOCKERHUB_USERNAME → My Docker Hub username

DOCKERHUB_TOKEN → Docker Hub access token

VM_HOST → Public IP of my AWS EC2 instance

VM_USER → SSH username (ubuntu)

VM_SSH_KEY → Private SSH key for EC2 access

VM_PORT → SSH port (default: 22)

⚙️ GitHub Actions Workflow

A CI/CD workflow file was created inside .github/workflows/.
The workflow is triggered whenever a change is pushed to the main branch.
The workflow performs the following tasks:

Checks out the latest code.

Builds Docker images for both frontend and backend.

Pushes the images to Docker Hub.

SSHs into the EC2 instance and pulls the latest images.

Restarts the containers using docker-compose.

☁️ AWS EC2 Setup

I launched an AWS EC2 t2.large instance (Ubuntu).

Installed necessary tools:

Docker

Docker Compose

Git (for initial setup)

The instance was configured with inbound rules for ports 22, 80, 443.

Docker Compose was used to run the containers and serve the app.

🚀 CI/CD Pipeline in Action

Once the pipeline was set up, the following workflow was tested:

I made a small change in the frontend file:
frontend/src/app/app.component.html

<!-- Old -->
<a href="#" class="navbar-brand">DD Task</a>
<!-- Updated -->
<a href="#" class="navbar-brand">Discover Dollar Task</a>


This change was committed and pushed to GitHub.

The CI/CD pipeline automatically detected the change, rebuilt the images, pushed them to Docker Hub, pulled them on EC2, and restarted the containers.

Within a few minutes, the updated text appeared live on the deployed application.

🌍 Live Application

The deployed application is accessible publicly at:

👉 http://13.239.225.49/

(This IP is shared exclusively for assessment and demonstration purposes.)

📸 Screenshots

I have included the following screenshots in this README for validation:

<img width="1920" height="1080" alt="Screenshot (17)" src="https://github.com/user-attachments/assets/c12f03bf-cffc-4ce6-bc81-a3e69f84dc18" />
<img width="1920" height="1080" alt="Screenshot (19)" src="https://github.com/user-attachments/assets/2803ac52-166d-4823-8cc5-1c21908e4e88" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b0fd8c3e-11a8-4c43-b131-0270056c279e" />
<img width="1920" height="1080" alt="Screenshot (8)" src="https://github.com/user-attachments/assets/5f405712-4ee6-4986-b8ba-7b9a180008db" />
<img width="1920" height="1080" alt="Screenshot (7)" src="https://github.com/user-attachments/assets/d93a1120-8716-4ce2-b47f-ef8bc26e4469" />
<img width="1920" height="1080" alt="Screenshot (6)" src="https://github.com/user-attachments/assets/b899ba1a-404f-47a1-b68b-57fce692f889" />
<img width="1920" height="1080" alt="Screenshot (5)" src="https://github.com/user-attachments/assets/2ff96c28-f2c4-4d3e-9b65-be586d5d5d18" />
<img width="1920" height="1080" alt="Screenshot (15)" src="https://github.com/user-attachments/assets/ec843710-ee6f-443e-8854-e724d1c88e93" />
<img width="1920" height="1080" alt="Screenshot (14)" src="https://github.com/user-attachments/assets/7b849676-2713-4e82-a95d-6cb218fa7286" />
<img width="1920" height="1080" alt="Screenshot (13)" src="https://github.com/user-attachments/assets/48da6efa-c531-4642-8389-236e12bc6eb1" />
<img width="1920" height="1080" alt="Screenshot (12)" src="https://github.com/user-attachments/assets/315c9230-6444-4bf2-a0ab-74fdafdf6dfd" />
<img width="1920" height="1080" alt="Screenshot (11)" src="https://github.com/user-attachments/assets/c84f88e4-b1b6-46c0-bada-02596ab01a5a" />
<img width="1920" height="1080" alt="Screenshot (10)" src="https://github.com/user-attachments/assets/7d351957-6810-487f-b953-1176821ffafd" />
Now commited new change 

<img width="1920" height="1080" alt="Screenshot (21)" src="https://github.com/user-attachments/assets/0b808095-58b0-4493-b0df-a1eae47a94fd" />
<img width="1920" height="1080" alt="Screenshot (22)" src="https://github.com/user-attachments/assets/6373f945-f329-4446-b6f2-857938174bc0" />
<img width="1920" height="1080" alt="Screenshot (23)" src="https://github.com/user-attachments/assets/fbbdeef3-00c0-4c21-9ff7-4ce7a9db684a" />


