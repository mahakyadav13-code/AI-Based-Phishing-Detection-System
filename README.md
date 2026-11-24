# PhishGuard AI 🛡️

> Intelligent Phishing Detection and Security Awareness Platform

[![Python](https://img.shields.io/badge/Python-3.11+-blue.svg)](https://www.python.org/)
[![React](https://img.shields.io/badge/React-18.2+-61DAFB.svg)](https://reactjs.org/)
[![Flask](https://img.shields.io/badge/Flask-3.0-000000.svg)](https://flask.palletsprojects.com/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

PhishGuard AI is an enterprise-grade web platform that leverages machine learning and explainable AI to detect phishing threats in emails and URLs. It provides comprehensive security awareness training through safe, controlled simulations.

## 🌟 Features

- **Email Phishing Analysis** - Advanced detection with header inspection and content analysis
- **URL Threat Scanner** - Real-time URL risk assessment without visiting malicious sites
- **Machine Learning Detection** - AI-powered classification with explainable results
- **Security Dashboard** - Comprehensive analytics and trend visualization
- **Awareness Training** - Safe phishing simulations with educational feedback
- **Scan History** - Complete audit trail with detailed reports
- **Modern UI** - Clean, editorial-minimalist design with professional aesthetics

## 🎨 Design

PhishGuard AI features a premium, minimalist interface inspired by modern developer tools:

- **Editorial Minimalist** aesthetic
- **Typography-driven** design with Inter font
- **Muted color palette** with coordinated semantic colors
- **Card-based layout** with subtle shadows
- **Responsive design** for all devices
- **Professional spacing** and alignment

Design reference: Modern AI/ML platform aesthetics with clean information architecture.

## 🏗️ Architecture

PhishGuard AI follows a modern three-tier architecture:

- **Frontend**: React + Vite + Tailwind CSS
- **Backend**: Flask + SQLAlchemy + RESTful API
- **ML Pipeline**: scikit-learn + pandas + NumPy

See [Architecture Documentation](docs/architecture.md) for detailed information.

## 🛠️ Technology Stack

### Frontend
- React 18.2+ with Vite
- Tailwind CSS for premium UI
- Axios for API communication
- Lucide React for icons
- Recharts for data visualization

### Backend
- Python 3.11+
- Flask 3.0 with Blueprints
- SQLAlchemy 2.0 ORM
- Flask-Migrate for database migrations
- Flask-Limiter for rate limiting
- Flask-CORS for secure cross-origin requests

### Machine Learning
- scikit-learn for model training
- pandas & NumPy for data processing
- joblib for model persistence

### Database
- SQLite (development)
- MySQL 8.0 (production-ready)

## 📋 Prerequisites

- **Python**: 3.11 or higher
- **Node.js**: 18 LTS or higher
- **npm**: 9.0 or higher
- **Git**: Latest version

Optional:
- MySQL 8.0 (for production database)
- Docker & Docker Compose (for containerized MySQL)

## 🚀 Installation

### 1. Clone the Repository

```bash
git clone <repository-url>
cd PhishGuard-AI
```

### 2. Backend Setup

```bash
cd backend

# Create virtual environment
python -m venv venv

# Activate virtual environment
# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Set up environment variables
cp ../.env.example .env
# Edit .env with your configuration

# Initialize database
flask db init
flask db migrate -m "Initial migration"
flask db upgrade
```

### 3. Frontend Setup

```bash
cd frontend

# Install dependencies
npm install

# Create environment file (optional)
# VITE_API_URL=http://localhost:5000/api
```

## ▶️ Running the Application

### Start Backend Server

```bash
cd backend
# Activate virtual environment if not already active
venv\Scripts\activate  # Windows
# source venv/bin/activate  # macOS/Linux

python run.py
```

Backend will run on `http://localhost:5000`

### Start Frontend Development Server

```bash
cd frontend
npm run dev
```

Frontend will run on `http://localhost:5173`

### Access the Application

Open your browser and navigate to `http://localhost:5173`

## 🧪 Running Tests

### Backend Tests

```bash
cd backend
pytest
pytest --cov=app tests/  # With coverage
```

### Security Scanning

```bash
cd backend
bandit -r app/  # Security vulnerability scan
safety check    # Dependency vulnerability check
```

## 📁 Project Structure

```
PhishGuard-AI/
├── frontend/              # React frontend application
│   ├── src/
│   │   ├── components/   # Reusable UI components
│   │   ├── pages/        # Page components
│   │   ├── services/     # API service layer
│   │   └── assets/       # Static assets
│   └── package.json
│
├── backend/              # Flask backend application
│   ├── app/
│   │   ├── models/      # Database models
│   │   ├── routes/      # API endpoints
│   │   ├── services/    # Business logic
│   │   ├── detection/   # Detection engines
│   │   └── security/    # Security utilities
│   ├── tests/           # Test suite
│   └── requirements.txt
│
├── ml/                  # Machine learning pipeline
│   ├── datasets/        # Training datasets
│   ├── notebooks/       # Jupyter notebooks
│   ├── training/        # Training scripts
│   └── models/          # Trained models
│
├── docs/                # Documentation
│   ├── architecture.md
│   ├── database-schema.md
│   ├── model-card.md
│   └── security-report.md
│
├── .env.example         # Environment template
├── .gitignore
├── LICENSE
└── README.md
```

## 🔒 Security

PhishGuard AI implements multiple security measures:

- CSRF protection on all endpoints
- Rate limiting to prevent abuse
- Input validation and sanitization
- SQL injection prevention via ORM
- XSS prevention through output encoding
- Secure session management
- Security headers configuration
- Dependency vulnerability scanning

**Important**: This is an educational tool. Never use it to send deceptive emails to real users or collect real credentials.

## 📊 Development Status

**Current Phase**: UI/UX Redesign - Landing Page Complete ✅

- [x] Project structure initialized
- [x] Backend foundation with Flask
- [x] Frontend foundation with React
- [x] **Landing page with premium redesigned UI** ✨
- [x] Design system established
- [x] Reusable components created
- [x] Health check endpoint
- [x] API communication established
- [ ] Dashboard page redesign (In Progress)
- [ ] Email analysis page (Pending)
- [ ] URL detection page (Pending)
- [ ] Database models (Phase 2)
- [ ] Email analysis (Phase 3)
- [ ] URL detection (Phase 4)
- [ ] Machine learning (Phase 5)
- [ ] Complete UI (Phase 6)
- [ ] Security testing (Phase 7)
- [ ] Documentation (Phase 8)

## 🤝 Contributing

This is an educational project. Contributions focused on improving security, detection accuracy, and user experience are welcome.

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## ⚠️ Disclaimer

PhishGuard AI is designed for legitimate security testing and awareness training only. Users must:

- Obtain proper authorization before testing
- Use only fictional scenarios for simulations
- Never collect real credentials or sensitive data
- Comply with all applicable laws and regulations

## 🔮 Future Enhancements

- Advanced NLP for email analysis
- Real-time threat intelligence integration
- Multi-language support
- Mobile application
- API for third-party integration
- Advanced reporting and exports

## 📧 Contact

For questions or support, please open an issue in the repository.

---

Built with ❤️ for cybersecurity education
