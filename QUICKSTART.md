# PhishGuard AI - Quick Start Guide

## 🚀 Quick Start (For Development)

### Prerequisites Check
```powershell
# Check Python (need 3.11+)
python --version

# Check Node.js (need 18+)
node --version

# Check npm
npm --version
```

### 1. Start Backend (Terminal 1)
```powershell
cd backend

# Activate virtual environment
.\venv\Scripts\Activate.ps1

# Run server
python run.py
```
Backend will run on **http://localhost:5000**

### 2. Start Frontend (Terminal 2)
```powershell
cd frontend

# Run development server
npm run dev
```
Frontend will run on **http://localhost:5173**

### 3. Access Application
Open your browser and visit: **http://localhost:5173**

You should see the **redesigned landing page** with:
- ✅ Clean, light theme
- ✅ Professional typography
- ✅ Muted color palette
- ✅ Card-based layout
- ✅ Responsive design
- ✅ Personalized footer

---

## 🎨 What's New in the Redesign

### Design Changes
- **Before**: Dark navy theme with neon blue accents
- **After**: Light cream theme with muted professional colors

### Key Features
- Editorial minimalist design
- Typography-driven layout with Inter font
- Coordinated semantic color system
- Subtle shadows and effects
- Professional spacing and alignment

### Color Palette
- Backgrounds: Off-white/cream (#fafaf9)
- Text: Near-black primary, gray secondary
- Accent: Muted blue (#3b82f6)
- Semantic: Green (safe), Red (phishing), Amber (suspicious)

---

## 🔧 First Time Setup

If this is your first time running the project:

### Backend Setup
```powershell
cd backend

# Create virtual environment
python -m venv venv

# Activate it
.\venv\Scripts\Activate.ps1

# Install dependencies
pip install -r requirements.txt

# Create environment file
Copy-Item ../.env.example .env
```

### Frontend Setup
```powershell
cd frontend

# Install dependencies
npm install
```

---

## ✅ Verify Installation

### Test Backend
```powershell
# Health check
curl http://localhost:5000/api/health

# Should return:
# {"service":"PhishGuard AI API","status":"healthy",...}
```

### Run Tests
```powershell
cd backend
.\venv\Scripts\Activate.ps1
pytest tests/ -v
```

---

## 🛑 Troubleshooting

### Backend won't start?
- Ensure virtual environment is activated: `.\venv\Scripts\Activate.ps1`
- Check `.env` file exists in backend directory
- Verify Python 3.11+ is installed

### Frontend won't start?
- Delete `node_modules` and run `npm install` again
- Clear npm cache: `npm cache clean --force`
- Verify Node.js 18+ is installed

### API not connecting?
- Ensure backend is running on port 5000
- Check CORS settings in `backend/app/__init__.py`
- Verify `FRONTEND_URL` in backend `.env` file

---

## 📚 Additional Commands

### Backend
```powershell
# Run with coverage
pytest --cov=app tests/

# Security scan
bandit -r app/

# Dependency check
safety check
```

### Frontend
```powershell
# Build for production
npm run build

# Preview production build
npm run preview

# Lint code
npm run lint
```

---

## 🔄 Development Workflow

1. **Morning Startup**
   - Start backend in one terminal
   - Start frontend in another terminal
   - Open http://localhost:5173 in browser

2. **Making Changes**
   - Backend changes auto-reload (Flask debug mode)
   - Frontend changes auto-reload (Vite HMR)
   - Just save your files and refresh

3. **Before Committing**
   - Run backend tests: `pytest`
   - Check for security issues: `bandit -r app/`
   - Lint frontend: `npm run lint`

---

## 📝 Important Notes

- **Never commit** `.env` files or secrets
- **Always activate** virtual environment before backend work
- **Port 5000** = Backend API
- **Port 5173** = Frontend UI
- **Health check** at `/api/health` to verify backend

---

## 🎯 Current Phase

**Phase 1**: Complete ✅  
**Phase 2**: Backend and Database (Next)

See `docs/phase1-completion-report.md` for detailed Phase 1 results.

---

## 💡 Tips

- Keep both terminals open during development
- Use `Ctrl+C` to stop servers
- Check logs in terminal if something fails
- API responses are JSON formatted
- UI updates live with Vite Hot Module Replacement

---

**Happy Coding! 🛡️**
