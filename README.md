# ChatApp

Production-ready real-time chat application with private chat, group chat, file sharing, and WebRTC calling.

## Features
- JWT authentication (register/login/protected routes)
- Friend request flow before private chat starts
- 1:1 and group conversations
- Group management:
    - create group, update name/description/photo
    - add/remove members
    - admin transfer and leave-group rules
    - centered system updates (join/remove/leave/profile changes)
- Real-time messaging with Socket.IO
- Reply, edit, delete-for-me, delete-for-everyone
- Unread counters (direct + group)
- Typing and presence indicators
- Voice and video calling (WebRTC)
- Image/file uploads

## Tech Stack
- Frontend: React, React Router, Socket.IO Client, Axios, date-fns
- Backend: Node.js, Express, Socket.IO
- Database: MySQL + Sequelize
- Auth: JWT + bcryptjs
- Uploads: Multer

## Project Structure
```text
chatapp-fixed/
    backend/
        config/
        controllers/
        middleware/
        models/
        routes/
        socket/
        server.js
    frontend/
        public/
        src/
            components/
            context/
            pages/
            utils/
```

## Local Setup

### 1) Create MySQL database
```sql
CREATE DATABASE chatapp_db CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```

### 2) Backend setup
```bash
cd backend
npm install
```

Create .env in backend folder:
```env
PORT=5000
DB_HOST=localhost
DB_PORT=3306
DB_NAME=chatapp_db
DB_USER=root
DB_PASSWORD=your_password
JWT_SECRET=your_super_secret_key
JWT_EXPIRES_IN=7d
CLIENT_URL=http://localhost:3000
MAX_FILE_SIZE=10485760
DB_SYNC_ALTER=false
NODE_ENV=development
```

Run backend:
```bash
npm run dev
```

### 3) Frontend setup
```bash
cd ../frontend
npm install
npm start
```

App URLs:
- Frontend: http://localhost:3000
- Backend API: http://localhost:5000

## Build
```bash
cd frontend
npm run build
```

## Deployment Notes
- Set production environment variables on your server/platform.
- Ensure MySQL is reachable from backend runtime.
- Set CORS client URL to your deployed frontend domain.
- Serve frontend build as static site and run backend as a Node service.
- Use HTTPS in production for auth tokens and WebRTC reliability.

## Recommended .gitignore
```gitignore
# dependencies
node_modules/

# env files
.env
backend/.env
frontend/.env

# build output
frontend/build/

# uploads (optional: keep if you want local media in repo)
backend/uploads/avatars/
backend/uploads/files/

# logs
npm-debug.log*
yarn-debug.log*
yarn-error.log*

# OS
.DS_Store
Thumbs.db
```

## License
This project is for personal/educational use. Add a license file if you plan to distribute publicly.
