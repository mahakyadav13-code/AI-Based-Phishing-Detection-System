# PhishGuard AI - User Guide

## 📚 How to Use This Application

### Quick Start (3 Steps)

#### Step 1: Start the Servers

Open **TWO** PowerShell terminals:

**Terminal 1 - Backend:**
```powershell
cd "e:\Internship Project 2\backend"
.\venv\Scripts\Activate.ps1
python run.py
```

**Terminal 2 - Frontend:**
```powershell
cd "e:\Internship Project 2\frontend"
npm run dev
```

#### Step 2: Open Your Browser

Go to: **http://localhost:5173**

#### Step 3: Explore the Application

You'll see the redesigned landing page!

---

## 🌐 Accessing the Application

### From Your Computer:
```
http://localhost:5173
```

### From Other Devices on Your Network:
Check the terminal output for the network URL, it will show something like:
```
http://192.168.x.x:5173
```

---

## 🎨 What You'll See

### Landing Page Features:

1. **Navigation Bar** (Top)
   - PhishGuard AI logo
   - API status indicator (green dot = connected)

2. **Hero Section**
   - Main heading: "Intelligent Phishing Detection and Security Intelligence"
   - Description of the platform
   - Two buttons:
     - "Start Scanning" (currently navigational placeholder)
     - "View Documentation" (currently navigational placeholder)

3. **Feature Cards**
   - Email Analysis
   - URL Scanner
   - Security Dashboard
   - Awareness Training

4. **How It Works**
   - 3-step process visualization
   - Shows the detection workflow

5. **Responsible Use Policy**
   - Important guidelines
   - Safety information

6. **Footer**
   - Personal attribution: "Made by Mahak Yadav with curiosity in Cybersecurity"

---

## 🔧 Current Functionality

### ✅ What's Working Now:

1. **Landing Page**
   - Fully redesigned with clean, professional UI
   - Responsive design (works on mobile, tablet, desktop)
   - Smooth animations and hover effects

2. **API Integration**
   - Backend health check working
   - Green indicator shows "API Connected"

3. **Design System**
   - Clean, light theme
   - Professional typography (Inter font)
   - Muted, coordinated colors

### 🚧 What's Coming Next (In Development):

The following features are planned but not yet implemented:

1. **Email Analysis Page** (Phase 3)
   - Paste email content or upload .eml files
   - View phishing indicators
   - Get risk classification

2. **URL Scanner Page** (Phase 4)
   - Enter URLs to scan
   - See suspicious indicators
   - Get safety recommendations

3. **Dashboard** (Phase 2)
   - View scan statistics
   - See detection trends
   - Review recent activity

4. **Scan History** (Phase 2)
   - Browse past scans
   - Filter and search results
   - View detailed reports

5. **User Authentication** (Phase 2)
   - Login/Register
   - Save your scan history
   - Personalized dashboard

---

## 📱 Responsive Design

The application works on all screen sizes:

### Desktop (1024px and up)
- Full-width layout
- 2-column feature grid
- Optimal reading experience

### Tablet (768px - 1023px)
- Adjusted layouts
- 2-column feature grid
- Touch-friendly interactions

### Mobile (below 768px)
- Single column layout
- Stacked elements
- Mobile-optimized navigation

**Try it**: Resize your browser window to see the responsive design in action!

---

## 🎯 For Developers: How to Continue Building

### Project Structure:

```
PhishGuard-AI/
├── frontend/
│   ├── src/
│   │   ├── components/     ← Add new components here
│   │   │   ├── Navigation.jsx
│   │   │   └── Footer.jsx
│   │   ├── pages/          ← Add new pages here
│   │   │   └── LandingPage.jsx
│   │   ├── services/       ← API calls go here
│   │   │   └── api.js
│   │   └── index.css       ← Global styles & design system
│   └── package.json
│
├── backend/
│   ├── app/
│   │   ├── routes/         ← Add API endpoints here
│   │   ├── models/         ← Database models
│   │   ├── services/       ← Business logic
│   │   └── detection/      ← ML & detection logic
│   └── requirements.txt
│
└── docs/                   ← Documentation
    ├── design-system.md
    └── ui-redesign-report.md
```

### Adding New Pages:

1. **Create page component:**
   ```jsx
   // frontend/src/pages/Dashboard.jsx
   import React from 'react';
   import Navigation from '../components/Navigation';
   import Footer from '../components/Footer';

   const Dashboard = () => {
     return (
       <div className="min-h-screen bg-bgPrimary">
         <Navigation />
         {/* Your dashboard content */}
         <Footer />
       </div>
     );
   };

   export default Dashboard;
   ```

2. **Add route in App.jsx:**
   ```jsx
   import Dashboard from './pages/Dashboard';

   <Routes>
     <Route path="/" element={<LandingPage />} />
     <Route path="/dashboard" element={<Dashboard />} />
   </Routes>
   ```

3. **Use the design system:**
   - Colors: `bg-bgPrimary`, `text-textPrimary`, `text-accent`
   - Components: `.btn-primary`, `.card`, `.badge-phase`
   - Spacing: `.section`, `.section-alt`

### Adding Backend Endpoints:

1. **Create new route file:**
   ```python
   # backend/app/routes/email_routes.py
   from flask import Blueprint, jsonify, request

   email_bp = Blueprint('email', __name__)

   @email_bp.route('/analyze', methods=['POST'])
   def analyze_email():
       data = request.get_json()
       # Your analysis logic here
       return jsonify({'result': 'analyzed'})
   ```

2. **Register blueprint:**
   ```python
   # backend/app/__init__.py
   from app.routes.email_routes import email_bp
   app.register_blueprint(email_bp, url_prefix='/api/email')
   ```

---

## 🎨 Using the Design System

### Colors:

```jsx
// Backgrounds
<div className="bg-bgPrimary">      {/* Off-white */}
<div className="bg-bgSecondary">    {/* Light stone */}
<div className="bg-bgCard">         {/* White */}

// Text
<h1 className="text-textPrimary">   {/* Near black */}
<p className="text-textSecondary">  {/* Gray */}
<span className="text-textMuted">   {/* Light gray */}

// Accents
<button className="text-accent">    {/* Blue */}
```

### Components:

```jsx
// Buttons
<button className="btn-primary">Primary Action</button>
<button className="btn-secondary">Secondary Action</button>

// Cards
<div className="card">Static Card</div>
<div className="card-hover">Interactive Card</div>

// Badges
<span className="badge-phase">Label</span>
<span className="badge-safe">Safe</span>
<span className="badge-phishing">Phishing</span>

// Sections
<section className="section">Normal Section</section>
<section className="section-alt">Alternate Background</section>
```

### Full Design System Documentation:
See `docs/design-system.md` for complete details.

---

## 🔍 Testing the Application

### Manual Testing:

1. **Responsive Design:**
   - Open browser DevTools (F12)
   - Toggle device toolbar (Ctrl+Shift+M)
   - Try different screen sizes

2. **API Connection:**
   - Check the green dot in navigation
   - Open DevTools Console (F12)
   - Look for successful API calls

3. **Interactions:**
   - Hover over cards (should have subtle animation)
   - Click buttons (should change appearance)
   - Try all links and buttons

### Backend Testing:

```powershell
# From backend directory
.\venv\Scripts\Activate.ps1

# Run tests
pytest tests/ -v

# Test health endpoint
curl http://localhost:5000/api/health
```

---

## 📊 Monitoring

### Check if Servers are Running:

**Backend:**
```powershell
curl http://localhost:5000/api/health
```
✅ Should return: `{"status":"healthy",...}`

**Frontend:**
```powershell
curl http://localhost:5173
```
✅ Should return: HTML content (or just open in browser)

### Common Issues:

#### "API Disconnected" showing:
1. Check backend is running: `curl http://localhost:5000/api/health`
2. Restart backend: Stop (Ctrl+C) and run `python run.py` again
3. Check firewall isn't blocking port 5000

#### Page not loading:
1. Check frontend is running: Look for "Local: http://localhost:5173" in terminal
2. Try clearing browser cache (Ctrl+Shift+Del)
3. Restart frontend: Stop (Ctrl+C) and run `npm run dev` again

#### Blank white page:
1. Open DevTools Console (F12)
2. Look for errors
3. Check if `index.css` compiled correctly
4. Restart frontend server

---

## 🚀 Next Steps for Usage

### As a User (Current State):

Right now, you can:
1. ✅ View the redesigned landing page
2. ✅ See the professional new design
3. ✅ Check API connectivity status
4. ✅ Explore the UI on different devices

### As a Developer (What to Build):

To make it fully functional, you need to implement:

1. **Email Analysis Feature:**
   - Create email input form
   - Add email parsing logic
   - Implement phishing detection rules
   - Display results

2. **URL Scanner Feature:**
   - Create URL input form
   - Add URL analysis logic
   - Implement risk detection
   - Show indicators

3. **Dashboard:**
   - Create statistics cards
   - Add charts (using Recharts)
   - Display recent scans
   - Show trends

4. **User System:**
   - Add authentication
   - Create user accounts
   - Save scan history
   - Personal dashboard

### Learning Resources:

- **React**: https://react.dev/learn
- **Tailwind CSS**: https://tailwindcss.com/docs
- **Flask**: https://flask.palletsprojects.com/
- **Design System**: See `docs/design-system.md`

---

## 💡 Tips

### For Presentation:

1. **Show the redesign:**
   - Open side-by-side: old vs new screenshots
   - Highlight the clean, professional design
   - Demonstrate responsive behavior

2. **Explain the tech:**
   - React frontend with Vite
   - Flask backend with SQLAlchemy
   - Tailwind CSS for styling
   - Design system architecture

3. **Demo the vision:**
   - Explain what each feature will do
   - Show the workflow (submit → analyze → results)
   - Discuss security considerations

### For Development:

1. **Keep servers running:**
   - Don't close the terminal windows
   - If you must restart, use the commands above

2. **Check for errors:**
   - Backend: Look at terminal output
   - Frontend: Open browser console (F12)
   - Fix issues immediately

3. **Follow the design system:**
   - Use existing components
   - Don't add random colors
   - Maintain consistency

---

## 📞 Getting Help

### Documentation:
- **Full README**: `README.md`
- **Design System**: `docs/design-system.md`
- **Redesign Report**: `docs/ui-redesign-report.md`
- **Quick Start**: `QUICKSTART.md`
- **Server Status**: `SERVER-STATUS.md`

### Common Commands:

```powershell
# Start backend
cd backend
.\venv\Scripts\Activate.ps1
python run.py

# Start frontend
cd frontend
npm run dev

# Run tests
cd backend
.\venv\Scripts\Activate.ps1
pytest

# Install dependencies (if needed)
cd backend
pip install -r requirements.txt

cd frontend
npm install
```

---

## 🎓 Summary

**To use PhishGuard AI right now:**

1. Start both servers (backend + frontend)
2. Open http://localhost:5173 in your browser
3. Explore the redesigned landing page
4. Check the design on different screen sizes
5. See the API connection indicator working

**What's functional:**
- ✅ Landing page with new design
- ✅ Responsive layout
- ✅ API integration
- ✅ Design system

**What's coming:**
- 🚧 Email analysis
- 🚧 URL scanning
- 🚧 Dashboard
- 🚧 User authentication
- 🚧 ML detection models

**Everything is set up and ready for you to build the remaining features!**

---

**Happy Building! 🛡️**
