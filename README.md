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
# 
interface User {
  id: number;
  username: string;
  roles: string[];  // Example: ['user', 'admin']
  groups: number[];  // List of group IDs the user belongs to
}
#
Group Model:
interface Group {
  id: number;
  name: string;
  administrators: number[];  // Admin user IDs
  channels: string[];  // List of channel names
  bannedUsers: { [channelName: string]: number[] };  // Map of banned users per channel
}
#
Server-Side
User Model:
const userSchema = new mongoose.Schema({
  id: Number,
  username: String,
  roles: [String],  // Roles like 'admin', 'user'
  groups: [Number]  // Group IDs
});
Group Model:
const groupSchema = new mongoose.Schema({
  id: Number,
  name: String,
  administrators: [Number],  // Admin user IDs
  channels: [String],  // List of channels
  bannedUsers: { type: Map, of: [Number] }  // Map of banned users
});
#
Frontend Architecture (Angular)
Components
Login: Handles user login through a form.
Sign-Up: Allows new users to register.
User Management: Enables admins to manage users, promote them to higher roles, or delete them.
Group Management: Admins can create groups and channels.
Channel: Displays channel content and user interactions.
Services
UserService: Manages user-related API interactions.
GroupService: Handles API requests for managing groups and channels.
AuthService: Handles authentication and role checking.
Routing
Angular routes are defined for smooth navigation between components like user management, group creation, and channel access.

Backend Architecture (Node.js)
Modules
Express.js: Handles routing and request management.
Mongoose: Facilitates communication with MongoDB.
Body-Parser: Middleware for parsing incoming requests.
Core Functions
User Management: Manages users' creation, promotion, and deletion.
Group and Channel Management: Handles creating and managing groups and channels.
Authentication: Verifies user credentials and assigns roles.
Key Files
server.js: Main entry point for the backend.
models/: Contains the Mongoose models for users and groups.
API Routes
User Management Routes
GET /api/users: Retrieves all users.
POST /api/signup: Registers a new user.
POST /api/users/:userId/promote-group-admin: Promotes a user to a group admin.
POST /api/users/:userId/promote-super-admin: Promotes a user to super admin.
DELETE /api/users/:userId: Deletes a user by their ID.
Group and Channel Management Routes
GET /api/groups: Retrieves all groups.
POST /api/groups: Creates a new group.
POST /api/groups/:groupId/channels: Adds a new channel to a group.
POST /api/groups/:groupId/remove-user: Removes a user from a group.
POST /api/groups/:groupId/ban-user: Bans a user from a specific channel.
Client-Server Interaction
Authentication and Session Management
The login component sends the user's credentials to the /api/auth endpoint, and the server validates them before issuing a session or token. This session is stored on the client-side for future authenticated requests.

Group Join Requests
Users can request to join a group, and administrators can respond to these requests through dedicated routes.

MongoDB Integration
Database Structure
MongoDB is used as the primary database, where documents are stored in collections for both users and groups. Each document represents an entity like a user or a group with its attributes.

Collection Overview
Users Collection: Stores information like username, email, roles, and group memberships.
Groups Collection: Contains groups, administrators, channels, and banned users.
Client-Server MongoDB Interaction
For operations like creating a group or banning a user from a channel, the client sends a request to the server, which then updates MongoDB with the new information.

Directory Structure
client/: Contains all Angular-related code.
server/: Contains all Node.js-related code. The separation ensures clarity and easier maintenance for both client and server.
Data Models
Client-Side
User Model:
