# YOU CAN FIND MY CODES HERE:
| Service           | REPO                           |
|------------------|-------------------------------|
|  Frontend UI    | [React App](https://github.com/Gizoskos/4458FinalFrontend)  |
|  API Gateway     | [Gateway](https://github.com/Gizoskos/4458ApiGateway)  |
|  Admin Service   | [Admin](https://github.com/Gizoskos/4458FinalAdminService)        |
|  Notification    | [Notification](https://github.com/Gizoskos/4458FinalNotificationService) |
|  Job Posting     | [Job Posting](https://github.com/Gizoskos/4458FinalJobPostingService)  |
|  Job Search      | [Job Search](https://github.com/Gizoskos/4458FinalJobSearchService)  |
|  AI Agent        | [AI_Agent](https://github.com/Gizoskos/4458FinalAiAgentService)  |

#  Kariyer.net Clone – Job Search Platform

This project is a modern, full-stack **Job Search Web Application** inspired by kariyer.net, built with a service-oriented architecture. The platform enables users to search and apply for jobs, track recent searches, receive notifications, and interact with an AI job assistant for smart job suggestions.

## DEMO VIDEO [DRIVE VIDEO](https://drive.google.com/drive/u/2/folders/1Zonud1cABklea31PdvkmZABe5sn-uX4w)
---

## Data Model (ER Diagram)
![image](https://github.com/user-attachments/assets/57c77915-c65f-42da-b111-6e8226abb94f)

##  Live Deployments

| Service           | URL                           |
|------------------|-------------------------------|
|  Frontend UI    | [React App](https://four458finalfrontend.onrender.com)  |
|  API Gateway     | [Gateway](https://four458apigateway.onrender.com)     |
|  Admin Service   | [Admin](https://four458finaladminservice.onrender.com)         |
|  Notification    | [Notification](https://four458finalnotificationservice.onrender.com) |
|  Job Posting     | [Job Posting](https://four458finaljobpostingservice.onrender.com)   |
|  Job Search      | [Job Search](https://four458finaljobsearchservice.onrender.com)     |
|  AI Agent        | [AI_Agent](https://four458finalaiagentservice.onrender.com)  |                                                                                
---

##  System Architecture

```text
[ React Frontend (Vite) ]
          |
     [ API Gateway ]
   ↙    ↓    ↘     ↘
Admin  Job  Notify  AI
Service Service Service Agent
React Frontend: Handles job browsing, filters, detail views, and AI chat.

API Gateway: Central request router and security proxy.

Admin Service: Admin-only endpoints to add or update job posts.

Job Posting Service: Stores job details, application count, related jobs (MongoDB + Redis).

Job Search Service: Enables keyword/city search, autocomplete, filters, and search history.

Notification Service: Handles job alerts via RabbitMQ and MongoDB.

AI Agent Service: Uses Together.ai to interpret user intent and return job matches.
```

 Features
## Job Search
Search by position and city

Smart autocomplete suggestions

Filter by location, work type, country

Display recent searches

Show related jobs on detail page

## Job Detail View
Show job title, company, location

Track number of applications

Show 3 related jobs

Display Apply button (only for logged-in users)

## AI Job Assistant
Users can type: “Show me remote React jobs in İzmir”

AI extracts query → calls job-search-service → returns job suggestions

## Admin Panel
Add, update, and manage jobs via secured endpoints

Requires JWT with role ADMIN

## Notifications
Users can create job alerts

Alerts matched with new jobs using RabbitMQ

Notifications logged and shown to users

## Security & Auth
JWT Authentication for /apply, /admin/**, and AI endpoints

Role-based access control using Spring Security

API Gateway handles login and token forwarding

## Technologies
Frontend: React.js, Vite, Axios, Tailwind

Backend: Spring Boot, MongoDB, Redis, RabbitMQ

AI/NLP: Together.ai for natural language parsing

Auth: JWT-based, secured via API Gateway

Cloud: All services deployed on Render.com

Service Architecture: Each module is independently deployable

📂 Directory Structure
4458Final/
├── admin-service/
├── job-posting-service/
├── job-search-service/
├── notification-service/
├── ai-agent-service/
├── api-gateway/
└── frontend/ (React + Vite)
## How to Run Locally
# Clone the repo
git clone [https://github.com/Gizoskos/4458Final](https://github.com/Gizoskos/4458Final.git)
cd 4458Final

# Start Frontend
cd frontend
npm install
npm run dev

# Run API Gateway
cd ../api-gateway
npm install
node index.js

# Run Spring Boot microservices
cd ../admin-service
mvn spring-boot:run

cd ../job-search-service
mvn spring-boot:run

cd ../job-posting-service
mvn spring-boot:run

cd ../notification-service
mvn spring-boot:run

cd ../ai-agent-service
node agent.js
## AI Message Format
Frontend sends:

json
{
  "text": "show me remote Java jobs in Ankara",
  "userId": "user123"
}
Agent returns:

json
{
  "reply": [
    {
      "title": "Java Developer",
      "location": "Ankara",
      "applyUrl": "/job/abc123"
    },
    ...
  ]
}
## Design Decisions
Used MongoDB for flexibility in job postings and alert storage

Integrated Redis to cache job details for faster response

Utilized RabbitMQ to decouple alert processing

Designed REST APIs for job CRUD, search, detail, apply

Used Together.ai to parse free-text job queries into structured API calls

## Known Issues
Render free-tier may cause cold starts/delays

AI rate limit: fallback response used if Together.ai times out

Some endpoints require JWT – use login form or Postman to obtain token

## Contact
Created with ❤️ by Gizoskos

For issues, please open a GitHub issue
