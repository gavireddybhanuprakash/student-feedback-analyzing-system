# Student Feedback Analysis System

A Flask-based recreation of the publicly visible **Student Feedback Analysis System** prototype.

## Live prototype
https://nandini123.pythonanywhere.com/

## Features
- Anonymous feedback form with course, question, 1–5 rating and optional comments.
- SQLite database storage.
- Dashboard with response totals and course-wise average ratings.
- Aggregated course/question reports and CSV export.
- Privacy threshold: groups with fewer than **5 responses** are excluded from aggregate reports.
- Individual comments are never displayed on the dashboard or reports.

## Tech stack
- Python 3
- Flask
- SQLite
- HTML, CSS and JavaScript
- Chart.js (loaded from CDN for the dashboard chart)

## Project structure
```text
student-feedback-analysis-system/
├── app.py
├── requirements.txt
├── README.md
├── .gitignore
├── templates/
│   ├── base.html
│   ├── index.html
│   ├── dashboard.html
│   └── reports.html
└── static/
    ├── css/style.css
    └── js/main.js
```

## Run locally
1. Install Python 3.10 or newer.
2. Create and activate a virtual environment:
   ```bash
   python -m venv .venv
   # Windows:
   .venv\Scripts\activate
   # macOS/Linux:
   source .venv/bin/activate
   ```
3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
4. Start the application:
   ```bash
   python app.py
   ```
5. Open http://127.0.0.1:5000

The SQLite database (`feedback.db`) is created automatically on first run.

## Routes
| Route | Purpose |
|---|---|
| `/` | Submit anonymous feedback |
| `/dashboard` | View aggregate dashboard |
| `/reports` | View course/question report |
| `/reports.csv` | Download aggregate report as CSV |

## Privacy notes
This implementation does not ask for student names or roll numbers. Optional comments are stored in the database for internal use but are never rendered in public dashboard/report pages. Aggregate groups are displayed only after reaching five responses.

For a real deployment, use HTTPS, set a strong `SECRET_KEY`, restrict database access, configure backups and retention, and review institutional privacy requirements. The five-response threshold is a basic safeguard, not a guarantee against re-identification.

## Important
This ZIP is a **new source-code recreation based on the visible pages and behavior of the live prototype**. It is not the original PythonAnywhere source code, original database, or original response data. Review and customize the course/question lists and deployment settings before using it.
