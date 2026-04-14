# Collaborative Code Editor

A real-time collaborative code editor that allows multiple users to edit code simultaneously with instant synchronization. Built with modern web technologies for seamless real-time collaboration experience.

## Overview

This is a full-stack web application enabling real-time collaborative code editing. Multiple users can join a session and edit the same code document concurrently, with all changes synchronized instantly across all connected clients using WebSocket connections.

---

## Features

### Core Functionality
- **Real-time Code Editing**: Multiple users can edit the same code document simultaneously with instant updates
- **Live User Presence**: See all connected users in a sidebar with real-time presence detection
- **WebSocket Communication**: Bidirectional real-time communication using Socket.io for low-latency synchronization
- **Session Management**: Users join sessions using a username parameter in the URL query string
- **Automatic Cleanup**: Graceful user disconnection handling when users leave or close the browser

### Technical Highlights
- **Conflict Resolution**: Built-in CRDT (Conflict-free Replicated Data Type) using Yjs for seamless merge of concurrent edits
- **Monaco Editor Integration**: Industry-standard code editor with syntax highlighting and advanced editing capabilities
- **Real-time Awareness State**: Track user presence and status across the collaborative session
- **CORS Enabled**: Backend configured for cross-origin requests to support distributed deployments

---

## Tech Stack

### Frontend
- **React 19.1.1**: Modern UI library for building interactive components
- **Vite 7.1.7**: Next-generation build tool for fast development and optimized production builds
- **Tailwind CSS 4.2.2**: Utility-first CSS framework for responsive design
- **Monaco Editor**: Professional code editor component with full language support
- **Yjs 13.6.30**: CRDT library for conflict-free real-time collaboration
- **y-monaco**: Binding layer between Monaco Editor and Yjs for collaborative editing
- **Socket.io Client**: WebSocket client library for real-time communication
- **y-socket.io**: Yjs provider for Socket.io transport

### Backend
- **Node.js**: JavaScript runtime for server-side development
- **Express.js 5.2.1**: Minimal web application framework
- **Socket.io 4.8.3**: Real-time communication library for WebSocket support
- **y-socket.io**: Server-side provider for Yjs synchronization
- **Nodemon**: Development tool for automatic server restart on file changes

### Development Tools
- **ESLint 9.36.0**: Code quality and style enforcement
- **Babel**: JavaScript transpiler for modern syntax support

---

## Project Structure

```
Docker+AWS/
├── Backend/
│   ├── package.json
│   ├── server.js           # Express server with Socket.io setup
│   └── node_modules/
│
└── Frontend/
    ├── package.json
    ├── vite.config.js
    ├── eslint.config.js
    ├── index.html
    ├── README.md
    ├── public/
    └── src/
        ├── main.jsx        # React entry point
        └── app/
            ├── App.jsx     # Main application component
            └── App.css     # Application styles
```

---

## Getting Started

### Prerequisites
- Node.js (v16 or higher)
- npm or yarn package manager

### Installation & Setup

#### Backend Setup
```bash
cd Backend
npm install
npm run dev          # Start development server with auto-reload
# or
npm run start        # Production start
```

The backend server will run on `http://localhost:3000`

#### Frontend Setup
```bash
cd Frontend
npm install
npm run dev          # Start development server with HMR
```

The frontend will typically run on `http://localhost:5173`

---

## Usage

1. **Start Backend**: Run the backend server first (listens on port 3000)
2. **Start Frontend**: Run the frontend development server
3. **Access Application**: Open `http://localhost:5173` in your browser
4. **Join Session**: Enter your username in the login form
5. **Share URL**: Share the URL with other users to collaborate:
   - `http://localhost:5173/?username=YourName`
6. **Collaborate**: All connected users can now edit code in real-time

---

## Key Implementation Details

### Real-time Synchronization
- Uses Yjs CRDT for automatic conflict resolution
- Socket.io establishes WebSocket connections for low-latency communication
- Awareness states track connected users and their presence
- Bidirectional data binding between Monaco Editor and shared document model

### User Presence Management
- Users join with a username passed via URL query parameter
- Active users displayed in the sidebar
- Automatic cleanup on page unload or disconnect
- Real-time user list updates across all clients

### Architecture
- **Frontend**: React components with hooks for state management and side effects
- **Backend**: Express.js HTTP server with Socket.io for WebSocket upgrades
- **Communication**: JSON-based message protocol over WebSocket

---

## Potential Enhancements

- [ ] Persistent document storage (database integration)
- [ ] User authentication and authorization
- [ ] Multiple document/file support
- [ ] Code execution environment
- [ ] Chat/commenting system
- [ ] Document history and version control
- [ ] Language mode selection for syntax highlighting
- [ ] Export/import functionality
- [ ] Docker containerization
- [ ] AWS deployment configuration

---

## Scripts

### Frontend
- `npm run dev` - Start development server with hot module replacement
- `npm run build` - Build optimized production bundle
- `npm run lint` - Run ESLint to check code quality
- `npm run preview` - Preview production build locally

### Backend
- `npm run dev` - Start development server with auto-reload (uses nodemon)
- `npm run start` - Start production server

---

## Browser Support

- Modern browsers with WebSocket support (Chrome, Firefox, Safari, Edge)
- ES6+ JavaScript support required

---

## Performance Considerations

- **Fast Development**: Vite's instant module replacement for rapid iteration
- **Optimized Build**: Vite produces highly optimized production bundles
- **Efficient Sync**: Yjs minimizes bandwidth with incremental updates
- **Scalable Architecture**: Socket.io supports horizontal scaling with adapters

---

## Future Deployment

The project is structured to be containerized with Docker and deployable on AWS:
- Backend API can be deployed on EC2, ECS, or Lambda
- Frontend can be served from S3 + CloudFront
- Socket.io can leverage AWS ElastiCache for message queuing in multi-instance setups
