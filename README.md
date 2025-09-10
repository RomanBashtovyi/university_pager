# 🎓 University Pager - Chat Application

A full-stack real-time chat application designed for university environments, built with React and Node.js, powered by Stream Chat API.

## 📋 Table of Contents

- [Overview](#overview)
- [Tech Stack](#tech-stack)
- [Features](#features)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Installation & Setup](#installation--setup)
- [Environment Variables](#environment-variables)
- [Running the Application](#running-the-application)
- [API Endpoints](#api-endpoints)
- [Architecture](#architecture)
- [Contributing](#contributing)

## 🎯 Overview

University Pager is a comprehensive chat application that enables real-time communication between university students and staff. The application features both team channels for group discussions and direct messaging for private conversations, with SMS notifications for offline users.

## 🛠️ Tech Stack

### Frontend (Client)

- **React 17** - UI framework with functional components and hooks
- **Stream Chat React** - Pre-built chat components and functionality
- **Axios** - HTTP client for API requests
- **Universal Cookie** - Session management
- **CSS3** - Custom styling with responsive design

### Backend (Server)

- **Node.js** - Runtime environment
- **Express.js** - Web framework
- **Stream Chat API** - Chat service and user management
- **Twilio** - SMS notification service
- **bcrypt** - Password hashing
- **CORS** - Cross-origin resource sharing
- **dotenv** - Environment variable management

### External Services

- **Stream Chat** - Real-time chat infrastructure and user storage
- **Twilio** - SMS messaging service

## ✨ Features

### 🔐 Authentication

- User registration with full profile (name, username, password, phone, avatar)
- Secure login system
- Session management with cookies
- Password hashing with bcrypt

### 💬 Chat Functionality

- **Team Channels** - Group discussions for teams/classes
- **Direct Messaging** - Private conversations between users
- **Real-time messaging** - Instant message delivery
- **Channel search** - Find channels and users quickly
- **Channel management** - Create and edit channels

### 📱 Notifications

- **SMS notifications** - Automatic SMS when user is offline
- **Real-time updates** - Live message delivery
- **Online/offline status** - User presence indicators

### 🎨 User Interface

- Modern, responsive design
- University branding with custom logo
- Mobile-friendly interface
- Intuitive navigation
- Custom color scheme (#005fff)

## 📁 Project Structure

```
university_pager/
├── client/                 # React frontend
│   ├── public/            # Static assets
│   ├── src/
│   │   ├── components/    # React components
│   │   │   ├── Auth.jsx
│   │   │   ├── ChannelContainer.jsx
│   │   │   ├── ChannelListContainer.jsx
│   │   │   └── ...
│   │   ├── assets/        # Images and icons
│   │   ├── App.jsx        # Main app component
│   │   └── index.js       # Entry point
│   └── package.json
├── server/                # Node.js backend
│   ├── controllers/       # Business logic
│   │   └── auth.js
│   ├── routes/           # API routes
│   │   └── auth.js
│   ├── index.js          # Server entry point
│   └── package.json
└── README.md
```

## 🔧 Prerequisites

Before running this application, make sure you have the following installed:

- **Node.js** (v14 or higher)
- **npm** (v6 or higher)
- **Stream Chat Account** - Sign up at [getstream.io](https://getstream.io)
- **Twilio Account** - Sign up at [twilio.com](https://twilio.com)

## 🚀 Installation & Setup

### 1. Clone the Repository

```bash
git clone <repository-url>
cd university_pager
```

### 2. Install Dependencies

#### Backend Dependencies

```bash
cd server
npm install
```

#### Frontend Dependencies

```bash
cd ../client
npm install
```

## 🔑 Environment Variables

Create a `.env` file in the `server` directory with the following variables:

```env
# Stream Chat Configuration
STREAM_API_KEY=your_stream_api_key
STREAM_API_SECRET=your_stream_api_secret
STREAM_APP_ID=your_stream_app_id

# Twilio Configuration
TWILIO_ACCOUNT_SID=your_twilio_account_sid
TWILIO_AUTH_TOKEN=your_twilio_auth_token
TWILIO_MESSAGING_SERVICE_SID=your_twilio_messaging_service_sid

# Server Configuration
PORT=5000
```

### How to get Stream Chat credentials:

1. Sign up at [getstream.io](https://getstream.io)
2. Create a new app
3. Copy the API Key, API Secret, and App ID from your dashboard

### How to get Twilio credentials:

1. Sign up at [twilio.com](https://twilio.com)
2. Get your Account SID and Auth Token from the console
3. Create a Messaging Service and get the SID

## 🏃‍♂️ Running the Application

### Development Mode

#### 1. Start the Backend Server

```bash
cd server
npm run dev
```

The server will start on `http://localhost:5000`

#### 2. Start the Frontend Client

```bash
cd client
npm start
```

The client will start on `http://localhost:3000`

### Production Mode

#### 1. Build the Frontend

```bash
cd client
npm run build
```

#### 2. Start the Backend

```bash
cd server
npm start
```

## 📡 API Endpoints

### Authentication Routes (`/auth`)

| Method | Endpoint       | Description       | Body                                                       |
| ------ | -------------- | ----------------- | ---------------------------------------------------------- |
| POST   | `/auth/signup` | Register new user | `{ fullName, username, password, phoneNumber, avatarURL }` |
| POST   | `/auth/login`  | User login        | `{ username, password }`                                   |

### Webhook Endpoint

| Method | Endpoint | Description                                        |
| ------ | -------- | -------------------------------------------------- |
| POST   | `/`      | Webhook for Stream Chat events (SMS notifications) |

## 🏗️ Architecture

### Data Flow

1. **User Registration/Login** → Backend validates and creates user in Stream Chat
2. **Real-time Chat** → Stream Chat handles all messaging functionality
3. **SMS Notifications** → Webhook triggers Twilio SMS for offline users
4. **Session Management** → Cookies store user session data

### Key Components

- **Stream Chat** acts as the primary database for users and messages
- **Express Server** handles authentication and webhooks
- **React Client** provides the user interface
- **Twilio** sends SMS notifications

## 🎨 Customization

### Styling

- Main color scheme defined in `client/src/App.css`
- Primary color: `#005fff`
- Responsive design with mobile support

### Branding

- Replace `dragomanov-logo.png` with your university logo
- Update the app name in `ChannelListContainer.jsx`

## 🐛 Troubleshooting

### Common Issues

1. **Stream Chat Connection Issues**

   - Verify your API credentials in `.env`
   - Check if your Stream Chat app is active

2. **SMS Notifications Not Working**

   - Verify Twilio credentials
   - Check if phone numbers are in correct format

3. **CORS Errors**
   - Ensure backend is running on correct port
   - Check CORS configuration in `server/index.js`

## 📝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the ISC License.

## 🙏 Acknowledgments

- [Stream Chat](https://getstream.io/chat/) for the chat infrastructure
- [Twilio](https://twilio.com) for SMS services
- [React](https://reactjs.org) for the frontend framework
- [Express.js](https://expressjs.com) for the backend framework

---

**Note**: This is an educational project demonstrating full-stack development with real-time chat functionality. Make sure to configure your environment variables properly before running the application.
