<div align="center">

# DevCollab

### Real-time editing, seamless collaboration.

<p>
  A full-stack web application enabling multiple users to edit code simultaneously with instant synchronization using CRDTs and WebSockets.
</p>

<p>
  <img src="https://img.shields.io/badge/React-19-20232A?style=for-the-badge&logo=react&logoColor=61DAFB" alt="React" />
  <img src="https://img.shields.io/badge/Vite-7-646CFF?style=for-the-badge&logo=vite&logoColor=white" alt="Vite" />
  <img src="https://img.shields.io/badge/Node.js-Express_5-339933?style=for-the-badge&logo=node.js&logoColor=white" alt="Node" />
  <img src="https://img.shields.io/badge/Socket.io-4-black?style=for-the-badge&logo=socket.io&logoColor=white" alt="Socket.io" />
  <img src="https://img.shields.io/badge/Monaco-Editor-007ACC?style=for-the-badge&logo=visual-studio-code&logoColor=white" alt="Monaco" />
  <img src="https://img.shields.io/badge/Yjs-CRDT-4285F4?style=for-the-badge&logo=data-box&logoColor=white" alt="Yjs" />
</p>

<p>
  <img src="https://img.shields.io/badge/Status-Active-success?style=flat-square" alt="Status" />
  <img src="https://img.shields.io/badge/Build-Vite%20Ready-646CFF?style=flat-square" alt="Build" />
  <img src="https://img.shields.io/badge/Sync-Real--time-green?style=flat-square" alt="Sync" />
</p>

<p>
  <a href="#-getting-started"><strong>Quick Start</strong></a> •
  <a href="#-system-architecture"><strong>Architecture</strong></a> •
  <a href="#-features"><strong>Features</strong></a>
</p>

</div>

---

## 📚 Table of Contents
- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [System Architecture](#-system-architecture)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
- [Scripts](#-scripts)
- [Troubleshooting](#-troubleshooting)

---

## ✨ Features

- **Real-time Collaboration**: Multiple users edit simultaneously with instant synchronization
- **Live Presence**: See all connected users and their cursors in real-time
- **Conflict-free Editing**: CRDT-based conflict resolution using Yjs—no merge conflicts
- **Professional Editor**: Monaco Editor with syntax highlighting and advanced features
- **Session-based Access**: Join sessions via username query parameter
- **Graceful Disconnection**: Automatic cleanup when users leave

---

## 🛠️ Tech Stack

### 🎨 Frontend
- React 19
- Vite 7
- Tailwind CSS 4
- Monaco Editor
- Yjs (CRDT)
- Socket.io Client

### ⚙️ Backend
- Node.js + Express 5
- Socket.io 4
- y-socket.io provider
- Nodemon (dev)

---

## 🧱 System Architecture

```text
Frontend (React + Monaco)
    |
    |  Socket.io (WebSocket)
    v
Backend (Express + Socket.io)
    |
    '-- Yjs state management (CRDT)
        '-- All connected clients
```

Flow:
1. User joins session with username
2. Yjs syncs document state across clients
3. Local edits propagated via WebSocket
4. All clients merge changes conflict-free

---

## 📁 Project Structure

```
DevCollab/
├── Backend/
│   ├── server.js
│   ├── package.json
│   └── public/
│
└── Frontend/
    ├── package.json
    ├── vite.config.js
    └── src/
        ├── main.jsx
        └── app/
            ├── App.jsx
            └── App.css
```

---

## 🏁 Getting Started

### ✅ Prerequisites
- Node.js 16+
- npm 9+

### Installation

Backend:
```bash
cd Backend
npm install
npm run dev
```

Frontend:
```bash
cd Frontend
npm install
npm run dev
```

Local URLs:
- Frontend: http://localhost:5173
- Backend: http://localhost:3000

Access the app, enter your username, and share the URL with others to collaborate.

---

## 📜 Scripts

### Backend
- `npm run dev`: Start with nodemon auto-reload
- `npm run start`: Production start

### Frontend
- `npm run dev`: Start Vite dev server
- `npm run build`: Build production bundle
- `npm run lint`: Run ESLint

---

## 🩺 Troubleshooting

### Connection Issues
- Ensure backend runs on port 3000
- Check browser console for WebSocket errors
- Verify CORS settings in Express

### Sync Problems
- Refresh browser if document state diverges
- Check Socket.io connection in DevTools Network tab
- Verify Yjs provider is initialized

---

## 🗺️ Roadmap
- Docker containerization
- AWS deployment setup

---

<div align="center">
  Built with ❤️ by <a href="https://github.com/yadavaman13">Yadav Aman</a>
  
  If you found this helpful, please give it a ⭐!
</div>
