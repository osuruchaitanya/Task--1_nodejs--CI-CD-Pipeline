---
## 📌 Task 1: Automate Code Deployment Using CI/CD Pipeline

This project demonstrates a complete CI/CD automation workflow using *GitHub Actions* to build and deploy a simple *Node.js* web application using *Docker*.

---

## 📁 Project Structure

nodejs-demo-app/ ├── app.js ├── Dockerfile ├── .github/ │   └── workflows/ │       └── main.yml  # CI/CD Pipeline ├── package.json └── README.md

---


## 🎯 Objective

Set up a CI/CD pipeline that automatically builds, tests, and deploys a Node.js web application using Docker and GitHub Actions.

---

## 🛠 Tools & Technologies

- GitHub
- GitHub Actions
- Node.js
- Docker
- DockerHub

---

## 🚦 CI/CD Workflow Summary

- Trigger: On push to main branch
- Jobs:
  - *Build*: Install dependencies and build Docker image
  - *Test*: Run basic unit tests
  - *Push*: Push image to DockerHub
  - *Deploy*: Deploy container (locally or on a server)

---

🧱 1. Basic Node.js App
server.js

js
Copy
Edit
const express = require("express");
const app = express();
const port = process.env.PORT || 3000;

app.get("/", (req, res) => {
  res.send("Hello from Node.js CI/CD pipeline!");
});

app.listen(port, () => {
  console.log(`Server running at http://localhost:${port}`);
});
package.json

json
Copy
Edit
{
  "name": "ci-cd-nodejs-demo",
  "version": "1.0.0",
  "main": "server.js",
  "scripts": {
    "start": "node server.js",
    "test": "echo \"No test specified\" && exit 0"
  },
  "dependencies": {
    "express": "^4.18.2"
  }
}
⚙️ 2. CI/CD Pipeline using GitHub Actions
.github/workflows/nodejs-ci-cd.yml

yaml
Copy
Edit
name: Node.js CI/CD Pipeline

on:
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Set up Node.js
        uses: actions/setup-node@v3
        with:
          node-version: '18'

      - name: Install dependencies
        run: npm install

      - name: Run tests
        run: npm test

      - name: Start server (optional for test or deploy)
        run: |
          npm start &
          sleep 5
          curl http://localhost:3000
🐳 (Optional) Dockerfile:
Dockerfile
Copy
Edit
FROM node:18
WORKDIR /app
COPY . .
RUN npm install
EXPOSE 3000
CMD ["node", "server.js"]
📤 3. How to Test the Pipeline
Push code to main branch on GitHub.

Navigate to Actions tab.

See the workflow running:

Install dependencies

Run tests

(Optionally) deploy or start the server

📚 4. README.md Sample
markdown
Copy
Edit
# Node.js CI/CD Pipeline

This is a demo of setting up a CI/CD pipeline for a Node.js app using GitHub Actions.

## Features
- Node.js server
- GitHub Actions CI/CD pipeline
- Dockerfile (optional)

## Steps to run locally
```bash
git clone <repo>
cd Task--1_nodejs--CI-CD-Pipeline
npm install
npm start
CI/CD
This project uses GitHub Actions for continuous integration and deployment.

yaml
Copy
Edit

---

## ✅ Deliverables:
- [ ] GitHub repo with CI/CD setup
- [ ] Working Node.js app
- [ ] `.github/workflows/` configured
- [ ] Optional Dockerfile
- [ ] `README.md` with setup & pipeline info

---

If you're submitting this as part of a course/project, let me know the platform (like DevOps course, WILP, etc.) and I’ll help generate a **report or documentation** too.







Is this helpful so far?



Ask ChatGPT
read me



Tools



ChatGPT can mak
