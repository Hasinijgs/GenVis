# GenVis 
## Short for Generative Vision (Genius)
## A Nemotron AI Powered Product Management Assistant

GenVis is an AI driven productivity tool built for product managers to transform raw ideas into actionable plans, structured requirements, and automated sprint reports to be fully integrated with Jira and Slack.

Originally built for PNC Bank’s Product Innovation Challenge at HackUTD 2025, GenVis accelerates the product lifecycle from ideation → planning → reporting.

## Features

### Product Ideation Assistant
- Generate product ideas, pain points, and customer personas with Nemotron AI powered brainstorming.
- Convert insights directly into project requirements.

### Requirements Generator
- Create user stories and acceptance criteria automatically.
- Instantly push tasks to Jira as issues for sprint planning.

### Sprint Reporting
- Summarize progress and generate stakeholder updates.
- Automatically broadcast reports to Slack channels.

### Multi-Integration Support
- NVIDIA Nemotron for reasoning and generation.
- Jira REST API for backlog sync.
- Slack Incoming Webhooks for broadcasts.

## Tech Stack

| Layer      | Technology                                |
|------------|-------------------------------------------|
| Frontend   | React, JavaScript, HTML/CSS, Lucide Icons |
| Backend    | FastAPI (Python)                          |
| AI Model   | NVIDIA Nemotron-Nano-9B                   |
| Integration| Jira REST API, Slack Incoming Webhooks    |
| Environment| Python 3.9+ with `venv`                   |
| Hosting (planned) | AWS / Render / GCP                 |

## Local Setup

### 1. Clone the repository
```bash
git clone https://github.com/razeenr05/GenVis.git
cd GenVis
```

### 2. Backend setup
```bash
cd backend
python3 -m venv venv
source venv/bin/activate # Mac/Linux
venv\Scripts\activate # Windows

pip install -r requirements.txt
```

Create `backend/.env` from `.env.example`:
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

### 3. Frontend setup
```bash
cd ../frontend
npm install
npm start
```

Open the app at `http://localhost:3000`.

## Roadmap
- Deploy to cloud infrastructure (Render / AWS).
- Build analytics dashboards for AI insights and sprint metrics.
- Enhance Slack bot with two-way interaction.
- Further fine-tune the AI model for regulated industries.

## Project Structure
```
GenVis/
├── backend/
│   ├── agent_backend.py        # Core agent workflows
│   ├── integrations.py         # Jira + Slack helpers
│   ├── mock_api.py             # FastAPI application / routes
│   ├── requirements.txt        # Python dependencies
│   └── .env.example            # Sample env vars
│
├── frontend/
│   ├── public/
│   │   └── index.html
│   ├── src/
│   │   ├── App.js
│   │   ├── App.css
│   │   ├── index.js
│   │   ├── index.css
│   │   └── assets/
│   └── package.json
│
├── .gitignore
└── README.md
```

## Summary
GenVis streamlines product ideation, requirement drafting, and executive reporting by connecting AI-generated insights directly to enterprise tools like Jira and Slack. Initially tailored to PNC’s product workflow, GenVis is designed to scale for any organization that wants AI-assisted product delivery.
