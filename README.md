# Undo - Smart Lost and Found Platform

**Helping lost belongings find their way back home.**

Undo is a full-stack web application designed to simplify the process of recovering lost belongings. It connects people who have lost items with those who have found them through centralized reporting, intelligent item matching, location-based discovery, and secure ownership verification.

The application is developed using the MERN stack: MongoDB, Express.js, React.js, and Node.js.

## Project Details

| Field            | Details                              |
| ---------------- | ------------------------------------ |
| Project Name     | Undo - Smart Lost and Found Platform |
| Course           | B.Tech                               |
| Branch           | CSE - DS                             |
| Section          | A                                    |
| Project Domain   | Full Stack Web Development           |
| Technology Stack | MERN                                 |

## Team Members

| S. No. | Name             | Roll Number   |
| ------ | ---------------- | ------------- |
| 1      | Lakshay Aggarwal | 2400321540108 |
| 2      | Kushal Chaudhary | 2400321540107 |

## Problem Statement

Losing personal belongings in public places can be stressful, while returning recovered items to their rightful owners can be difficult. Traditional lost-and-found processes often depend on manual searches, disconnected announcements, and word of mouth.

Undo aims to solve this problem through a centralized platform where users can report lost and found items, discover potential matches, and coordinate the recovery process.

## Objectives

* Provide a centralized system for reporting lost and found belongings.
* Help users discover potential matches between lost and found reports.
* Enable efficient searching and filtering of item listings.
* Implement secure authentication and authorization.
* Facilitate ownership verification before an item is returned.
* Provide a responsive and intuitive user interface.
* Maintain persistent application data through a database-backed architecture.

## Key Features

### 1. User Authentication

* User registration and login.
* Secure password hashing.
* Authentication-protected routes and APIs.
* User profile management.
* Authorization checks for protected operations.

### 2. Lost Item Reporting

Users can submit reports containing an item name, description, category, approximate location, date, and optional image.

### 3. Found Item Reporting

Users can publish found-item reports to help identify the rightful owners of recovered belongings.

### 4. Intelligent Item Matching

The matching system will identify and rank potentially corresponding lost and found reports using attributes such as:

* Item category.
* Description similarity.
* Location proximity.
* Date of loss or discovery.

Matching scores will help users prioritize relevant reports. They will not be treated as definitive proof of ownership.

### 5. Search and Filtering

* Search by item name and description.
* Filter by category, location, and date.
* Sort reports by relevance or recency.
* Paginate listing results.

### 6. Ownership Verification

A verification workflow will help establish whether a claimant is the rightful owner before an item is returned. Sensitive identifying details will not be exposed publicly.

### 7. Image Uploads

Users can attach images to reports to make item identification easier. Image files can be managed through a dedicated cloud storage service.

### 8. Notifications

Users can receive notifications about relevant matches and updates to their reports. Real-time notifications may be implemented using Socket.IO.

### 9. User Dashboard

Users can manage their reports, track their status, review potential matches, and update relevant information.

### 10. Administrative Controls

Administrative functionality may include reviewing reports, handling inappropriate content, and managing reported misuse.

## Technology Stack

### Frontend

* **React.js:** Component-based user interface.
* **JavaScript:** Application logic.
* **Vite:** Frontend development and build tooling.
* **Tailwind CSS:** Responsive styling.
* **React Router:** Client-side navigation.
* **Axios:** Communication with backend APIs.

### Backend

* **Node.js:** Server-side JavaScript runtime.
* **Express.js:** REST API development.
* **JWT:** Authentication and protected API access.
* **bcrypt:** Password hashing and verification.
* **Multer:** Handling multipart file uploads where required.

### Database

* **MongoDB:** Persistent document storage.
* **Mongoose:** Schema definition, validation, and database operations.

### Additional Services

* **Cloudinary:** Image storage and delivery.
* **Socket.IO:** Optional real-time notifications.
* **Git and GitHub:** Version control and collaboration.
* **Vercel and a suitable Node.js hosting platform:** Deployment.

The final selection of third-party services may change during implementation.

## System Architecture

Undo follows a client-server architecture.

```text
              USER
                |
                v
       React.js Frontend
                |
          HTTP / REST API
                |
                v
       Node.js + Express.js
                |
        +-------+-------+
        |       |       |
        v       v       v
    MongoDB   Matching  Auth and
    Database  Service   Validation
                |
                v
       Matching Results
                |
                v
       React.js Frontend
```

Image storage and real-time notifications can be integrated as separate services.

## Planned Application Modules

| Module           | Responsibilities                                           |
| ---------------- | ---------------------------------------------------------- |
| Authentication   | Registration, login, authorization, and profile management |
| Lost Items       | Create and manage lost-item reports                        |
| Found Items      | Create and manage found-item reports                       |
| Matching Engine  | Rank potentially corresponding reports                     |
| Search           | Filtering, sorting, and pagination                         |
| Image Management | Upload and retrieve item images                            |
| Notifications    | Communicate relevant matches and report updates            |
| Administration   | Moderate reports and handle misuse                         |

## Planned Database Models

### User

Stores account and profile information.

Potential fields:

* `name`
* `email`
* `password`
* `role`
* `createdAt`
* `updatedAt`

### Item

Stores lost and found reports.

Potential fields:

* `title`
* `description`
* `category`
* `reportType`
* `location`
* `date`
* `images`
* `status`
* `reportedBy`
* `createdAt`
* `updatedAt`

### Match

Stores potential matches between lost and found reports.

Potential fields:

* `lostItem`
* `foundItem`
* `matchScore`
* `matchStatus`
* `createdAt`

### Notification

Stores notifications associated with users.

Potential fields:

* `recipient`
* `type`
* `message`
* `relatedItem`
* `isRead`
* `createdAt`

These are proposed schemas and may be adjusted as the application requirements become clearer.

## API Design

The backend will expose RESTful endpoints for the frontend.

| Method | Endpoint                 | Purpose                                   |
| ------ | ------------------------ | ----------------------------------------- |
| POST   | `/api/auth/register`     | Register a user                           |
| POST   | `/api/auth/login`        | Authenticate a user                       |
| GET    | `/api/users/me`          | Retrieve the authenticated user's profile |
| POST   | `/api/items`             | Create an item report                     |
| GET    | `/api/items`             | Retrieve and filter item reports          |
| GET    | `/api/items/:id`         | Retrieve a specific report                |
| PATCH  | `/api/items/:id`         | Update an authorized user's report        |
| DELETE | `/api/items/:id`         | Delete an authorized user's report        |
| GET    | `/api/matches`           | Retrieve potential matches                |
| GET    | `/api/notifications`     | Retrieve user notifications               |
| PATCH  | `/api/notifications/:id` | Update notification status                |

Additional endpoints will be introduced for administrative operations and other application workflows.

## Project Structure

The project will use a separate frontend and backend structure.

```text
undo-lost-and-found/
├── client/
│   ├── public/
│   ├── src/
│   │   ├── assets/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── layouts/
│   │   ├── hooks/
│   │   ├── context/
│   │   ├── services/
│   │   ├── utils/
│   │   ├── App.jsx
│   │   └── main.jsx
│   ├── index.html
│   └── package.json
├── server/
│   ├── src/
│   │   ├── config/
│   │   ├── controllers/
│   │   ├── middleware/
│   │   ├── models/
│   │   ├── routes/
│   │   ├── services/
│   │   ├── utils/
│   │   └── app.js
│   ├── server.js
│   └── package.json
├── .gitignore
└── README.md
```

The final structure may evolve as the project develops.

## Security Considerations

* Hash passwords before storing them.
* Validate and sanitize incoming data.
* Enforce authorization on the server.
* Restrict file types and upload sizes.
* Keep secrets in environment variables.
* Apply rate limiting to sensitive endpoints.
* Protect private item details and ownership-verification information.
* Avoid treating a matching score as proof of ownership.

## Future Enhancements

* Image-based similarity matching.
* Map-based item discovery.
* More advanced text-similarity algorithms.
* Real-time match notifications.
* Secure communication between users.
* Automated duplicate-report detection.
* Analytics for item recovery rates.
* Progressive Web App support.

## Expected Outcome

Undo aims to provide a centralized, accessible, and secure lost-and-found platform. The project will demonstrate practical full-stack development through React-based interfaces, REST API design, MongoDB persistence, authentication, business logic, and third-party service integration.

## Contributors

**Lakshay Aggarwal**
Roll Number: 2400321540108

**Kushal Chaudhary**
Roll Number: 2400321540107

**Course:** B.Tech
**Branch:** CSE - DS
**Section:** A

---

*Undo - Because lost doesn't have to mean gone.*
