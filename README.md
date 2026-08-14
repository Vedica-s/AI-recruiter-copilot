# AI Recruiter Copilot

AI-powered recruitment copilot with multi-LLM orchestration for automated candidate sourcing, screening, and engagement.

## 🚀 Project Overview

AI Recruiter Copilot is an intelligent recruitment automation system that leverages multiple Large Language Models (LLMs) to streamline the hiring process. The system orchestrates five specialized AI agents to handle candidate sourcing, resume screening, skill assessment, and automated engagement — reducing time-to-hire while improving candidate quality.

Built as a hackathon project, this repo demonstrates multi-agent AI orchestration across GPT-4, Claude, and Gemini working together on a shared pipeline.

## ✨ Features

- **Multi-LLM Orchestration** — intelligent routing between GPT-4, Claude, and Gemini based on task requirements
- **Automated Candidate Sourcing** — AI-powered search across LinkedIn, GitHub, and job boards
- **Intelligent Resume Screening** — automated parsing and structured extraction of candidate profiles
- **Skills Assessment** — technical and soft-skill scoring against a job's requirements
- **Automated Engagement** — personalized outreach email generation
- **Analytics Dashboard** — tracks recruitment pipeline metrics (screened → qualified → contacted)
- **Composio Integration** — connects agents to external platforms and tools

## 🧩 My Contributions

This was a team hackathon build. My work focused on three of the five agents/modules:

- **Resume Parsing (Screening Agent)** — building the extraction pipeline that turns unstructured resumes into structured candidate data (PDF parsing, NLP extraction, entity recognition)
- **Candidate Scoring (Assessment Agent)** — designing the scoring logic that ranks candidates against job requirements
- **Analytics Dashboard** — the reporting layer that surfaces pipeline metrics (total screened, qualified, contacted)

Sourcing (candidate discovery via Composio) and Engagement (outreach email generation) were built by other teammates.

## 📋 Requirements

- Python 3.8+
- OpenAI API key
- Anthropic API key (for Claude)
- Google AI API key (for Gemini)
- Composio account and API key
- Internet connection for API calls

## 🔧 Installation

```bash
# Clone the repository
git clone https://github.com/Vedica-s/AI-recruiter-copilot.git
cd AI-recruiter-copilot

# Create a virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

## 🔑 Environment Configuration

Create a `.env` file in the root directory (see `.env.example`):

```
# OpenAI Configuration
OPENAI_API_KEY=your_openai_api_key_here

# Anthropic Configuration
ANTHROPIC_API_KEY=your_anthropic_api_key_here

# Google AI Configuration
GOOGLE_AI_API_KEY=your_google_ai_api_key_here

# Composio Configuration
COMPOSIO_API_KEY=your_composio_api_key_here

# Database Configuration (Optional)
DATABASE_URL=sqlite:///recruiter.db

# Email Configuration (Optional)
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=your_email@gmail.com
SMTP_PASSWORD=your_app_password

# Application Settings
ENVIRONMENT=development
LOG_LEVEL=INFO
```

**Note:** Never commit your `.env` file to version control.

## 🚀 How to Run

```bash
# Run the main recruiter agent
python main.py

# Run with a specific job description
python main.py --job-file configs/job_descriptions/example.json

# Run with custom configuration
python main.py --config custom_config.yaml

# Run in interactive mode
python main.py --interactive
```

## 📊 Expected Input/Output

**Input** — job description in JSON format:

```json
{
  "title": "Senior Software Engineer",
  "company": "Tech Corp",
  "requirements": [
    "5+ years Python experience",
    "Experience with AI/ML frameworks",
    "Strong problem-solving skills"
  ],
  "nice_to_have": [
    "Open source contributions",
    "Leadership experience"
  ],
  "location": "Remote",
  "salary_range": "$120k-$180k"
}
```

**Output** — ranked candidates with match reasoning and pipeline summary:

```json
{
  "candidates": [
    {
      "name": "John Doe",
      "score": 92,
      "profile_url": "https://linkedin.com/in/johndoe",
      "match_reasons": [
        "8 years Python experience",
        "Contributed to TensorFlow",
        "Led team of 5 engineers"
      ],
      "email_draft": "Personalized outreach message..."
    }
  ],
  "summary": {
    "total_screened": 150,
    "qualified": 25,
    "contacted": 10
  }
}
```

## 🔄 Workflow Summary

1. **Job Analysis** — parse and understand job requirements using GPT-4
2. **Candidate Sourcing** — search platforms using Composio integrations
3. **Resume Screening** — extract and structure candidate information with Claude
4. **Skills Matching** — score candidates against requirements using Gemini
5. **Ranking** — sort candidates by fit score and availability
6. **Engagement** — generate personalized outreach emails
7. **Follow-up** — track responses and schedule interviews
8. **Analytics** — generate recruitment pipeline reports

## 🤖 Agents Breakdown

| Agent | Model | Function | Tools |
|---|---|---|---|
| Sourcing | GPT-4 | Discovers candidates across platforms | LinkedIn API, GitHub API, Indeed scraper |
| Screening | Claude | Parses resumes, extracts structured data | PDF parser, NLP extraction, entity recognition |
| Assessment | Gemini | Evaluates technical/soft skills | Skill taxonomy, scoring algorithms |
| Engagement | GPT-4 | Creates personalized communication | Email templates, tone analyzer |
| Orchestrator | Multi-LLM | Coordinates agents, manages workflow | State management, decision routing |

## 👥 Team

- **Vedica** — Resume Parsing (Screening Agent), Candidate Scoring (Assessment Agent), Analytics Dashboard


## 🎯 Future Enhancements

- [ ] Video interview scheduling automation
- [ ] Integration with ATS systems
- [ ] Advanced analytics dashboard
- [ ] Multi-language support
- [ ] Mobile application
- [ ] Chrome extension for quick candidate evaluation
