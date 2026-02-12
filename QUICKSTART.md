# 🚀 NEXUS ARCADE - Quick Start Guide

## ⚡ Fast Setup (5 Minutes)

### Prerequisites Check
- ✅ PostgreSQL installed and running
- ✅ Redis installed and running (optional for basic features)
- ✅ Node.js v18+ installed

### Step 1: Install Backend Dependencies (1 min)
```bash
cd backend
npm install
```

### Step 2: Setup Database (1 min)
```bash
# The .env file is already configured with default settings
# Just make sure PostgreSQL password matches (default: postgres)

# Run automated database setup
npm run setup-db
```

This will:
- Create the `nexus_arcade` database
- Create all tables (users, games, high_scores, achievements, etc.)
- Seed 6 games and 50+ achievements

### Step 3: Start Backend Server (10 sec)
```bash
npm start
```

You should see:
```
╔════════════════════════════════════════╗
║   NEXUS ARCADE Backend API Server     ║
╠════════════════════════════════════════╣
║   Status: Running                      ║
║   Port: 3000                          ║
╚════════════════════════════════════════╝
```

### Step 4: Open Frontend (10 sec)
1. Open `index.html` with Live Server (VS Code extension)
2. Or use any static server pointing to the root directory
3. Default URL: `http://127.0.0.1:5500`

### Step 5: Test Authentication (1 min)
1. Click **"Login"** button in the header
2. Switch to **"Register"** tab
3. Create account:
   - Username: `testplayer`
   - Email: `test@example.com`
   - Password: `password123`
4. Click **"Create Account"**
5. Your username should appear in the header! 🎉

## ✅ Verification Checklist

- [ ] Backend server running on port 3000
- [ ] Frontend accessible in browser
- [ ] Can register a new account
- [ ] Can login with credentials
- [ ] Username appears in header when logged in
- [ ] Can logout successfully
- [ ] Login persists after page refresh

## 🎮 What's Working Now

### ✅ Completed Features:
1. **Authentication System**
   - Register new users
   - Login with email/password
   - JWT token authentication
   - Persistent sessions
   - Secure password hashing

2. **User Interface**
   - Neon-themed login/register modal
   - Username display in header
   - Login/logout functionality
   - Beautiful animations

3. **Backend Infrastructure**
   - Express.js API server
   - PostgreSQL database with full schema
   - Redis configuration (ready to use)
   - Rate limiting & security
   - Error handling

4. **Database**
   - User management system
   - Game session tracking (ready)
   - High score system (ready)
   - Achievement system (ready)
   - Friendship system (ready)

### 🚧 Coming Next (Not Yet Implemented):
- Game score submission
- Live leaderboards
- User profiles
- Achievement unlocking
- Friend system
- Daily challenges

## 🔧 Troubleshooting

### Backend won't start
```bash
# Check if PostgreSQL is running
psql -U postgres -c "SELECT version();"

# Check if port 3000 is available
netstat -ano | findstr :3000

# Reinstall dependencies
cd backend
rm -rf node_modules
npm install
```

### Database setup fails
```bash
# Manually create database
psql -U postgres
CREATE DATABASE nexus_arcade;

# Then run migrations manually
cd backend
psql -U postgres -d nexus_arcade -f migrations/001_initial_schema.sql
psql -U postgres -d nexus_arcade -f migrations/001_seed_data.sql
```

### Can't login / CORS errors
1. Check `backend/.env` file exists
2. Verify `CORS_ORIGIN=http://127.0.0.1:5500` matches your frontend URL
3. Restart backend server after changing .env

### Redis connection errors
Redis is optional for basic functionality. To disable Redis warnings:
- Comment out Redis initialization in `backend/server.js`
- Or install and start Redis server

## 📁 Project Structure

```
game-website/
├── index.html              # Main frontend page
├── css/
│   └── style.css          # Styles with auth modal
├── js/
│   ├── main.js            # Auth logic & UI management
│   └── games.js           # Game implementations
├── backend/
│   ├── server.js          # Main server file
│   ├── .env               # Environment configuration
│   ├── setup-database.js  # Database setup script
│   ├── config/
│   │   ├── database.js    # PostgreSQL connection
│   │   └── redis.js       # Redis connection
│   ├── routes/
│   │   └── auth.js        # Authentication endpoints
│   ├── middleware/
│   │   ├── auth.js        # JWT verification
│   │   ├── rateLimiter.js # Rate limiting
│   │   └── errorHandler.js # Error handling
│   └── migrations/
│       ├── 001_initial_schema.sql  # Database schema
│       └── 001_seed_data.sql       # Initial data
└── QUICKSTART.md          # This file
```

## 🔑 Default Configuration

### Database
- Host: `localhost`
- Port: `5432`
- Database: `nexus_arcade`
- User: `postgres`
- Password: `postgres` (change in `.env`)

### Backend
- Port: `3000`
- Environment: `development`

### Frontend
- Default: `http://127.0.0.1:5500` (Live Server)

## 📚 Next Steps

1. **Play some games** - All 6 games are playable!
2. **Check the database** - View registered users and game data
3. **Explore the code** - Learn how authentication works
4. **Read documentation** - Check `AUTH_IMPLEMENTATION.md` and `SETUP_GUIDE.md`

## 🎯 Development Commands

```bash
# Backend commands (run from backend/ directory)
npm start          # Start server
npm run dev        # Start with auto-reload (if nodemon installed)
npm run setup-db   # Setup database

# Database commands
psql -U postgres -d nexus_arcade    # Connect to database
\dt                                  # List all tables
SELECT * FROM users;                # View users
SELECT * FROM games;                # View games
SELECT * FROM achievements;         # View achievements
```

## 🆘 Getting Help

If you encounter issues:
1. Check the console for error messages (browser & terminal)
2. Verify all services are running (PostgreSQL, Redis, Backend)
3. Review `.env` configuration
4. Check network tab in browser DevTools
5. Read detailed guides in `SETUP_GUIDE.md`

## 🎉 Success!

Once you see your username in the header after logging in, you're all set! The authentication system is working perfectly. Welcome to NEXUS ARCADE! 🎮✨
