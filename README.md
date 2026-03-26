# Career Launch Pad – Placement Prep Tracker

## 📌 Hackathon Submission Details

| Field                | Information                                      |
|----------------------|--------------------------------------------------|
| **College**          | **Mahendra Engineering College**                 |
| **Department**       | **Cyber Security**                               |
| **Team Name**        | **Cyber Squirrels**                              |
| **Team Leader**      | **R. Dinesh**                                    |
| **Team Members**     | P.S. Kanishka, M. Manoj, M. Monisha, Poovendan, I. Vinitha |
| **Date**             | 27th March 2026                                  |
| **Problem Statement**| **Placement Prep Tracker – Track coding, aptitude, HR process-4** |

---

## 📖 Introduction

**Career Launch Pad (CLP)** is an intelligent, all‑in‑one platform that helps engineering students prepare for campus placements by tracking and enhancing their performance in **coding**, **aptitude**, and **HR skills**. Powered by local AI (Ollama with `llama3.2:3b`), the platform delivers personalised recommendations, real‑time feedback, and psychological nudges to keep users motivated. It gamifies the preparation journey with streaks, leaderboards, goal contracts, and simulated interviews – making the process engaging and effective.

---

## 🎯 Problem Statement

**Placement Prep Tracker – Track coding, aptitude, HR process-4**

Students often struggle to:
- Track their progress across multiple domains (coding, aptitude, HR).
- Receive personalised, actionable feedback.
- Stay motivated over long preparation periods.
- Identify their weaknesses and get targeted practice.

Career Launch Pad addresses these challenges by:
- Consolidating all three preparation areas into a single dashboard.
- Using AI to generate customised questions, analyse answers, and provide improvement suggestions.
- Applying behavioural psychology (loss aversion, social proof, fear of missing out) to maintain engagement.
- Offering predictive insights that show the impact of daily effort on future placement outcomes.

---

## ✨ Key Features

### 🔐 Authentication & User Management
- Secure JWT‑based login/registration.
- User profiles store solved problems, mock scores, ATS scores, and streak information.
- Data persisted locally via JSON files – no external database required.

### 💻 Coding Arena
- A curated bank of problems (easy, medium, hard) with tags and difficulty indicators.
- **AI‑recommended problems** – the model suggests the next best problem based on solved history.
- **Problem of the Day** – a random unsolved problem with a countdown timer to encourage daily practice.
- **Leaderboard** – ranks users by problems solved and displays streaks.
- **Battle Mode** – challenge peers and compete in timed sessions.

### 🧮 Aptitude Lab
- AI‑generated multiple‑choice questions tailored to the user’s weakest topics.
- Topic‑wise performance breakdown with visual progress bars.
- Trending topics – shows what other students are solving right now (AI‑generated).
- Mock tests with instant scoring and feedback.

### 🎙️ HR Mirror
- Practice HR interview questions with AI‑powered answer analysis.
- The AI evaluates answers using the STAR method (Situation, Task, Action, Result).
- Provides a score (1‑10) and specific suggestions for improvement.
- Success stories from placed students to inspire.

### 🤖 AI Coach
- A blunt, data‑aware mentor that knows your solved count, readiness, and streak.
- Generates a **daily optimized study plan** based on your weaknesses.
- **Future self simulation** – compares the likely outcome if you push hard vs. if you slack.
- Chat interface – ask any placement‑related question and receive actionable advice.

### 🎥 Interview Simulation
- Live webcam feed with **eye‑tracking and head pose detection** (using MediaPipe).
- Anti‑cheat flags – looking away triggers a distraction flag.
- Multi‑phase interview: MCQ, coding, technical, HR.
- Final score combines attention and answer quality.
- Saves the mock score to your profile.

### 📄 Resume ATS Checker
- Paste your resume text, and the AI returns an ATS compatibility score (0–100).
- Detailed feedback on keywords, formatting, action verbs, and completeness.
- Specific issues and suggestions to improve your resume’s ATS friendliness.

### 🏆 Impact Records
- Showcases real placement success stories (masked names) with company, package, and stats.
- Filter by company (Google, Microsoft, Amazon, etc.).
- **What If Simulator** – slider to see how solving extra problems per day affects your predicted placement package (AI‑generated).

### 🧠 Mind Games
- **Do Nothing** – sit idle for 5 minutes while the app shows harsh facts to push you to act.
- **The Mirror** – type your biggest fear; the AI converts it into motivational fuel.
- **Mystery Box** – unlocks after solving a set number of problems, revealing a secret resource.
- **Rival Generator** – AI creates a virtual competitor with slightly better stats to spur you on.

### 📜 Goal Contracts
- Set binding goals with a target date and progress tracking.
- Penalty box for failing goals (e.g., restricted access to certain features).
- Goals are stored on the backend and persist across sessions.

### ⚙️ Settings & Customisation
- Light/dark theme toggle.
- Ollama connection URL configuration.
- Logout option.

---

## 🛠️ Technology Stack

| Layer        | Technologies Used                                      |
|--------------|--------------------------------------------------------|
| **Frontend** | HTML5, CSS3, JavaScript (ES6), Chart.js                |
| **Backend**  | Python 3.8+, FastAPI, JWT authentication               |
| **AI**       | Ollama (llama3.2:3b), MediaPipe for face detection     |
| **Storage**  | JSON files (atomic writes)                             |
| **Server**   | Uvicorn (backend), Python http.server (frontend)       |

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                         Frontend (Browser)                      │
│  - Single‑page application (SPA)                               │
│  - API calls to backend (REST)                                 │
│  - Ollama calls for AI features                                │
└───────────────────────────────┬─────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────┐
│                     Backend (FastAPI - port 8000)               │
│  - Authentication (JWT)                                        │
│  - JSON file storage (users, goals, placements, etc.)          │
│  - Endpoints for leaderboard, stats, problem solving           │
└───────────────────────────────┬─────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────┐
│                Local AI Service (Ollama - port 11434)           │
│  - Model: llama3.2:3b                                          │
│  - Used for all AI generation (coach, resume, etc.)            │
└─────────────────────────────────────────────────────────────────┘
```

---

## 🚀 Getting Started

### Prerequisites
- Python 3.8+ installed.
- Ollama installed and the model `llama3.2:3b` pulled:
  ```bash
  ollama pull llama3.2:3b
  ```
- Git (optional).

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/career-launch-pad.git
   cd career-launch-pad
   ```

2. **Set up the backend**
   ```bash
   cd backend
   pip install -r requirements.txt
   uvicorn main:app --reload --port 8000
   ```
   The backend will automatically create a `data/` folder with initial JSON files and a test user (`test` / `test123`).

3. **Serve the frontend**
   Open a new terminal in the project root and run:
   ```bash
   python -m http.server 3000
   ```
   (or use any static server)

4. **Access the app**
   Open your browser and go to `http://localhost:3000`.

### First Login
- Use the test account:
  - Username: `test`
  - Password: `test123`
- Or register a new account.
- **Demo user** (for testing all features):
  - Username: `demo`
  - Password: `demo123`

---

## 🧪 How to Use

### Dashboard
- View your readiness score, problems solved, mock average, and streak.
- Urgent alerts (e.g., “Streak dies in 4h”) keep you focused.
- Activity chart shows weekly progress.
- Peer comparison and mentor notes provide social proof and authority.

### Coding Arena
- Browse problems; solved ones are marked.
- Click “Solve” to mark a problem as solved – your streak and solved count update automatically.
- The AI‑recommended problem appears as “Problem of the Day”.
- Leaderboard shows your rank and the top performers.

### Aptitude Lab
- Take a mock test – questions are generated on the fly by the AI.
- After answering, you get immediate feedback and a score.
- Topic weaknesses are visualised; focus on the weakest areas.

### HR Mirror
- Choose a question, type your answer, and click “Analyze with AI”.
- The AI evaluates your answer and gives a score with specific suggestions.
- Use the STAR method to improve your responses.

### Resume ATS
- Paste your resume text into the text area.
- Click “Analyze Resume” – the AI returns an ATS score and detailed feedback.
- Follow the suggestions to improve your resume.

### AI Coach
- Type any question in the chat input.
- The AI replies with personalised, blunt advice based on your stats.
- The daily plan shows the most important tasks for you.

### Interview Simulation
- Click “Start Simulation” to activate the webcam.
- Answer questions in the different tabs; your attention is tracked.
- Flags appear if you look away.
- End the session to save your score.

### Goals & Mind Games
- Sign a goal contract with a target date.
- Track your progress; failing goals may restrict features.
- Use mind games like “Do Nothing” to build discipline.

---

## 🤖 AI Integration Details

All AI features are powered by **Ollama** with the `llama3.2:3b` model. The frontend makes direct calls to the Ollama API (`http://localhost:11434/api/chat`), using carefully crafted prompts to obtain structured JSON responses for:

- **Problem recommendations** – suggests the next problem based on solved list.
- **Aptitude question generation** – creates questions tailored to weak topics.
- **Resume analysis** – returns ATS score, keywords, issues, strengths.
- **HR answer analysis** – evaluates STAR structure, confidence, and gives a score.
- **Daily study plan** – prioritises tasks based on user stats.
- **Future self predictions** – estimates placement package based on effort.
- **Rival generation** – creates a virtual competitor with realistic stats.
- **Fear conversion** – turns user fears into motivational text.

If Ollama is not running or the model is unavailable, the application falls back to sensible static data, ensuring the platform remains usable.

---

## 📁 Project Structure

```
career-launch-pad/
├── frontend/
│   ├── index.html          # Main application
│   ├── css/
│   │   └── style.css       # Styling (light/dark theme)
│   ├── js/
│   │   ├── main.js         # Core logic (UI, events, AI integration)
│   │   └── api.js          # API client for backend communication
│   └── assets/             # (optional) images, etc.
├── backend/
│   ├── main.py             # FastAPI server with endpoints
│   ├── auth.py             # JWT and password handling
│   ├── seed_data.py        # Initial data seeding
│   ├── face_detector.py    # MediaPipe face mesh analysis
│   ├── requirements.txt    # Python dependencies
│   └── data/               # JSON storage (created automatically)
│       ├── users.json
│       ├── placements.json
│       ├── problems.json
│       └── goals.json
└── README.md               # This file
```

---

## 🔧 Batch File for Easy Launch

Create a file named `start_clp.bat` in the project root with the following content:

```batch
@echo off
echo Starting Career Launch Pad...

:: Start Frontend Server (Python HTTP Server on port 3000)
start "CLP Frontend" cmd /k "echo Starting frontend on http://localhost:3000 & python -m http.server 3000"

:: Wait a moment to ensure frontend starts (optional)
timeout /t 2 /nobreak >nul

:: Start Backend Server (Uvicorn on port 8000)
cd backend
start "CLP Backend" cmd /k "echo Starting backend on http://localhost:8000 & uvicorn main:app --reload --port 8000"

echo Both servers started. Access the application at http://localhost:3000
echo Close each terminal window to stop the respective server.
pause
```

Double‑click the batch file to start both servers simultaneously.

---

## 📝 Sample Test Data

### Resume Text (for ATS testing)

```
R. Dinesh
Email: dinesh@example.com | Phone: +91 9876543210
GitHub: github.com/dinesh | LinkedIn: linkedin.com/in/dinesh

EDUCATION
B.Tech in Computer Science and Engineering (Cyber Security)
Mahendra Engineering College, Tamil Nadu
CGPA: 8.7 | Expected Graduation: 2026

TECHNICAL SKILLS
Programming Languages: Python, Java, C++, JavaScript
Web Technologies: React, Node.js, Express, HTML/CSS
Databases: MongoDB, MySQL
Tools: Git, Docker, Postman

EXPERIENCE
Cyber Security Intern | TechSecure Pvt Ltd | May 2025 – July 2025
• Conducted vulnerability assessments for 10+ web applications using OWASP tools.
• Developed an automated script to detect SQL injection flaws, reducing manual testing time by 40%.
• Presented security findings to the development team and assisted in remediation.

PROJECTS
1. AI‑Powered Placement Tracker (Career Launch Pad)
   • Built a full‑stack web application with FastAPI backend and AI (Ollama) integration.
   • Implemented JWT authentication, real‑time leaderboards, and eye‑tracking interview simulation.
   • Technologies: Python, JavaScript, MediaPipe, HTML/CSS.

2. Secure File Encryption Tool
   • Developed a desktop application using Python and cryptography library.
   • Implemented AES‑256 encryption with key derivation (PBKDF2).

CERTIFICATIONS
• Certified Ethical Hacker (CEH) v12 – EC‑Council
• Google IT Automation with Python – Coursera

ACHIEVEMENTS
• Winner of Intra‑College Hackathon 2025
• Solved 250+ problems on LeetCode (Rating: 1650)
```

### Aptitude Questions (for manual testing)

1. A train 150 m long passes a pole in 6 seconds. What is its speed in km/h?  
   **Answer:** 90 km/h  
2. The average of 20 numbers is 30. If two numbers 25 and 35 are removed, what is the new average?  
   **Answer:** 30  
3. A man buys a cycle for ₹1400 and sells it at a loss of 15%. What is the selling price?  
   **Answer:** ₹1190  
4. If 5 men can complete a work in 12 days, how many days will 6 men take to complete the same work?  
   **Answer:** 10 days  
5. A shopkeeper marks his goods 20% above cost price and gives a discount of 10%. Find his profit percent.  
   **Answer:** 8%


## 🎯 Conclusion

Career Launch Pad successfully tackles the **Placement Prep Tracker** problem statement by integrating coding, aptitude, and HR preparation into a single, AI‑driven platform. It combines real‑time feedback, gamification, and psychological principles to keep students engaged and on track. The project demonstrates how modern AI (Ollama) can be used to personalise learning and simulate real‑world interview scenarios, giving students a competitive edge in campus placements.

---

**Happy Coding! 🚀**
