# Code Brigade - A01

Welcome to your official HackToFuture 4 repository.

This repository template will be used for development, tracking progress, and final submission of your project. Ensure that all work is committed here within the allowed hackathon duration.

---

### Instructions for the teams:

- Fork the Repository and name the forked repo in this convention: hacktofuture4-team_id (for eg: hacktofuture4-A01)

---

## Rules

- Work must be done ONLY in the forked repository
- Only Four Contributors are allowed.
- After 36 hours, Please make PR to the Main Repository. A Form will be sent to fill the required information.
- Do not copy code from other teams
- All commits must be from individual GitHub accounts
- Please provide meaningful commits for tracking.
- Do not share your repository with other teams
- Final submission must be pushed before the deadline
- Any violation may lead to disqualification

---

# The Final README Template 

## Problem Statement / Idea

Clearly describe the problem you are solving.

- What is the problem?
- Why is it important?
- Who are the target users?

---

## Proposed Solution

Explain your approach:

- What are you building?
- How does it solve the problem?
- What makes your solution unique?

---

## Features

List the core features of your project:

- Feature 1
- Feature 2
- Feature 3

---

## Tech Stack

Mention all technologies used:

- Frontend:
- Backend:
- Database:
- APIs / Services:
- Tools / Libraries:

---

## Project Setup Instructions

## Step 1: Go to project root
cd "Nova Chat"

## Step 2: Install dependencies (all services)
Do this for each service:
cd auth-service
npm install

cd ../messaging-service
npm install

cd ../presence-service
npm install

cd ../agent-service
npm install

cd ../security-service
npm install

## Step 3: Setup environment variables
Create .env files in each service.
## Example (auth-service/.env)
PORT=3001
MONGO_URI=mongodb://<laptop-IP-Address>/nova-chat

## messaging-service
PORT=3002
MONGO_URI=mongodb://<laptop-IP-Address>/nova-chat

## presence-service
PORT=3003

## agent-service
PORT=4000
GROQ_API_KEY=your_key_here

## security-service
PORT=3005

## dashboard frontend
NEXT_PUBLIC_AGENT_BASE_URL=http://localhost:4000
NEXT_PUBLIC_SECURITY_BASE_URL=http://localhost:3005

## Step 4: Start MongoDB (VERY IMPORTANT)
If local MongoDB:
mongod

OR if using Docker:
docker run -d -p 27017:27017 --name mongo mongo

## Step 5: Run dashboard frontend
cd dashboard
npm run dev
Open:
http://localhost:5173

## Step 6: Test system
Check:
http://localhost:4000/agent/analyze
http://localhost:3005/security/status
http://localhost:3005/security/alerts

## OPTION 2 — Docker (Better for demo)
## Step 1: Build all services
From root:
docker-compose build

## Step 2: Start all services
docker-compose up
OR background:
docker-compose up -d

## Step 3: Check running containers
docker ps

## Step 4: Open app
http://localhost:5173

## Step 5: Check logs
docker-compose logs -f

## OPTION 3 — Kubernetes (Final Hackathon Demo)
## Step 1: Start Minikube
minikube start --driver=docker

## Step 2: Enable Docker inside Minikube
eval $(minikube docker-env) 

## Step 3: Build images
docker build -t nova-chat-auth-service ./auth-service
docker build -t nova-chat-messaging-service ./messaging-service
docker build -t nova-chat-presence-service ./presence-service
docker build -t nova-chat-agent-service ./agent-service
docker build -t nova-chat-security-service ./security-service
docker build -t nova-chat-frontend ./dashboard

## Step 4: Apply Kubernetes configs
kubectl apply -f k8s/

## Step 5: Check pods
kubectl get pods

## Step 6: Check services
kubectl get svc

## Step 7: Port forward (VERY IMPORTANT)
Dashboard:
kubectl port-forward svc/frontend 5173:80
Agent:
kubectl port-forward svc/agent-service 4000:4000
Security:
kubectl port-forward svc/security-service 3005:3005

## Step 8: Open app
http://localhost:5173

## FINAL TEST COMMANDS
Check agent
curl http://localhost:4000/agent/analyze

Check security
curl http://localhost:3005/security/status
curl http://localhost:3005/security/alerts

## Demo testing commands
Trigger overload
curl -X POST http://localhost:3002/simulate/overload
