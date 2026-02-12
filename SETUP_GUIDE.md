# NEXUS ARCADE - Quick Setup Guide

## Prerequisites
1. **PostgreSQL** installed and running
2. **Redis** installed and running
3. **Node.js** (v14 or higher)

## Backend Setup

### 1. Install Dependencies
```bash
cd backend
npm install
```

### 2. Configure Environment Variables
```bash
# Copy the example environment file
copy .env.example .env

# Edit .env and update the following:
# - DB_PASSWORD: Your PostgreSQL password
# - JWT_SECRET: A secure random string
# - JWT_REFRESH_SECRET: Another secure random string
# - CORS_ORIGIN: Your frontend URL (e.g., http://127.0.0.1:5500)
```

### 3. Setup Database
```bash
# Connect to PostgreSQL (using psql or pgAdmin)
psql -U postgres

# Create the database
CREATE DATABASE nexus_arcade;

# Connect to the database
\c nexus_arcade

# Run the schema migration
\i migrations/001_initial_schema.sql

# Run the seed data
\i migrations/001_seed_data.sql

# Verify setup
SELECT * FROM games;
SELECT * FROM achievements;
```

### 4. Start Backend Server
```bash
npm start
```

The server should start on `http://localhost:3000`

## Frontend Setup

### 1. Open the Frontend
Simply open `index.html` in your browser using Live Server or any static file server.

**Recommended:** Use VS Code Live Server extension
- Right-click on `index.html`
- Select "Open with Live Server"
- It should open at `http://127.0.0.1:5500`

### 2. Update API URL (if needed)
If your backend runs on a different port, update the `API_BASE_URL` in `js/main.js`:
```javascript
const API_BASE_URL = 'http://localhost:3000/api';
```

## Testing the Authentication System

### 1. Register a New Account
- Click the "Login" button in the header
- Switch to "Register" tab
- Fill in:
  - Username: testplayer
  - Email: test@example.com
  - Password: password123
- Click "Create Account"

### 2. Login
- Click the "Login" button
- Enter your credentials
- Click "Login"

### 3. Verify Login
- Your username should appear in the header
- The "Login" button should change to a logout icon

## Troubleshooting

### Database Connection Issues
- Ensure PostgreSQL is running
- Check your database credentials in `.env`
- Verify the database exists: `psql -U postgres -l`

### Redis Connection Issues
- Ensure Redis is running
- Windows: Check if redis-server is running in Services
- Linux/Mac: `redis-cli ping` should return "PONG"

### CORS Issues
- Make sure `CORS_ORIGIN` in `.env` matches your frontend URL exactly
- Common URLs:
  - Live Server: `http://127.0.0.1:5500`
  - File protocol: `http://localhost:5500`

### Backend Not Starting
- Check if port 3000 is available
- Look for error messages in the console
- Verify all dependencies are installed: `npm list`

## Next Steps

Once the authentication system is working:
1. Start playing games
2. Your scores will be saved to the database
3. Check the leaderboard (once implemented)
4. Earn achievements (once implemented)

## Development Commands

### Backend
```bash
# Start server
npm start

# Start with auto-reload (if nodemon is installed)
npm run dev

# Run tests
npm test
```

### Database Management
```bash
# Connect to database
psql -U postgres -d nexus_arcade

# View all tables
\dt

# View users
SELECT * FROM users;

# View game sessions
SELECT * FROM game_sessions;

# Reset database (WARNING: Deletes all data)
DROP DATABASE nexus_arcade;
CREATE DATABASE nexus_arcade;
```

## Support

If you encounter issues:
1. Check the console for error messages
2. Verify all services are running (PostgreSQL, Redis, Backend)
3. Check the browser network tab for API call failures
4. Review the `.env` configuration
