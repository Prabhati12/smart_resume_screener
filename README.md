# smart_resume_screener

```markdown
# AI-Powered Resume Screening Dashboard

This project is an automated resume screening system built with Streamlit and GoogleAI Studio(API key extraction). It extracts structured candidate data from PDF resumes, compares it against a job description, assigns a fit score, and stores all results in an SQLite database for future reference.

## Features

- PDF resume parsing using PyPDF2
- Structured data extraction using Google Gemini with Pydantic
- Objective job fit scoring (1–10) with justification
- Interactive web interface built with Streamlit
- Persistent storage of results using SQLite

## Tech Stack

| Technology        | Purpose |
|-------------------|---------|
| Streamlit         | Web interface |
| Google Gemini API | Data extraction and scoring |
| Pydantic          | Structured output validation |
| PyPDF2            | PDF text extraction |
| SQLite3           | Database storage |

## Project Structure
├── dashboard.py           # Main Streamlit application
├── models.py              # Pydantic schemas (CandidateData, MatchResult)
├── requirements.txt       # Dependencies
├── recruitment_results.db # Auto-created SQLite database
└── venv/                  # Virtual environment (optional)
```
## Installation and Setup

### 1. Clone the Repository
````

```bash
git clone https://github.com/YourUsername/YourRepoName.git
cd YourRepoName
````

### 2. Create and Activate Virtual Environment

```bash
python -m venv venv

# Windows:
.\venv\Scripts\activate

# macOS/Linux:
source venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install streamlit google-genai pydantic pypdf
```

## Set the Gemini API Key

Obtain your API key from Google AI Studio and configure it in your terminal.

### macOS/Linux

```bash
export GEMINI_API_KEY="YOUR_API_KEY_HERE"
```

### Windows (Command Prompt)

```bash
set GEMINI_API_KEY=YOUR_API_KEY_HERE
```

### Windows (PowerShell)

```bash
$env:GEMINI_API_KEY="YOUR_API_KEY_HERE"
```

## Run the Application

```bash
streamlit run dashboard.py
```

Open your browser at `http://localhost:8501`

## Database Persistence (SQLite)

The application stores all results in a local SQLite database (`recruitment_results.db`) under the `results` table.

| Column               | Type    | Description                      |
| -------------------- | ------- | -------------------------------- |
| id                   | INTEGER | Primary Key                      |
| timestamp            | TEXT    | Processing date/time             |
| candidate_name       | TEXT    | Extracted name                   |
| job_description_hash | TEXT    | JD identifier                    |
| score                | REAL    | Fit score (1–10)                 |
| candidate_json       | TEXT    | Extracted candidate data (JSON)  |
| match_json           | TEXT    | Scoring and justification (JSON) |

## LLM Processing Flow

1. Upload PDF resume
2. Extract and structure candidate data using Gemini and Pydantic
3. Compare against job description
4. Generate fit score with justification
5. Store results in SQLite database
