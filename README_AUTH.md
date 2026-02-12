# 🎮 NEXUS ARCADE - Authentication System

## 🌟 Overview

A complete, secure, and beautiful authentication system for NEXUS ARCADE gaming platform with:
- ✨ Neon-themed UI
- 🔐 JWT authentication
- 💾 PostgreSQL database
- 🚀 Express.js backend
- 🎨 Glassmorphism design

## 📸 Screenshots (Visual Description)

### Login Modal
```
┌─────────────────────────────────────────────┐
│  ✕                                          │
│                                             │
│          Welcome Back                       │
│    Login to continue your journey           │
│                                             │
│  📧 Email                                   │
│  ┌───────────────────────────────────────┐ │
│  │ your.email@example.com                │ │
│  └───────────────────────────────────────┘ │
│                                             │
│  🔒 Password                                │
│  ┌───────────────────────────────────────┐ │
│  │ ••••••••••••                          │ │
│  └───────────────────────────────────────┘ │
│                                             │
│  ☑ Remember me      Forgot password?       │
│                                             │
│  ┌───────────────────────────────────────┐ │
│  │         🔑 Login                      │ │
│  └───────────────────────────────────────┘ │
│                                             │
│  Don't have an account? Register here       │
│                                             │
└─────────────────────────────────────────────┘
```

### Registration Modal
```
┌─────────────────────────────────────────────┐
│  ✕                                          │
│                                             │
│           Join NEXUS                        │
│  Create your account and start playing      │
│                                             │
│  👤 Username                                │
│  ┌───────────────────────────────────────┐ │
│  │ Choose a username                     │ │
│  └───────────────────────────────────────┘ │
│                                             │
│  📧 Email                                   │
│  ┌───────────────────────────────────────┐ │
│  │ your.email@example.com                │ │
│  └───────────────────────────────────────┘ │
│                                             │
│  🔒 Password                                │
│  ┌───────────────────────────────────────┐ │
│  │ Create a password                     │ │
│  └───────────────────────────────────────┘ │
│                                             │
│  🔒 Confirm Password                        │
│  ┌───────────────────────────────────────┐ │
│  │ Confirm your password                 │ │
│  └───────────────────────────────────────┘ │
│                                             │
│  ☑ I agree to the Terms & Conditions       │
│                                             │
│  ┌───────────────────────────────────────┐ │
│  │      👥 Create Account                │ │
│  └───────────────────────────────────────┘ │
│                                             │
│  Already have an account? Login here        │
│                                             │
└─────────────────────────────────────────────┘
```

### Header (Logged Out)
```
╔═══════════════════════════════════════════════════════════╗
║  🎮 NEXUS ARCADE  │  Home  Favorites  Leaderboard         ║
║                   │                      👤 Guest  🔑Login ║
╚═══════════════════════════════════════════════════════════╝
```

### Header (Logged In)
```
╔═══════════════════════════════════════════════════════════╗
║  🎮 NEXUS ARCADE  │  Home  Favorites  Leaderboard         ║
║                   │              👤 PlayerName  🚪 Logout  ║
╚═══════════════════════════════════════════════════════════╝
```

## 🎯 Features

### User Interface
- ✅ Beautiful neon-themed modal design
- ✅ Smooth animations and transitions
- ✅ Responsive mobile-friendly layout
- ✅ Glassmorphism effects
- ✅ Real-time form validation
- ✅ Toast notifications
- ✅ Dynamic username display

### Authentication
- ✅ User registration
- ✅ User login
- ✅ Secure logout
- ✅ Session persistence
- ✅ Auto-login on page load
- ✅ Token refresh capability
- ✅ Login streak tracking

### Security
- ✅ Password hashing (bcrypt)
- ✅ JWT token authentication
- ✅ Input validation (Joi)
- ✅ CORS protection
- ✅ Rate limiting
- ✅ SQL injection prevention
- ✅ XSS protection

## 🚀 Quick Start

### 1. Prerequisites
```bash
# Install PostgreSQL
# Download from: https://www.postgresql.org/download/

# Install Node.js
# Download from: https://nodejs.org/

# Install Redis (optional)
# Download from: https://redis.io/download/
```

### 2. Setup Backend
```bash
cd backend
npm install
npm run setup-db
npm start
```

### 3. Open Frontend
```bash
# Open index.html with Live Server
# Or use any static file server
```

### 4. Test Authentication
1. Click "Login" in header
2. Switch to "Register"
3. Create account
4. Login with credentials
5. See your username in header! 🎉

## 🔧 Configuration

### Environment Variables (backend/.env)
```env
# Server
PORT=3000
NODE_ENV=development

# Database
DB_HOST=localhost
DB_PORT=5432
DB_NAME=nexus_arcade
DB_USER=postgres
DB_PASSWORD=postgres

# JWT
JWT_SECRET=your_secret_key_here
JWT_REFRESH_SECRET=your_refresh_secret_here

# CORS
CORS_ORIGIN=http://127.0.0.1:5500
```

## 📡 API Endpoints

### POST /api/auth/register
Register a new user account.

**Request:**
```json
{
  "username": "player123",
  "email": "player@example.com",
  "password": "securepass123"
}
```

**Response:**
```json
{
  "message": "User registered successfully",
  "user": {
    "userId": "uuid-here",
    "username": "player123",
    "email": "player@example.com",
    "xp": 0,
    "level": 1,
    "points": 0
  },
  "accessToken": "jwt-token-here",
  "refreshToken": "refresh-token-here"
}
```

### POST /api/auth/login
Login to existing account.

**Request:**
```json
{
  "email": "player@example.com",
  "password": "securepass123"
}
```

**Response:**
```json
{
  "message": "Login successful",
  "user": {
    "userId": "uuid-here",
    "username": "player123",
    "email": "player@example.com",
    "xp": 100,
    "level": 2,
    "points": 500,
    "loginStreak": 5
  },
  "accessToken": "jwt-token-here",
  "refreshToken": "refresh-token-here"
}
```

### POST /api/auth/refresh
Refresh access token.

**Request:**
```json
{
  "refreshToken": "refresh-token-here"
}
```

**Response:**
```json
{
  "accessToken": "new-jwt-token-here"
}
```

### POST /api/auth/logout
Logout current session.

**Response:**
```json
{
  "message": "Logout successful"
}
```

## 🎨 Design System

### Colors
```css
--primary: #00ff9d      /* Neon green */
--secondary: #00d4ff    /* Neon blue */
--accent: #ff00ff       /* Neon pink */
--danger: #ff3366       /* Error red */
--dark: #0a0e27         /* Background */
--glass: rgba(26, 31, 58, 0.7)  /* Glassmorphism */
```

### Typography
```css
Font: 'Rajdhani' (body)
Font: 'Orbitron' (headings)
```

### Effects
- Glassmorphism backgrounds
- Neon glow shadows
- Smooth transitions
- Backdrop blur
- Gradient borders

## 💾 Database Schema

### Users Table
```sql
CREATE TABLE users (
  user_id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  username VARCHAR(50) UNIQUE NOT NULL,
  email VARCHAR(255) UNIQUE NOT NULL,
  password_hash VARCHAR(255) NOT NULL,
  xp INTEGER DEFAULT 0,
  level INTEGER DEFAULT 1,
  points INTEGER DEFAULT 0,
  login_streak INTEGER DEFAULT 0,
  last_login TIMESTAMP,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

## 🔒 Security Features

### Password Security
- Bcrypt hashing with 10 salt rounds
- Minimum 6 character requirement
- Password confirmation matching
- Never stored in plain text

### Token Security
- JWT signed tokens
- Short-lived access tokens (1 hour)
- Long-lived refresh tokens (7 days)
- Secure token storage in localStorage

### API Security
- CORS protection
- Rate limiting (5 requests per 15 min for auth)
- Helmet middleware
- Input validation with Joi
- SQL injection prevention
- XSS protection

## 📊 State Management

### Frontend State
```javascript
// Global state
currentUser = {
  userId: "uuid",
  username: "player123",
  email: "player@example.com",
  xp: 100,
  level: 2,
  points: 500,
  loginStreak: 5
}

// LocalStorage
localStorage.accessToken    // JWT access token
localStorage.refreshToken   // JWT refresh token
localStorage.userData       // User data JSON
```

### Auth Flow
```
User Action (Login/Register)
    ↓
Frontend Validation
    ↓
API Request to Backend
    ↓
Backend Validation
    ↓
Password Hash/Verify
    ↓
Generate JWT Tokens
    ↓
Return User + Tokens
    ↓
Store in localStorage
    ↓
Update UI
    ↓
Show Success Notification
```

## 🧪 Testing

### Manual Testing
```bash
# Test Registration
1. Open http://127.0.0.1:5500
2. Click "Login"
3. Switch to "Register"
4. Fill form and submit
5. Check: Username appears in header

# Test Login
1. Logout if logged in
2. Click "Login"
3. Enter credentials
4. Check: Username appears in header

# Test Persistence
1. Login to account
2. Refresh page
3. Check: Still logged in

# Test Logout
1. Click logout button
2. Check: Shows "Guest"
```

### Database Testing
```sql
-- Check registered users
SELECT * FROM users;

-- Check login streaks
SELECT username, login_streak, last_login FROM users;

-- Check user count
SELECT COUNT(*) FROM users;
```

## 📁 File Structure

```
game-website/
├── index.html                   # Auth modal HTML
├── css/
│   └── style.css               # Auth modal styles
├── js/
│   └── main.js                 # Auth logic
├── backend/
│   ├── routes/
│   │   └── auth.js            # Auth endpoints
│   ├── middleware/
│   │   └── auth.js            # JWT verification
│   └── config/
│       └── database.js        # DB connection
└── docs/
    ├── QUICKSTART.md          # Quick start guide
    ├── SETUP_GUIDE.md         # Detailed setup
    └── AUTH_IMPLEMENTATION.md  # Technical docs
```

## 🐛 Troubleshooting

### Common Issues

**Cannot connect to database**
```bash
# Check PostgreSQL is running
psql -U postgres -c "SELECT version();"

# Check credentials in .env
DB_PASSWORD=your_actual_password
```

**CORS errors**
```bash
# Update CORS_ORIGIN in .env to match frontend URL
CORS_ORIGIN=http://127.0.0.1:5500
```

**Token expired errors**
```javascript
// Tokens expire after 1 hour
// Use refresh token to get new access token
// Or login again
```

## 📚 Documentation

- `QUICKSTART.md` - Get started in 5 minutes
- `SETUP_GUIDE.md` - Detailed setup instructions
- `AUTH_IMPLEMENTATION.md` - Technical documentation
- `IMPLEMENTATION_COMPLETE.md` - Project summary

## 🎉 Success Criteria

✅ **All Requirements Met:**
- Login page implemented
- Register page implemented
- Username shown when logged in
- Guest shown when logged out
- Beautiful neon-themed UI
- Secure authentication
- Persistent sessions
- Full documentation

## 📞 Support

For issues or questions:
1. Check the documentation files
2. Review console errors (browser + terminal)
3. Verify all services are running
4. Check configuration in `.env`

## 🌟 Credits

**Built with:**
- Express.js - Backend framework
- PostgreSQL - Database
- JWT - Authentication
- Bcrypt - Password hashing
- Joi - Validation
- Font Awesome - Icons

**Design:**
- Neon theme with glassmorphism
- Inspired by cyberpunk aesthetics
- Smooth animations and transitions

---

**Version:** 1.0.0  
**Status:** ✅ Production Ready  
**Last Updated:** November 2, 2025
