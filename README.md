# 🚀 DevOps Internship – Task 1

## Automate Code Deployment Using CI/CD Pipeline

This project demonstrates a **CI/CD pipeline using GitHub Actions** to automatically test a Node.js application, build a Docker image, and push the image to DockerHub.

The pipeline is triggered automatically whenever code is pushed to the `main` branch.

---

## 📌 Task Objective

The objective of this task is to set up a CI/CD pipeline that automates the process of:

```text
Code Push
    ↓
GitHub Actions
    ↓
Install Dependencies
    ↓
Run Tests
    ↓
Build Docker Image
    ↓
Push Docker Image to DockerHub
```

---

## 🛠️ Technologies Used

* **Node.js** – Application runtime
* **Express.js** – Web framework
* **Docker** – Containerization
* **DockerHub** – Docker image registry
* **GitHub** – Source code management
* **GitHub Actions** – CI/CD automation
* **Git** – Version control
* **PowerShell** – Local development environment

---

## 📁 Project Structure

```text
nodejs-demo-app/
│
├── .github/
│   └── workflows/
│       └── main.yml
│
├── app.js
├── test.js
├── Dockerfile
├── .gitignore
├── package.json
├── package-lock.json
└── README.md
```

---

# 1️⃣ Node.js Application

The application is created using Node.js and Express.js.

The application provides two endpoints:

### Home Endpoint

```text
GET /
```

Response:

```text
Hello! Node.js CI/CD Pipeline is working.
```

### Health Endpoint

```text
GET /health
```

Response:

```json
{
  "status": "UP",
  "message": "Application is healthy"
}
```

The health endpoint is also used to verify the application during testing.

---

# 2️⃣ Install Dependencies

Initialize the Node.js project:

```bash
npm init -y
```

Install Express:

```bash
npm install express
```

Install dependencies:

```bash
npm install
```

---

# 3️⃣ Run the Application Locally

Start the application:

```bash
npm start
```

The application runs on:

```text
http://localhost:3000
```

Health check:

```text
http://localhost:3000/health
```

---

# 4️⃣ Run Tests

The project contains a `test.js` file that starts the application and checks the `/health` endpoint.

Run:

```bash
npm test
```

Expected result:

```text
Test passed!
```

This test is also executed automatically by GitHub Actions.

---

# 5️⃣ Docker Configuration

A `Dockerfile` is used to containerize the Node.js application.

### Dockerfile

```dockerfile
FROM node:22-alpine

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

EXPOSE 3000

CMD ["npm", "start"]
```

---

# 6️⃣ Build Docker Image

Build the Docker image:

```bash
docker build -t nodejs-demo-app .
```

Check the image:

```bash
docker images
```

Example:

```text
nodejs-demo-app:latest
```

---

# 7️⃣ Run Docker Container

Run the application inside a Docker container:

```bash
docker run -p 3000:3000 nodejs-demo-app
```

Open:

```text
http://localhost:3000
```

Health check:

```text
http://localhost:3000/health
```

---

# 8️⃣ DockerHub

The Docker image is pushed to DockerHub.

DockerHub repository:

```text
shindeharshad/nodejs-demo-app
```

Local image is tagged using:

```bash
docker tag nodejs-demo-app:latest shindeharshad/nodejs-demo-app:latest
```

Push the image:

```bash
docker push shindeharshad/nodejs-demo-app:latest
```

---

# 9️⃣ GitHub Actions CI/CD Pipeline

The CI/CD workflow is defined in:

```text
.github/workflows/main.yml
```

The pipeline is triggered whenever code is pushed to the `main` branch.

### Pipeline Flow

```text
Developer
    │
    │ git push
    ▼
GitHub Repository
    │
    ▼
GitHub Actions
    │
    ├── Checkout Code
    │
    ├── Setup Node.js
    │
    ├── Install Dependencies
    │
    ├── Run Tests
    │
    ├── Login to DockerHub
    │
    ├── Build Docker Image
    │
    └── Push Image
            │
            ▼
        DockerHub
```

---

# 🔟 GitHub Actions Workflow

The workflow performs the following operations:

1. Checkout source code
2. Set up Node.js
3. Install dependencies
4. Run tests
5. Login to DockerHub
6. Build Docker image
7. Push Docker image to DockerHub

The workflow uses GitHub Secrets for DockerHub authentication.

---

# 🔐 GitHub Secrets

The following repository secrets are configured in GitHub:

```text
DOCKER_USERNAME
DOCKER_PASSWORD
```

`DOCKER_PASSWORD` contains the DockerHub access token.

The secrets are referenced in the GitHub Actions workflow without exposing their values.

---

# 🔄 CI/CD Workflow

Whenever code is pushed to the `main` branch:

```text
git push
    ↓
GitHub Actions starts
    ↓
Checkout code
    ↓
Setup Node.js
    ↓
npm ci
    ↓
npm test
    ↓
Docker login
    ↓
Docker build
    ↓
Docker push
    ↓
DockerHub
```

If the test fails, the pipeline stops and the Docker image is not pushed.

---

# 📸 Screenshots

Add screenshots of the completed task below.

## 1. Node.js Application

Add screenshot showing the application running:

```text
screenshots/application.png
```

## 2. Docker Image

Add screenshot showing:

```bash
docker images
```

```text
screenshots/docker-image.png
```

## 3. DockerHub Repository

Add screenshot showing the DockerHub repository and image tag:

```text
screenshots/dockerhub.png
```

## 4. GitHub Actions

Add screenshot showing the successful GitHub Actions workflow:

```text
screenshots/github-actions.png
```

## 5. Successful Pipeline

Add screenshot showing all CI/CD steps completed successfully:

```text
screenshots/pipeline-success.png
```

---

# 🧪 Local Testing Commands

### Check Node.js

```bash
node --version
```

### Check npm

```bash
npm --version
```

### Install dependencies

```bash
npm install
```

### Run tests

```bash
npm test
```

### Start application

```bash
npm start
```

### Build Docker image

```bash
docker build -t nodejs-demo-app .
```

### Run Docker container

```bash
docker run -p 3000:3000 nodejs-demo-app
```

### Tag Docker image

```bash
docker tag nodejs-demo-app:latest shindeharshad/nodejs-demo-app:latest
```

### Push Docker image

```bash
docker push shindeharshad/nodejs-demo-app:latest
```

---

# 🎯 Learning Outcomes

By completing this task, I learned:

* How CI/CD works
* How to create a Node.js application
* How to create a Docker image
* How to run an application inside a Docker container
* How to push Docker images to DockerHub
* How GitHub Actions automates CI/CD
* How to configure GitHub Actions workflows
* How to use GitHub Secrets securely
* How to automate testing
* How to automate Docker image building and deployment

---

# 📌 Conclusion

This project demonstrates a basic CI/CD implementation using **GitHub Actions, Node.js, Docker, and DockerHub**.

The pipeline automatically performs:

```text
Test → Build → Push
```

whenever new code is pushed to the `main` branch.

This automation reduces manual deployment steps and demonstrates the basic workflow of a DevOps CI/CD pipeline.

---

## 👨‍💻 Project

**Project:** Node.js CI/CD Demo Application

**Task:** DevOps Internship – Task 1

**DockerHub Repository:** `shindeharshad/nodejs-demo-app`

**CI/CD Tool:** GitHub Actions

**Container Platform:** Docker

**Image Registry:** DockerHub
