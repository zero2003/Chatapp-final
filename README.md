# Chatapp-final
Table of Contents
Introduction
Repository Structure
Data Models
Client-side
Server-side
Frontend Architecture (Angular)
Backend Architecture (Node.js)
Routes and Functions
API Routes
User Management
Group and Channel Management
Client-Server Interaction
Authentication and Session Management
Group Join Requests
MongoDB Integration
Introduction
This project is a full-stack web-based chat application, utilizing Angular for the frontend and Node.js with Express for the backend. It provides various functionalities such as user authentication, group creation, channel management, and user roles, with seamless communication between the client and server using a REST API.

Repository Structure
Branching Strategy
Main Branch: This branch contains stable, production-ready code, thoroughly tested and reviewed.
Feature Branches: Every new feature or bug fix is developed on a dedicated branch, such as feature/feature-name or bugfix/issue-name. Once completed, the feature branch is merged into the main branch after code review and testing.
Directory Structure
client/: Contains all Angular-related code.
server/: Contains all Node.js-related code. The separation ensures clarity and easier maintenance for both client and server.
Data Models
Client-Side
User Model:
