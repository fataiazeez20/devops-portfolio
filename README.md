# DevOps Portfolio Website

A personal DevOps portfolio website built to showcase my DevOps projects, technical skills, and learning journey.

This project demonstrates how a static website can be containerized with Docker and prepared for automated deployment using GitHub Actions, GitHub Container Registry (GHCR), and AWS EC2.

---

## Architecture

```text
Developer
    |
    v
GitHub Repository
    |
    v
GitHub Actions
    |
    +---- Run Tests
    |
    +---- Build Docker Image
    |
    v
GitHub Container Registry (GHCR)
    |
    v
AWS EC2
    |
    v
Docker Container
    |
    v
Nginx
    |
    v
Portfolio Website
```

---

## Technologies Used

* HTML5
* CSS3
* Linux / Ubuntu
* Git
* GitHub
* Docker
* Docker Compose
* GitHub Actions
* GitHub Container Registry (GHCR)
* AWS EC2
* Nginx
* SSH
* Ansible

---

## Features

* Responsive DevOps portfolio website
* Navigation between website sections
* About section
* Technical skills section
* DevOps projects section
* DevOps learning journey section
* Contact section
* Docker containerization
* Nginx web server
* Docker health check
* Docker Compose development environment
* Automated CI/CD deployment workflow
* GitHub Container Registry image storage
* AWS EC2 deployment

---

## Project Structure

```text
devops-portfolio/
├── .github/
│   └── workflows/
│       └── deploy.yml
├── images/
├── .dockerignore
├── .gitignore
├── Dockerfile
├── docker-compose.yml
├── docker-compose.prod.yml
├── index.html
├── style.css
└── README.md
```

---

## Local Development

### Clone the repository

```bash
git clone git@github.com:fataiazeez20/devops-portfolio.git
cd devops-portfolio
```

### Run with Docker Compose

```bash
docker-compose up -d --build
```

The website runs on:

```text
http://localhost:8080
```

The Docker Compose configuration maps:

```text
Host port 8080 → Container port 80
```

### Check the running container

```bash
docker ps
```

### Stop the application

```bash
docker-compose down
```

---

## Docker

The application uses Nginx as the web server inside an Alpine Linux-based Docker image.

The Dockerfile:

1. Uses the Nginx Alpine image.
2. Removes the default Nginx website.
3. Copies the portfolio HTML and CSS files into the Nginx web directory.
4. Exposes port 80.
5. Defines a Docker health check.

Build the image manually:

```bash
docker build -t devops-portfolio .
```

Run the container manually:

```bash
docker run -d \
  --name devops-portfolio \
  -p 8080:80 \
  devops-portfolio
```

---

## Docker Compose

The development Docker Compose configuration runs the portfolio on port 8080.

```text
Host
  |
  | Port 8080
  v
Docker Container
  |
  | Port 80
  v
Nginx
  |
  v
Portfolio Website
```

The production Compose configuration is reserved for the AWS EC2 deployment environment.

---

## CI/CD Pipeline

The project uses GitHub Actions to automate the application deployment process.

The planned pipeline performs the following steps:

```text
Git Push
   |
   v
GitHub Actions
   |
   v
Run Tests
   |
   v
Build Docker Image
   |
   v
Login to GHCR
   |
   v
Push Docker Image
   |
   v
Connect to AWS EC2
   |
   v
Pull Latest Image
   |
   v
Restart Container
   |
   v
Live Website
```

This removes the need to manually build and deploy the application after every change.

---

## GitHub Container Registry

GitHub Container Registry is used to store the Docker image produced by the CI/CD pipeline.

The general image flow is:

```text
Source Code
    |
    v
Docker Build
    |
    v
Docker Image
    |
    v
GHCR
    |
    v
AWS EC2
```

The EC2 server can pull the image from GHCR during deployment.

---

## AWS EC2 Deployment

The production application will be deployed to an AWS EC2 Ubuntu server.

The application deployment directory is:

```text
/opt/devops-portfolio
```

`/opt` is used as the conventional location for deployed application files on Linux systems.

The production environment will run the portfolio using Docker.

---

## Ansible

Ansible can be used to automate the configuration of the AWS EC2 server.

Potential configuration tasks include:

* Installing Docker
* Installing Nginx
* Creating application directories
* Configuring server permissions
* Configuring firewall rules
* Configuring Nginx
* Managing required services

Ansible is used for infrastructure and server configuration, while Docker handles application packaging and execution.

---

## DevOps Concepts Demonstrated

This project demonstrates practical experience with:

### Version Control

Git and GitHub are used to track application changes and maintain the source code repository.

### Containerization

Docker packages the website and Nginx web server into a portable container.

### Infrastructure

AWS EC2 provides the Linux server where the application can run.

### Automation

GitHub Actions automates testing, image building, publishing, and deployment.

### Container Registry

GHCR stores Docker images so they can be pulled by the deployment server.

### Configuration Management

Ansible can automate the configuration of the EC2 environment.

### Web Server

Nginx serves the static portfolio website.

### SSH

SSH provides secure access to the EC2 server and GitHub authentication.

---

## Project Goals

The main goals of this project are to:

* Build a professional DevOps portfolio
* Practice Docker containerization
* Understand CI/CD automation
* Deploy applications to AWS
* Practice Linux server administration
* Work with container registries
* Improve infrastructure automation skills
* Build real-world DevOps experience
