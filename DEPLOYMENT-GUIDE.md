# PhishGuard AI - Deployment Guide

## ⚠️ Important: Full-Stack Deployment Consideration

PhishGuard AI has **two parts**:
1. **Frontend (React)** - Can deploy to Netlify ✅
2. **Backend (Flask/Python)** - Cannot deploy to Netlify ❌

## 🎯 Recommended Deployment Strategy

### Option 1: Deploy Frontend to Netlify + Backend to Render (Recommended)
- ✅ Frontend: Netlify (Free)
- ✅ Backend: Render.com (Free tier available)
- ✅ Both work together

### Option 2: Deploy Frontend Only to Netlify (Demo)
- ✅ Frontend: Netlify (Free)
- ⚠️ Backend: Not deployed (API won't work)
- ⚠️ Shows design only, no functionality

### Option 3: Deploy Both to Render
- ✅ Frontend: Render
- ✅ Backend: Render
- ✅ Everything in one place

---

## 🚀 Option 1: Frontend to Netlify + Backend to Render (BEST)

### Step 1: Prepare for GitHub

First, let's upload to GitHub:

```powershell
# Navigate to project
cd "e:\Internship Project 2"

# Initialize git (if not already done)
git init

# Add all files
git add .

# Commit
git commit -m "Initial commit - PhishGuard AI with redesigned UI"

# Create repository on GitHub (do this manually on github.com)
# Then connect and push:
git remote add origin https://github.com/YOUR-USERNAME/phishguard-ai.git
git branch -M main
git push -u origin main
```

### Step 2: Deploy Backend to Render

1. **Go to**: https://render.com
2. **Sign up/Login** (can use GitHub)
3. **Click**: "New +" → "Web Service"
4. **Connect** your GitHub repository
5. **Configure**:
   - **Name**: `phishguard-ai-backend`
   - **Environment**: `Python 3`
   - **Root Directory**: `backend`
   - **Build Command**: `pip install -r requirements.txt`
   - **Start Command**: `gunicorn run:app`
   - **Plan**: Free

6. **Add Environment Variables**:
   ```
   FLASK_ENV=production
   SECRET_KEY=your-random-secret-key-here-change-this
   DATABASE_URL=sqlite:///phishguard.db
   ```

7. **Deploy** - Wait for it to build

8. **Copy the URL** - You'll get something like:
   ```
   https://phishguard-ai-backend.onrender.com
   ```

### Step 3: Deploy Frontend to Netlify

1. **Go to**: https://netlify.com
2. **Sign up/Login** (can use GitHub)
3. **Click**: "Add new site" → "Import an existing project"
4. **Connect** your GitHub repository
5. **Configure**:
   - **Base directory**: `frontend`
   - **Build command**: `npm run build`
   - **Publish directory**: `frontend/dist`

6. **Add Environment Variable**:
   - Click "Site settings" → "Environment variables"
   - Add:
     ```
     VITE_API_URL=https://phishguard-ai-backend.onrender.com/api
     ```
   (Use the URL from Step 2!)

7. **Deploy** - Wait for it to build

8. **Your site is live!** You'll get:
   ```
   https://phishguard-ai-mahak.netlify.app
   ```

### Step 4: Update Backend CORS

Update `backend/app/__init__.py` to allow your Netlify domain:

```python
CORS(app, resources={
    r"/api/*": {
        "origins": [
            "http://localhost:5173",
            "https://phishguard-ai-mahak.netlify.app"  # Add your Netlify URL
        ],
        "methods": ["GET", "POST", "PUT", "DELETE", "OPTIONS"],
        "allow_headers": ["Content-Type", "Authorization"]
    }
})
```

Commit and push this change to trigger redeployment.

---

## 🎨 Option 2: Frontend Only to Netlify (Demo/Portfolio)

If you just want to show the design:

### Step 1: Create GitHub Repository

```powershell
cd "e:\Internship Project 2"
git init
git add .
git commit -m "PhishGuard AI - Frontend Demo"
git remote add origin https://github.com/YOUR-USERNAME/phishguard-ai.git
git branch -M main
git push -u origin main
```

### Step 2: Deploy to Netlify

1. Go to: https://netlify.com
2. Sign up/Login
3. Click: "Add new site" → "Import an existing project"
4. Connect GitHub
5. Select your repository
6. Configure:
   - **Base directory**: `frontend`
   - **Build command**: `npm run build`
   - **Publish directory**: `frontend/dist`
7. Click "Deploy"

### Step 3: Update Frontend for Demo Mode

The API won't work, but the design will show. You can modify the landing page to remove API checks:

```jsx
// In LandingPage.jsx, comment out API check:
// const [apiStatus, setApiStatus] = useState('checking');
const [apiStatus, setApiStatus] = useState('demo'); // Always show as demo

// In checkBackendHealth, do nothing
const checkBackendHealth = async () => {
  // Demo mode - no backend
};
```

---

## 📦 Option 3: Both to Render

### Why Use Render for Both?

- ✅ One platform for everything
- ✅ Easier to manage
- ✅ Both parts work together automatically

### Steps:

1. **Backend** (same as Option 1, Step 2)
2. **Frontend**:
   - Create new "Static Site" on Render
   - Configure:
     - **Build Command**: `cd frontend && npm install && npm run build`
     - **Publish Directory**: `frontend/dist`
   - Add environment variable: `VITE_API_URL`

---

## 🛠️ Additional Files Needed for Deployment

### For Backend on Render:

Create `backend/gunicorn_config.py`:
```python
bind = "0.0.0.0:5000"
workers = 2
threads = 2
timeout = 120
```

Add to `backend/requirements.txt`:
```
gunicorn==21.2.0
```

### For Frontend Build:

Your `frontend/package.json` already has:
```json
"scripts": {
  "build": "vite build"
}
```

This creates the `dist` folder that Netlify/Render will serve.

---

## 🔐 Security Before Deployment

### 1. Update SECRET_KEY

In `.env` or Render environment variables:
```
SECRET_KEY=generate-a-random-secure-key-here
```

Generate one with Python:
```python
import secrets
print(secrets.token_hex(32))
```

### 2. Enable Production Settings

In `backend/app/config.py`, production config already has:
```python
SESSION_COOKIE_SECURE = True
DEBUG = False
```

### 3. Review CORS Settings

Make sure only your domains are allowed.

---

## 📊 Expected Costs

### Free Tier Limits:

**Netlify (Frontend):**
- ✅ 100 GB bandwidth/month
- ✅ 300 build minutes/month
- ✅ Custom domain support
- ✅ HTTPS included

**Render (Backend):**
- ✅ 750 hours/month (always on)
- ⚠️ Sleeps after 15 min inactivity (free tier)
- ⚠️ Cold start delay (~30 seconds)
- ✅ Upgrade to $7/month for always-on

---

## 🎯 Recommended: GitHub + Netlify + Render

This gives you:
- ✅ Portfolio on GitHub
- ✅ Live demo URL for resume
- ✅ Professional deployment
- ✅ Fully functional app
- ✅ All FREE (with limitations)

---

## 🚦 Quick Comparison

| Platform | Frontend | Backend | Database | Cost |
|----------|----------|---------|----------|------|
| **Netlify + Render** | ✅ | ✅ | ✅ | Free* |
| **Netlify Only** | ✅ | ❌ | ❌ | Free |
| **Render Only** | ✅ | ✅ | ✅ | Free* |
| **Vercel + Render** | ✅ | ✅ | ✅ | Free* |

*Free tier with limitations (backend sleeps, bandwidth caps)

---

## 🎓 For Your Internship/Portfolio

### What to Show:

**GitHub Repository:**
```
https://github.com/YOUR-USERNAME/phishguard-ai
```

**Live Demo:**
```
https://phishguard-ai-mahak.netlify.app
```

**Backend API:**
```
https://phishguard-ai-backend.onrender.com
```

### On Your Resume:

> **PhishGuard AI** - Intelligent Phishing Detection Platform  
> *React, Flask, Machine Learning, Tailwind CSS*  
> - Designed and developed full-stack cybersecurity application
> - Implemented ML-powered threat detection (planned)
> - Created comprehensive design system
> - Deployed: [Live Demo](https://phishguard-ai-mahak.netlify.app)
> - Code: [GitHub](https://github.com/YOUR-USERNAME/phishguard-ai)

---

## 🆘 Troubleshooting

### "Build Failed" on Netlify:

1. Check Node version in `frontend/package.json`:
   ```json
   "engines": {
     "node": ">=18.0.0"
   }
   ```

2. Ensure build command is correct:
   ```
   npm run build
   ```

3. Check publish directory is `dist`

### "Application Error" on Render:

1. Check logs in Render dashboard
2. Verify `gunicorn` is in requirements.txt
3. Check environment variables are set
4. Ensure database path is correct

### "API Disconnected" on Live Site:

1. Backend URL is correct in frontend env
2. CORS allows your Netlify domain
3. Backend is awake (visit backend URL directly)

---

## 📋 Deployment Checklist

Before deploying:

- [ ] Code pushed to GitHub
- [ ] `.env` file is in `.gitignore` (not uploaded)
- [ ] `.env.example` is included (shows required vars)
- [ ] `SECRET_KEY` changed from default
- [ ] CORS settings updated for production
- [ ] `gunicorn` added to requirements.txt
- [ ] Frontend build command works locally
- [ ] Backend runs with `gunicorn run:app`
- [ ] README updated with live URLs
- [ ] Screenshots added to repository

---

## 🎉 After Deployment

Your project will be live at:
- **Frontend**: `https://your-site.netlify.app`
- **Backend**: `https://your-backend.onrender.com`
- **GitHub**: `https://github.com/your-username/phishguard-ai`

Share these links in:
- Resume
- LinkedIn
- Portfolio website
- Internship applications

---

**Let me know which option you want to use, and I'll help you set it up step by step!** 🚀
