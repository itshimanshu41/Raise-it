# Raise It - Complaint Management System

A comprehensive web-based platform for managing and resolving public grievances through a systematic, multi-level approach. This system enables citizens to file complaints, track their status, and receive timely updates while allowing government officers to efficiently manage and resolve issues.

## 🎯 Overview

Raise It is a full-stack grievance management system designed to streamline the process of complaint filing, assignment, tracking, and resolution. The platform implements a hierarchical officer system where complaints are automatically assigned to appropriate officers based on district, department, and workload.

## ✨ Key Features

### For Citizens (Users)
- **Complaint Filing**: Submit grievances with subject, description, and department categorization
- **Status Tracking**: Real-time tracking of complaint status (pending, in process, resolved)
- **Complaint Management**: View all complaints, delete unresolved complaints
- **Reopen Complaints**: Reopen resolved complaints (up to 3 times) if not satisfied
- **Send Reminders**: Send reminder emails to assigned officers
- **Rate Officers**: Rate officers after complaint resolution (1-5 stars)
- **Email Notifications**: Receive email updates on complaint status changes
- **User Profile**: Manage personal information and district details

### For Officers
- **Task Dashboard**: View all assigned complaints
- **Update Status**: Update complaint status and add feedback
- **Forward Tasks**: Forward complaints to higher-level officers when needed
- **Action History**: Maintain complete history of all actions taken
- **Performance Tracking**: View ratings and feedback from citizens

### For Administrators
- **User Management**: Manage all users, officers, and admins
- **Officer Management**: Add, update, and manage officer details
- **System Oversight**: Monitor system-wide complaint statistics
- **Profile Management**: Update admin profiles and settings

## 🏗️ System Architecture

### Multi-Level Officer Hierarchy
- **Level 1 Officers**: First point of contact for new complaints
- **Level 2 Officers**: Handle escalated complaints
- **Level 3 Officers**: Handle complex or unresolved issues
- **Smart Assignment**: Complaints are automatically assigned to officers with the least workload in the same district and department

### Complaint Workflow
1. User files a complaint → Assigned to Level 1 officer in the same district and department
2. Officer updates status and provides feedback
3. If needed, complaint can be forwarded to higher-level officers
4. Once resolved, user can rate the officer
5. User can reopen complaint if not satisfied (max 3 times)

## 🛠️ Technology Stack

### Frontend
- **React 18** - UI library
- **Vite** - Build tool and dev server
- **React Router** - Client-side routing
- **Tailwind CSS** - Utility-first CSS framework
- **Axios** - HTTP client
- **Formik** - Form management
- **React Icons** - Icon library

### Backend
- **Node.js** - Runtime environment
- **Express.js** - Web framework
- **MongoDB** - NoSQL database
- **Mongoose** - MongoDB object modeling
- **JWT** - Authentication tokens
- **bcryptjs** - Password hashing
- **Nodemailer** - Email notifications
- **Express Rate Limit** - API rate limiting
- **Helmet** - Security headers
- **XSS-Clean** - XSS protection

## 📁 Project Structure

```
raiseit-platform-1/
├── client/                 # Frontend React application
│   ├── src/
│   │   ├── Components/    # React components
│   │   ├── services/      # API service functions
│   │   ├── assets/        # Static assets
│   │   └── Images/        # Image files
│   ├── public/            # Public assets
│   └── package.json
├── server/                # Backend Node.js application
│   ├── controllers/       # Route controllers
│   ├── models/           # MongoDB models
│   ├── routes/           # API routes
│   ├── middleware/       # Custom middleware
│   ├── errors/           # Error handling
│   ├── db/               # Database connection
│   └── package.json
└── README.md
```

## 🚀 Getting Started

### Prerequisites
- Node.js (v14 or higher)
- MongoDB (local or cloud instance)
- npm or yarn

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/itshimanshu41/Raise-it.git
   cd Raise-it
   ```

2. **Install server dependencies**
   ```bash
   cd server
   npm install
   ```

3. **Install client dependencies**
   ```bash
   cd ../client
   npm install
   ```

4. **Environment Setup**
   
   Create a `.env` file in the `server` directory:
   ```env
   MONGO_URI=your_mongodb_connection_string
   JWT_SECRET=your_jwt_secret_key
   JWT_LIFETIME=7d
   PORT=3000
   ```

5. **Start the development servers**
   
   Terminal 1 - Start backend server:
   ```bash
   cd server
   npm start
   ```
   
   Terminal 2 - Start frontend dev server:
   ```bash
   cd client
   npm run dev
   ```

6. **Access the application**
   - Frontend: http://localhost:5173
   - Backend API: http://localhost:3000

## 🔐 Authentication & Security

- **JWT-based Authentication**: Secure token-based authentication for all users
- **Role-based Access Control**: Separate authentication for users, officers, and admins
- **Password Hashing**: bcryptjs for secure password storage
- **Rate Limiting**: API rate limiting to prevent abuse
- **Security Headers**: Helmet.js for security headers
- **XSS Protection**: XSS-clean middleware
- **CORS Configuration**: Configured for secure cross-origin requests

## 📊 Database Models

- **User**: Citizen accounts with district, email, phone, age
- **Officer**: Government officers with level, department, district
- **Admin**: System administrators
- **Complaint**: Grievance records with status, feedback history, ratings
- **OfficerRatings**: Rating aggregation for officers
- **Blacklist**: Token blacklist for logout functionality

## 🔄 API Endpoints

### Authentication
- `POST /api/v1/auth/register` - User registration
- `POST /api/v1/auth/login` - User login
- `POST /api/v1/auth/forgot-password` - Password reset request
- `POST /api/v1/auth/reset-password` - Password reset

### Complaints
- `GET /api/v1/complaints` - Get all user complaints
- `POST /api/v1/complaints` - Create new complaint
- `GET /api/v1/complaints/:id` - Get specific complaint
- `DELETE /api/v1/complaints/:id` - Delete complaint
- `POST /api/v1/complaints/:id/remind` - Send reminder
- `POST /api/v1/complaints/:id/reopen` - Reopen complaint
- `POST /api/v1/complaints/:id/rate` - Rate officer

### Tasks (Officer)
- `GET /api/v1/tasks` - Get all assigned tasks
- `GET /api/v1/tasks/:id` - Get specific task
- `PATCH /api/v1/tasks/:id` - Update task status
- `POST /api/v1/tasks/:id/pass` - Forward task to higher officer

## 🎨 Departments Supported

- Health
- Education
- Transport
- Pension
- Other

## 📧 Email Notifications

The system sends automated email notifications for:
- Complaint assignment
- Status updates
- Task forwarding
- Reminder requests
- Complaint reopening
- Rating submissions

## 🔄 Status Flow

- **Pending**: Complaint filed, awaiting officer action
- **In Process**: Officer is actively working on the complaint
- **Resolved**: Complaint has been resolved

## 📝 License

ISC

## 👥 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📞 Contact

For questions or support, please open an issue on the GitHub repository.

---

**Note**: This project is actively maintained and under continuous development. For the latest updates, please check the repository.
