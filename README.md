# Node.js Demo App: CI/CD Pipeline with GitHub Actions

## About
A small Node.js (Express) web app with an automated CI/CD pipeline.
Every push to the `main` branch automatically tests the code, builds a
Docker image, and pushes it to DockerHub.

## Pipeline flow
Push to main → Run tests → Build Docker image → Push to DockerHub

## Tools used
- GitHub and GitHub Actions
- Node.js and Express
- Jest and Supertest (testing)
- Docker and DockerHub

## Project structure
- `app.js`: the Express app
- `server.js`: starts the server
- `app.test.js`: test that checks the home page returns 200
- `Dockerfile`: instructions to package the app
- `.github/workflows/main.yml`: the CI/CD workflow

## How the workflow works
1. **test job:** checks out the code, installs Node.js 20, runs `npm ci` and `npm test`.
2. **build-and-push job:** runs only if tests pass. Logs in to DockerHub, builds the image, and pushes it with the tags `latest` and the commit SHA.

## Secrets setup
Add these in the repo under Settings → Secrets and variables → Actions:
- `DOCKERHUB_USERNAME`: your DockerHub username
- `DOCKERHUB_TOKEN`: a DockerHub access token with Read & Write permission

## Run locally
```bash
npm install
npm test
npm start
```
Open http://localhost:3000

## Run the image from DockerHub
```bash
docker run -p 3000:3000 kottalayash/nodejs-demo-app:latest
```

## Screenshots
### Successful pipeline run
![Pipeline success](screenshots/pipeline-success.png)

### Image on DockerHub
![DockerHub](screenshots/dockerhub.png)

## What I learned
- How CI/CD automates testing and deployment
- How GitHub Actions jobs, steps, and runners work
- How to keep credentials safe using GitHub Secrets
- How the Docker build and push workflow works
