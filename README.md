# GenVis
## Short for Generative Vision (Genius)
## A Nemotron AI-Powered Product Management Assistant

GenVis is an AI-driven productivity tool built for Product Managers to transform raw ideas into actionable plans, structured requirements, and automated sprint reports fully integrated with Jira and Slack.

Originally built for **PNC Bank’s Product Innovation Challenge** at **HackUTD 2025**, GenVis accelerates the product lifecycle from **Ideation → Planning → Reporting**, while meeting the following two HackUTD challenges:

1. **AI-Powered Productivity Challenge (Product Managers)**  
   - GenVis reimagines AI across the product lifecycle, assisting with ideation, requirements drafting, market research synthesis, prototyping/testing, GTM strategy, and automation of repetitive PM tasks.
   
2. **NVIDIA Nemotron Intelligent Agent Challenge**  
   - GenVis leverages Nemotron for multi-step reasoning, workflow orchestration, API integration, and real-world impact. The system demonstrates AI taking action—pushing tasks to Jira, broadcasting updates to Slack, and automating reporting.

---

## Features

### Product Ideation Assistant
- Generate product ideas, pain points, and customer personas with **Nemotron AI-powered brainstorming**.
- Convert insights directly into structured project requirements.

### Requirements Generator
- Automatically generate **user stories and acceptance criteria**.
- Instantly push tasks to **Jira** for sprint planning.

### Sprint Reporting
- Summarize project progress and generate **stakeholder updates**.
- Automatically broadcast reports to **Slack channels**.

### Multi-Integration Support
- **NVIDIA Nemotron** for AI reasoning and generation.
- **Jira REST API** for backlog sync.
- **Slack Incoming Webhooks** for reports.

### Caching & Timing Mechanism
- API responses and AI outputs are **cached temporarily** to reduce redundant requests and accelerate repeated queries.
- Cached items are timestamped to ensure **freshness** while improving response speed for frequently accessed tasks, improving UX on the frontend.

---

## Tech Stack

| Layer         | Technology                                |
|---------------|-------------------------------------------|
| **Frontend**  | React, JavaScript, HTML/CSS, Lucide Icons |
| **Backend**   | FastAPI (Python)                          |
| **AI Model**  | NVIDIA Nemotron-Nano-9B                   |
| **Integration**| Jira REST API, Slack Incoming Webhooks   |
| **Environment**| Python 3.9+ with `venv`                  |
| **Hosting (planned)** | AWS / Render / GCP                  |

---

## Local Setup

### 1. Clone the repository
Run the following commands in your terminal:

```bash
git clone https://github.com/razeenr05/GenVis.git
cd GenVis
```

### 2. Backend Setup
Set up the backend environment and install dependencies:

```bash
cd backend
python3 -m venv venv
source venv/bin/activate # Mac/Linux
venv\Scripts\activate    # Windows

pip install -r requirements.txt
```

Create `backend/.env` from `.env.example` and configure your keys:

```env
# Nemotron
NVIDIA_API_KEY=your_nvidia_api_key
NVIDIA_MODEL=nvidia/nemotron-nano-9b-v2

# Jira
JIRA_BASE_URL=https://yourworkspace.atlassian.net
JIRA_EMAIL=your_email@example.com
JIRA_API_TOKEN=your_jira_api_token
JIRA_PROJECT_KEY=PROJECT
JIRA_ISSUE_TYPE=Story
JIRA_STORY_POINTS_FIELD=customfield_10020

# Slack
SLACK_WEBHOOK_URL=https://hooks.slack.com/services/XXX/YYY/ZZZ
SLACK_CHANNEL=#product-updates

PORT=8000
HOST=0.0.0.0
```

Run the backend:

```bash
uvicorn mock_api:app --reload
```

Backend runs at `http://127.0.0.1:8000`.

### 3. Frontend Setup
Set up the frontend and start the app:

```bash
cd ../frontend
npm install
npm start
```

Open the app at `http://localhost:3000`.

---

## Project Structure

```
GenVis/
├── backend/
│   ├── agent_backend.py        # Core agent workflows, Nemotron orchestration
│   ├── integrations.py         # Jira + Slack helper functions
│   ├── mock_api.py             # FastAPI application & routes
│   ├── requirements.txt        # Python dependencies
│   └── .env.example            # Sample environment variables
│
├── frontend/
│   ├── public/
│   │   └── index.html          # Frontend HTML entry point
│   ├── src/
│   │   ├── App.js              # Main React application
│   │   ├── App.css             # Global styling
│   │   ├── index.js            # React DOM entry
│   │   ├── index.css           # Reset & global CSS
│   │   └── assets/             # Images, icons, and static assets
│   └── package.json            # Node dependencies & scripts
│
├── .gitignore
└── README.md
```

---

## Roadmap

* Deploy to cloud infrastructure (Render / AWS / GCP)
* Build analytics dashboards for AI insights and sprint metrics
* Enhance Slack bot with **interactive, two-way communication**
* Further fine-tune the AI model for **regulated industries**
* Expand caching and timing mechanism to optimize AI throughput

---

## Summary

GenVis streamlines product ideation, requirement drafting, and executive reporting by connecting AI-generated insights directly to enterprise tools like **Jira** and **Slack**. Initially tailored for PNC’s product workflow, GenVis scales to any organization seeking **AI-assisted product delivery**, demonstrating **multi-step reasoning, workflow orchestration, and integration** as envisioned in HackUTD 2025’s challenges.

---

## Contributors

- **Isaac Pandyan** – Backend & Frontend  
- **Krish Patel** – Backend & Frontend  
- **Razeen Rahman** – Backend & Frontend
