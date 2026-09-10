# Pre-Legal — Justice Department Document & Workflow Automation Platform

[![Next.js](https://img.shields.io/badge/Frontend-Next.js%2014%2B-black?style=flat-square&logo=next.js)](https://nextjs.org/)
[![FastAPI](https://img.shields.io/badge/Backend-FastAPI-009688?style=flat-square&logo=fastapi)](https://fastapi.tiangolo.com/)
[![Python](https://img.shields.io/badge/Python-3.11%2B-3776AB?style=flat-square&logo=python)](https://www.python.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.0%2B-3178C6?style=flat-square&logo=typescript)](https://www.typescriptlang.org/)
[![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)

**Pre-Legal** is a modern, enterprise-ready Legal SaaS application designed to streamline and automate pre-legal workflows, case preparation, and document drafting for justice department requirements, legal practitioners, and citizens.

---

## 📌 Overview & Vision

Pre-legal processes—such as drafting formal notices, petition requests, affidavits, case intake summaries, and compliance filings—often suffer from manual errors, inconsistent phrasing, and excessive turnaround times. 

**Pre-Legal** bridges this gap by providing an intuitive web interface backed by a high-performance backend:
- **Intelligent Template Engine**: Generate legally compliant filings, notices, and formal documentation by filling guided, dynamic forms.
- **Workflow & Case Preparation**: Track matter statuses, pre-filing checklists, and compliance validation before submitting to justice department portals or judicial courts.
- **Standardized Legal Formats**: Export polished, court-compliant documents directly to PDF and DOCX formats.

---

## ✨ Key Features

- 📑 **Template-Based Legal Document Generation**
  - Rich library of judicial and pre-legal templates (Affidavits, Legal Notices, Settlement Requests, Intake Briefs, Power of Attorney drafts).
  - Dynamic questionnaire intake mapping directly into standardized legal clauses.
  
- ⚖️ **Compliance & Validation Engine**
  - Automated field validation to ensure mandatory legal details (jurisdictions, dates, statutory references, party details) are complete before generation.
  
- 📂 **Case & Matter Management**
  - Organize drafts and generated documents by case docket, client, or department reference.
  - Revision history and draft versioning.

- 🖨️ **Multi-Format Export & Digital Signatures**
  - Pixel-perfect PDF rendering and editable `.docx` exports.
  - Watermarking, redaction, and ready-to-sign document delivery.

- 🔒 **Role-Based Access Control (RBAC) & Security**
  - Secure multi-role access (Legal Officer, Clerk, Administrator, Client/Applicant).
  - Audit logging for all generated documents and actions.

---

## 🛠️ Architecture & Tech Stack

### Frontend
- **Framework**: [Next.js](https://nextjs.org/) (App Router, React, Server Components)
- **Language**: [TypeScript](https://www.typescriptlang.org/)
- **Styling**: Tailwind CSS & Modern UI Components
- **State & Data Fetching**: React Query / TanStack Query, Axios / Fetch API
- **Icons & Visuals**: Lucide Icons

### Backend
- **Framework**: [FastAPI](https://fastapi.tiangolo.com/) (Asynchronous Python REST API)
- **Validation & Serialization**: [Pydantic v2](https://docs.pydantic.dev/)
- **Database & ORM**: PostgreSQL / SQLite with [SQLAlchemy](https://www.sqlalchemy.org/) & [Alembic](https://alembic.sqlalchemy.org/)
- **Document Rendering**: Jinja2, `python-docx`, WeasyPrint / ReportLab
- **Authentication**: OAuth2 with JWT (JSON Web Tokens) & Passlib (Bcrypt)

---

## 📁 Repository Structure

```text
pre-legal/
├── frontend/               # Next.js frontend application
│   ├── src/
│   │   ├── app/            # Next.js App Router (pages & layouts)
│   │   ├── components/     # UI & Legal Form Components
│   │   ├── hooks/          # Custom React hooks
│   │   ├── lib/            # API client and utility helpers
│   │   └── types/          # TypeScript interfaces & definitions
│   ├── public/             # Static assets and template previews
│   ├── package.json
│   └── tailwind.config.ts
│
├── backend/                # FastAPI backend application
│   ├── app/
│   │   ├── api/            # API router endpoints (auth, templates, documents, cases)
│   │   ├── core/           # Configuration, security, and database session setup
│   │   ├── models/         # SQLAlchemy database models
│   │   ├── schemas/        # Pydantic request/response models
│   │   ├── services/       # Document rendering & legal template engines
│   │   └── templates/      # Jinja2 / DOCX legal template source files
│   ├── alembic/            # Database migration scripts
│   ├── requirements.txt    # Python package dependencies
│   └── main.py             # FastAPI entry point
│
├── .gitignore              # Project-wide git exclusion rules
├── LICENSE                 # License file
└── README.md               # Project documentation
```

---

## 🚀 Getting Started

### Prerequisites
- **Node.js**: v18.x or v20.x+
- **Python**: v3.10+ (v3.11 recommended)
- **Package Managers**: `npm`, `pnpm`, or `yarn` & `pip`
- **Database** (Optional for local dev): PostgreSQL (SQLite supported out-of-the-box for development)

---

### 1. Backend Setup (FastAPI)

1. Navigate to the backend directory:
   ```bash
   cd backend
   ```

2. Create and activate a Python virtual environment:
   ```bash
   # Windows (PowerShell)
   python -m venv .venv
   .venv\Scripts\Activate.ps1

   # macOS / Linux
   python3 -m venv .venv
   source .venv/bin/activate
   ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Configure environment variables:
   ```bash
   cp .env.example .env
   ```

5. Run the FastAPI development server:
   ```bash
   uvicorn app.main:app --reload --port 8000
   ```
   - API documentation will be available at: [http://localhost:8000/docs](http://localhost:8000/docs) (Swagger UI)

---

### 2. Frontend Setup (Next.js)

1. Open a new terminal and navigate to the frontend directory:
   ```bash
   cd frontend
   ```

2. Install Node dependencies:
   ```bash
   npm install
   # or
   pnpm install
   ```

3. Configure environment variables:
   ```bash
   cp .env.example .env.local
   ```
   Ensure `NEXT_PUBLIC_API_URL` is set to `http://localhost:8000/api/v1`.

4. Start the Next.js development server:
   ```bash
   npm run dev
   ```
   - Web application will be accessible at: [http://localhost:3000](http://localhost:3000)

---

## ⚙️ Environment Configuration

### Backend (`backend/.env`)
```env
PROJECT_NAME="Pre-Legal API"
ENVIRONMENT="development"
SECRET_KEY="your-super-secret-jwt-key"
ALGORITHM="HS256"
ACCESS_TOKEN_EXPIRE_MINUTES=1440

# Database
DATABASE_URL="sqlite:///./pre_legal.db"
# For PostgreSQL:
# DATABASE_URL="postgresql+psycopg2://user:password@localhost:5432/pre_legal_db"

# CORS
BACKEND_CORS_ORIGINS=["http://localhost:3000"]
```

### Frontend (`frontend/.env.local`)
```env
NEXT_PUBLIC_APP_NAME="Pre-Legal"
NEXT_PUBLIC_API_URL="http://localhost:8000/api/v1"
```

---

## 🗺️ Roadmap

- [x] Project architecture & initial repository setup
- [ ] Legal template registry & schema definition
- [ ] Dynamic form builder for questionnaire intake
- [ ] PDF & DOCX generation microservice
- [ ] Role-based user authentication & workspace management
- [ ] Justice department filing integration / export connectors
- [ ] AI-assisted clause suggestion & discrepancy checker

---

## 📄 License

This project is licensed under the terms of the [MIT License](LICENSE).
