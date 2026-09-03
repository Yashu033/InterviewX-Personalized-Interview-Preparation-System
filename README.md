# InterviewX - AI-Driven Personalized Interview Preparation System

[![Frontend](https://img.shields.io/badge/frontend-React%20%2B%20Vite-61DAFB)](https://github.com/Yashu033/InterviewX-Personalized-Interview-Preparation-System/tree/main/frontend)
[![Backend](https://img.shields.io/badge/backend-FastAPI-009688)](https://github.com/Yashu033/InterviewX-Personalized-Interview-Preparation-System/tree/main/backend)

## Overview

InterviewX is an AI-driven personalized interview preparation platform for students preparing for technical and professional interviews. It brings resume analysis, AI-generated interview questions, context-aware follow-up questions, coding practice, performance tracking, and personalized feedback into one application.

The platform combines role-based preparation with AI-assisted analysis. Where external AI services are unavailable, the backend provides local rule-based and NLP fallbacks so the core interview evaluation experience can still be demonstrated.

## 🎯 Problem Statement

Students often face unrealistic practice environments, generic preparation material, difficulty identifying resume weaknesses, limited personalized feedback, and no consistent way to track improvement. Coding practice and interview preparation are also commonly spread across separate tools.

InterviewX addresses these challenges with a single workflow for resume review, technical and behavioral interview practice, coding exercises, readiness metrics, and feedback that is connected to the candidate's selected role and previous responses.

## 🛠️ Key Features

### 🤖 AI-Powered Interview Preparation

- Role-based technical and behavioral interview questions
- Context-aware question selection that avoids recently asked questions
- Personality-based follow-up responses
- Answer evaluation using TF-IDF cosine similarity against an ideal answer
- Session feedback, readiness scoring, and identified weak areas

### 📄 Resume Analysis

- PDF resume upload and text extraction with PyMuPDF
- Technical skill extraction using keyword matching and optional spaCy processing
- ATS-style score, missing keywords, and improvement suggestions
- Optional Groq-powered resume analysis, with a local fallback when no key is configured

### 💻 Coding Practice

- DSA problem bank with difficulty information and test cases
- Monaco code editor in the frontend
- Local Python execution against configured test cases
- Optional Groq-assisted code review

### 📊 Performance Tracking

- Interview readiness and resume scores
- Stored readiness history and previous score values
- Weak-area tracking from interview results
- Analytics and feedback views for reviewing preparation progress

### 🎯 Personalized Preparation

- Preparation based on roles such as SDE, ML, frontend, backend, data science, and product management
- Technical, behavioral, resume, coding, and company-focused workflows
- Structured career roadmaps with week-by-week tasks

### 🎨 Interactive UI

- React and Vite single-page application
- Responsive dashboard and feature pages
- 3D interviewer scene using React Three Fiber, Three.js, and Drei
- Optional browser-based body-language analysis using MediaPipe Face Landmarker

## 🎭 3D AI Interviewer

The interview experience includes an interactive 3D interviewer scene rendered in the browser with React Three Fiber, Three.js, and React Three Drei. It supports the visual interview workflow while text, speech, evaluation, and follow-up logic are handled by the React application and FastAPI backend.

The scene is an original application experience and is not presented as an official or licensed representation of any third-party character.

## 🌟 Real-World Solutions

- **Experience Gap:** Provides repeatable mock interviews with technical and behavioral questions, optional voice interaction, and a 3D interview scene.
- **Generic Feedback:** Scores answers against role-specific ideal answers and returns targeted feedback, weak areas, and follow-up reasoning.
- **Skill Fragmentation:** Combines resume, interview, coding, company preparation, roadmap, analytics, and feedback workflows in one platform.
- **Difficulty Adaptation:** Selects questions by role and uses the candidate's recent context and answer scores to guide follow-up practice.

## ⚙️ Technical Architecture

```text
React / Vite frontend
   ↓
FastAPI REST API
   ↓
AI and NLP processing
   ↓
SQLite database via SQLAlchemy ORM
```

The backend is organized into focused components:

- **Authentication:** Signup, login, password hashing, and JWT token creation
- **Resume processing:** PDF parsing, skill extraction, scoring, and persistence
- **Interview management:** Question generation, answer evaluation, follow-ups, finalization, and reports
- **Coding:** Problem retrieval, Python test execution, persistence, and optional AI review
- **Miscellaneous APIs:** Company preparation and personalized roadmaps
- **AI agents:** Resume, interview, coding, and company/roadmap agent classes

## 🧠 Multi-Agent Architecture

The backend contains specialized agents for separate preparation tasks:

- **Resume Agent:** Extracts PDF text, detects technical skills, and produces resume scoring and keyword feedback.
- **Interview Agent:** Selects role-based questions, evaluates answers with TF-IDF similarity, generates personality-based follow-ups, and summarizes sessions.
- **Coding Agent:** Returns coding problems, runs submitted Python against test cases, and optionally requests a Groq code review.
- **Company and Roadmap Agents:** Provide company preparation content and structured role-based study plans.

The analytics and feedback views consume stored user and interview data from the application database.

## 🧰 Tech Stack

### Frontend

- React
- Vite
- Tailwind CSS
- Axios
- React Router
- Lucide React icons
- Recharts
- Monaco Editor React

### 3D and Visualization

- React Three Fiber
- Three.js
- React Three Drei
- MediaPipe Tasks Vision for browser-based face and body-language analysis

### Backend

- Python
- FastAPI
- Uvicorn
- SQLAlchemy
- Python Multipart
- PyMuPDF
- spaCy
- Celery and Redis dependencies for background-task integration

### Database

- SQLite by default
- SQLAlchemy ORM
- JSON fields for user score history and weak areas

### AI and NLP

- Groq Chat Completions API using `llama-3.3-70b-versatile` when `GROQ_API_KEY` is configured
- scikit-learn TF-IDF and cosine similarity for local answer evaluation
- spaCy for optional NLP processing
- Local rule-based fallbacks when external AI credentials are unavailable

## 📁 Project Structure

```text
InterviewX-Personalized-Interview-Preparation-System/
├── backend/
│   ├── agents/
│   ├── models/
│   ├── routes/
│   ├── schemas/
│   ├── uploads/
│   ├── utils/
│   ├── database.py
│   ├── main.py
│   ├── migrate_db.py
│   ├── requirements.txt
│   └── run_backend.bat
├── frontend/
│   ├── public/
│   ├── src/
│   ├── package.json
│   ├── package-lock.json
│   ├── vite.config.js
│   └── index.html
├── README.md
└── .gitignore
```

## 🔌 API Documentation

The backend is built with FastAPI. Swagger provides interactive API documentation for testing the available REST endpoints:

https://interviewx-backend-yah00.onrender.com/docs

## 🌐 Live Demo

### Frontend

https://interviewx-personalized-interview-8ykt.onrender.com

This is the deployed InterviewX web application.

### Backend API

https://interviewx-backend-yah00.onrender.com

This is the deployed FastAPI backend.

### API Documentation

https://interviewx-backend-yah00.onrender.com/docs

This is the interactive Swagger API documentation.

## 🚀 Getting Started

### Prerequisites

- Python 3.10 or newer
- Node.js 18 or newer
- npm
- Git
- A Groq API key for optional external AI feedback and resume analysis

### Clone the Repository

```bash
git clone https://github.com/Yashu033/InterviewX-Personalized-Interview-Preparation-System.git
cd InterviewX-Personalized-Interview-Preparation-System
```

### Backend Setup

```bash
cd backend
python -m venv venv
```

Activate the environment:

```bash
# Windows PowerShell
venv\Scripts\Activate.ps1

# macOS or Linux
source venv/bin/activate
```

Install dependencies and start FastAPI:

```bash
python -m pip install -r requirements.txt
python -m uvicorn main:app --reload
```

The local backend runs at http://127.0.0.1:8000. Swagger is available at http://127.0.0.1:8000/docs.

For external AI features, create `backend/.env` and add:

```env
GROQ_API_KEY=your_groq_api_key
```

The default database is SQLite at `backend/interviewx.db`. A different database URL can be supplied with `DATABASE_URL`.

### Frontend Setup

Open a second terminal at the project root:

```bash
cd frontend
npm install
npm run dev
```

The local frontend runs at the Vite URL shown in the terminal, normally http://localhost:5173.

## ☁️ Deployment

The frontend is deployed as a Render Static Site and the backend is deployed as a Render web service.

### Frontend Render Configuration

- **Root Directory:** `frontend`
- **Build Command:** `npm install && npm run build`
- **Publish Directory:** `dist`

The frontend source is configured to call the deployed backend at `https://interviewx-backend-yah00.onrender.com`.

### Backend Render Configuration

Use `backend` as the service root directory and start FastAPI with a Render-provided port:

```bash
uvicorn main:app --host 0.0.0.0 --port $PORT
```

## 👩‍💻 Author

**Thippareddy Yashaswini**

GitHub: https://github.com/Yashu033
