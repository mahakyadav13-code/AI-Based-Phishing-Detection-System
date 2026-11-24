# PhishGuard AI – Master Development Prompt

> **Project:** PhishGuard AI – Intelligent Phishing Simulation and Detection Platform  
> **Category:** Cybersecurity, AI/ML, Full-Stack Development  
> **Purpose:** Cybersecurity internship project and professional GitHub portfolio  
> **Automation constraint:** Build the project using conventional Python/application code only. **Do not use n8n or any workflow automation platform.**

---

# 1. Role

Act as a Senior Cybersecurity Engineer, Machine Learning Engineer, Full-Stack Developer, Software Architect, and UI/UX Designer.

Design, implement, run, test, debug, and document a complete application named **PhishGuard AI**.

Do not merely generate code. Execute the application and verify it after every development phase. Do not claim that a feature works unless it has actually been run and tested.

# 2. Project Objective

Build a web-based platform that:

- Analyzes submitted email content for phishing indicators.
- Analyzes URLs for suspicious characteristics.
- Uses machine learning and explainable rule-based checks to classify potential threats.
- Provides safe phishing-awareness simulations using fictional content and mock pages.
- Records scan history and security events.
- Displays results in a polished security dashboard.
- Generates downloadable analysis reports.

The platform is an educational detection and awareness tool. It must not be used to send deceptive messages to real people, harvest credentials, or attack systems.

# 3. Technology Stack

Use compatible, maintained versions and record the versions selected.

## Frontend
- React
- Vite
- Tailwind CSS
- JavaScript or TypeScript
- Lucide icons
- Recharts for data visualization

## Backend
- Python 3.11+
- Flask
- Flask-SQLAlchemy
- Flask-Migrate
- Flask-WTF or equivalent CSRF protection
- Flask-Limiter

## Machine Learning and analysis
- Scikit-learn
- pandas
- NumPy
- joblib
- Python standard-library email parsing utilities
- Carefully selected URL parsing and feature extraction utilities

## Database
- MySQL 8.0 preferred
- SQLite as a local development fallback

## Testing and quality
- Pytest
- pytest-cov
- Bandit
- Ruff
- Dependency vulnerability scanning
- OWASP ZAP for authorized local testing, if available

## Development and deployment
- Git
- Docker Compose is optional for local MySQL setup
- Render or another suitable hosting provider may be considered after local validation

**Do not use n8n, Zapier, Make, or another workflow automation platform.** Implement application behavior directly in Python and the frontend.

Do not add paid APIs or external services unless explicitly approved. The core project must work locally without API keys.

# 4. Premium UI/UX Requirements

UI quality is a top priority. Create a premium, enterprise-style cybersecurity SaaS interface—not a generic student project dashboard.

## Visual direction
- Deep navy and charcoal backgrounds
- Restrained cyan, blue, and violet accents
- Strong visual hierarchy
- Professional typography
- Consistent spacing and alignment
- Refined borders, shadows, and card surfaces
- Subtle transitions and micro-interactions
- Responsive desktop, tablet, and mobile layouts
- Lucide icons instead of emoji navigation
- Accessible contrast, labels, and focus states

Avoid excessive gradients, clutter, unnecessary animation, oversized cards, inconsistent spacing, and default browser styling.

## Required pages

### A. Landing page
- PhishGuard AI branding
- Clear product explanation
- Hero section with primary actions
- Feature overview
- Detection workflow explanation
- Responsible-use statement
- Login and registration links if authentication is implemented
- Professional footer

### B. Authentication pages
- Login and registration
- Password visibility toggle
- Client- and server-side validation
- Clear success and error messages
- Secure session handling

### C. Main dashboard
Show:
- Total email scans
- Total URL scans
- Phishing detections
- Potentially suspicious detections
- Safe/low-risk detections
- Recent scan activity
- Detection trend chart
- Risk distribution chart
- Recent security events

Use real database-backed values. Do not hardcode dashboard metrics.

### D. Email analysis page
- Paste email text
- Upload supported `.eml` files
- Validate file type and size
- Display extracted sender, subject, links, and relevant headers when available
- Show classification, risk level, confidence, and reasons
- Clearly identify missing data or unsupported headers

Do not execute attachments, macros, embedded scripts, or remote content.

### E. URL scanner page
- URL input with validation
- Display extracted URL features
- Show classification and risk level
- Explain the indicators that influenced the result
- Provide safe handling guidance

Do not automatically visit, crawl, or execute submitted URLs. Do not fetch arbitrary URLs from the backend. This prevents the scanner from becoming an SSRF or malware-execution service.

### F. Scan history
- Search and filters
- Scan type
- Classification
- Risk level
- Timestamp
- Detailed result view
- Pagination

### G. Awareness simulation
- Use fictional sample phishing scenarios
- Provide a mock training page hosted locally
- Record only safe interaction events, such as opening a training scenario or clicking a clearly controlled simulation link
- Never collect or store real passwords
- Do not impersonate real organizations or send campaigns to real users
- Show a learning explanation after the exercise

### H. Reports
- Summary of email and URL scans
- Detection statistics
- Model evaluation metrics
- Exportable CSV or PDF reports where practical
- Report generation timestamp and limitations

## UI validation
After each page is implemented:

1. Run the frontend and backend.
2. Inspect the actual rendered page in a browser if browser tools are available.
3. Check desktop and mobile layouts.
4. Test buttons, forms, links, navigation, loading states, empty states, and error states.
5. Check browser console and server logs.
6. Fix visual and functional defects.
7. Repeat verification.

If browser inspection is unavailable, state that clearly and provide reproducible manual verification steps. Never claim visual inspection that was not performed.

# 5. Core Functional Modules

## Module 1: Email phishing analysis

Accept pasted email text and supported `.eml` files.

Extract, when available:
- Sender and reply-to information
- Subject
- Message body
- URLs in the message
- Selected authentication headers such as SPF, DKIM, and DMARC results, when present

Analyze indicators such as:
- Urgent or coercive language
- Requests for credentials or sensitive information
- Suspicious sender/reply-to mismatch
- URL and display-text mismatch
- Unusual link patterns
- Suspicious attachment references
- Authentication-header failures, if reliable header data is present

Do not infer that an email is safe solely because SPF, DKIM, or DMARC passes. Do not claim to verify headers that are absent or untrusted.

## Module 2: URL analysis

Parse URLs safely without opening them.

Extract relevant features such as:
- URL length
- Hostname length
- Number of subdomains
- IP-address hostname indicator
- HTTPS scheme indicator
- Presence of unusual ports
- Suspicious tokens
- Encoded characters
- Number of query parameters
- Punycode indicator
- URL shortener indicator, using a documented local list if included

Treat HTTPS as one signal only; it does not prove a site is legitimate.

Do not automatically resolve, visit, crawl, or download content from submitted URLs.

## Module 3: Machine learning detection engine

Build separate, appropriately evaluated classifiers for email text and URL features where the available datasets support this.

Candidate algorithms:
- Logistic Regression
- Multinomial Naive Bayes for suitable text features
- Random Forest
- Decision Tree
- Linear SVM, where probability calibration is handled correctly

Use suitable feature engineering:
- TF-IDF for email text
- Numeric and categorical URL features
- Proper preprocessing pipelines

Dataset requirements:
- Use reputable, legally accessible datasets.
- Document dataset source, license, date, label definitions, and limitations.
- Do not invent training data or claim a dataset was used if it was not.
- Keep training, validation, and test sets separate.
- Avoid data leakage and duplicate records across splits.
- Use stratified splitting where appropriate.
- Address class imbalance responsibly.

Evaluate with:
- Precision
- Recall
- F1-score
- Confusion matrix
- ROC-AUC or PR-AUC when appropriate
- False-positive and false-negative analysis

Prioritize phishing recall while clearly reporting false-positive trade-offs. Do not present accuracy alone as proof of model quality.

Persist trained pipelines with joblib and load them safely from trusted project artifacts. Never load untrusted pickle/joblib files.

If no suitable dataset is available, implement the analysis pipeline with clearly labeled rule-based results and do not pretend a trained model exists.

## Module 4: Explainable risk assessment

Return:
- Classification: phishing, suspicious, or likely legitimate
- Risk level: high, medium, or low
- Model score or confidence, clearly distinguished from calibrated probability
- Key indicators
- Recommended next steps
- Limitations of the analysis

Do not present model output as certainty. Use cautious wording such as “potential phishing” or “no strong phishing indicators detected.”

## Module 5: Safe awareness simulation

Build controlled, local-only awareness exercises:
- Fictional training scenarios
- Mock landing pages
- Safe click tracking
- Learning feedback
- Aggregate training statistics

Do not collect credentials, session cookies, personal secrets, or sensitive information. Do not send deceptive emails or run campaigns against real users. Keep simulation data synthetic or consent-based.

# 6. Backend and API Requirements

Use a modular Flask application with an application factory and Blueprints.

Suggested API endpoints:
- `GET /api/health`
- `POST /api/analyze/email`
- `POST /api/analyze/url`
- `GET /api/scans`
- `GET /api/scans/<id>`
- `GET /api/dashboard/summary`
- `GET /api/reports/summary`
- `POST /api/simulation/start`
- `POST /api/simulation/event`

Define request and response schemas. Validate all input on the server. Apply authentication and authorization where user-specific data is stored.

Use consistent HTTP status codes and safe error messages. Do not expose stack traces, secrets, internal file paths, or sensitive data in API responses.

# 7. Database Design

Create suitable models, such as:

- Users (if authentication is included)
- EmailScans
- URLScans
- ExtractedIndicators
- ModelVersions
- SimulationSessions
- SimulationEvents
- AuditLogs

Use:
- Primary and foreign keys
- Appropriate indexes
- Unique constraints where needed
- Timestamps
- Data retention rules
- Pagination for history queries

Do not store passwords in plaintext. Avoid storing full email bodies or sensitive personal data unless essential. Prefer storing minimized analysis results and provide a documented retention policy.

# 8. Security Requirements

Apply relevant OWASP guidance and secure coding practices:

- Authentication and authorization
- Password hashing with Argon2id or bcrypt if passwords are stored
- CSRF protection
- XSS prevention and output encoding
- SQL injection prevention through ORM/parameterized queries
- Secure cookies and session configuration
- Rate limiting
- Input validation
- File upload size/type restrictions
- Safe error handling
- Security headers
- Secrets in environment variables
- Dependency security checks
- Audit logging without secrets or credentials

Protect against SSRF by **not fetching submitted URLs**. If a future feature requires network access, design a separate isolated and allowlisted service with explicit safeguards.

Document which controls are implemented, partially implemented, not applicable, or not yet verified. Do not claim complete OWASP compliance without evidence.

# 9. Project Structure

Use a maintainable structure similar to:

```text
PhishGuard-AI/
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── layouts/
│   │   ├── services/
│   │   ├── hooks/
│   │   └── assets/
│   ├── package.json
│   └── vite.config.js
│
├── backend/
│   ├── app/
│   │   ├── __init__.py
│   │   ├── config.py
│   │   ├── models/
│   │   ├── routes/
│   │   ├── services/
│   │   ├── detection/
│   │   ├── security/
│   │   └── utils/
│   ├── tests/
│   ├── migrations/
│   ├── requirements.txt
│   └── run.py
│
├── ml/
│   ├── datasets/
│   ├── notebooks/
│   ├── training/
│   ├── evaluation/
│   └── models/
│
├── docs/
│   ├── architecture.md
│   ├── database-schema.md
│   ├── model-card.md
│   ├── security-report.md
│   └── testing-report.md
│
├── .env.example
├── .gitignore
├── README.md
└── LICENSE
```

Adapt the structure if there is a strong technical reason, but keep frontend, backend, ML, tests, and documentation logically separated.

# 10. Mandatory Phase-by-Phase Development Workflow

**This requirement is mandatory for every phase.**

For each phase, follow this exact cycle:

### Step 1 – Plan
Explain the objective, design, dependencies, and acceptance criteria.

### Step 2 – Implement
Create or modify complete working files. Avoid incomplete snippets when implementation is expected.

### Step 3 – Install
Install dependencies and verify compatible versions.

### Step 4 – Run
Start the relevant services. Keep the application runnable at the end of the phase.

### Step 5 – Test
Run automated tests and relevant manual checks.

### Step 6 – Verify
Verify API responses, database operations, model behavior, and rendered UI as applicable.

### Step 7 – Debug
If something fails:
- Identify the root cause.
- Fix the issue.
- Restart the affected service.
- Rerun the failed test.
- Confirm the result.

### Step 8 – Report
Provide:
- Files created or changed
- Commands executed
- Services started
- Tests performed
- Actual test results
- Screenshots or output evidence where available
- Remaining issues and limitations

### Step 9 – Approval gate
Do not proceed until the current phase meets its acceptance criteria.

## Mandatory rules
- Never skip running the application.
- Never assume generated code works.
- Never mark a phase complete without running its relevant checks.
- Never hide errors or weaken security controls to make tests pass.
- Do not claim a test, scan, or browser inspection was performed unless it was.
- If an external dependency or credential is unavailable, state the limitation and provide reproducible instructions.
- Keep the application runnable after every phase.

# 11. Development Phases

## Phase 1 – Requirements, Architecture, and Environment
- Inspect the development environment and existing files.
- Propose architecture and data flow.
- Create project structure.
- Set up Python virtual environment and frontend tooling.
- Install dependencies.
- Configure `.env.example`.
- Build a minimal frontend and backend health endpoint.
- Run both services.
- Verify the landing page and `/api/health`.

**Acceptance criteria:** Frontend and backend start successfully and communicate where applicable.

## Phase 2 – Backend and Database
- Configure SQLite initially or MySQL if available.
- Create database models and migrations.
- Implement API Blueprints.
- Add validation and error handling.
- Test database connectivity and CRUD operations.

**Acceptance criteria:** Database operations work and automated backend tests pass.

## Phase 3 – Email Phishing Analysis
- Implement `.eml` parsing and pasted-email analysis.
- Extract relevant headers, sender, subject, body, and URLs.
- Add explainable rule-based indicators.
- Implement the email analysis endpoint.
- Create unit and integration tests.
- Run and verify sample cases.

**Acceptance criteria:** Safe sample emails can be analyzed and results explain their indicators.

## Phase 4 – URL Detection
- Implement URL parsing and feature extraction without visiting URLs.
- Create rule-based risk indicators.
- Add the URL analysis endpoint.
- Test benign, suspicious, malformed, and edge-case URLs.
- Verify no outbound requests are made to submitted URLs.

**Acceptance criteria:** URL analysis works locally and does not fetch submitted destinations.

## Phase 5 – Machine Learning
- Identify and document suitable datasets.
- Build preprocessing and feature pipelines.
- Split data without leakage.
- Train candidate models.
- Evaluate precision, recall, F1, confusion matrix, and suitable AUC metrics.
- Compare models and document the selection.
- Persist and load the trusted model artifact.
- Integrate inference into the backend.
- Test inference and failure handling.

**Acceptance criteria:** Reproducible training and evaluation results exist. If no suitable dataset is available, clearly label the ML phase as pending and do not fabricate results.

## Phase 6 – Premium Frontend
- Build the landing page.
- Build email analysis and URL scanner pages.
- Build dashboard and charts.
- Build scan history and detailed result pages.
- Build safe awareness simulation pages.
- Build reports page.
- Connect all pages to real backend APIs.
- Test responsive layouts and all interactions.

**Acceptance criteria:** Main user journeys work end-to-end and the UI has been inspected at available viewport sizes.

## Phase 7 – Integration and Security Testing
- Test frontend/backend integration.
- Run full automated test suite.
- Test access control and validation.
- Run Bandit and dependency checks.
- Perform authorized local security testing.
- Fix findings and document unresolved risks.

**Acceptance criteria:** No unresolved critical/high-severity issues without documented mitigation and explicit disclosure.

## Phase 8 – Documentation and GitHub Publication
- Create professional README.
- Add setup and execution instructions.
- Add architecture and database diagrams.
- Add screenshots.
- Add model card and evaluation results.
- Add security and testing reports.
- Review `.gitignore`.
- Check for secrets and sensitive data before publication.

**Acceptance criteria:** A new developer can reproduce the project from the README and repository without relying on undocumented local files.

# 12. Required Documentation

Create:

```text
README.md
.env.example
.gitignore
LICENSE
SECURITY.md
backend/requirements.txt
docs/architecture.md
docs/database-schema.md
docs/model-card.md
docs/security-report.md
docs/testing-report.md
```

README must include:
- Project overview
- Features
- Technology stack
- Architecture
- Prerequisites
- Installation
- Environment configuration
- How to run frontend and backend
- How to run tests
- Dataset sources and licenses
- Model evaluation results
- Screenshots
- API documentation
- Security controls
- Known limitations
- Future improvements

Never commit real credentials, `.env` files, private datasets, personal email content, database files containing personal information, or model artifacts whose license does not permit redistribution.

# 13. Final Deliverables

The finished project must contain:

1. Working React frontend
2. Working Flask backend
3. Email phishing analysis
4. URL risk analysis
5. Machine learning pipeline, if supported by suitable data
6. Explainable detection results
7. Safe phishing-awareness simulation
8. Persistent scan history
9. Security and model evaluation reports
10. Automated tests
11. Professional documentation
12. GitHub-ready source code

# 14. Start Instructions

**Begin with Phase 1 ONLY.**

First inspect the existing development environment and available files. Do not overwrite existing work without inspecting it.

Then:

1. Explain the proposed architecture.
2. Show the folder structure.
3. Explain frontend/backend communication.
4. Initialize the project.
5. Install dependencies.
6. Start the frontend and backend.
7. Verify the landing page and health endpoint.
8. Run relevant checks.
9. Report files, commands, actual results, and limitations.

Do not start Phase 2 until Phase 1 has been successfully executed and verified.

**Final instruction:** Act as an engineering partner, not merely a code generator. Prioritize security, real functionality, premium UI quality, reproducibility, and verified execution over speed.
