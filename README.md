# SUNHACKS - ATS (Applicant Tracking System)

An AI-powered Applicant Tracking System built with **Django**. This platform streamlines the recruitment process by automatically parsing applicant resumes (both PDF and image formats) and extracting relevant skills, key performance metrics (like CGPA), and total experience using **Google Generative AI (Gemini)**.

## Core Domain Models & Features

- **Automated Resume Parsing**: Handles both PDF (using `PyMuPDF`/`fitz`) and Image (`.jpg`, `.png`) uploads. 
- **AI-Driven Data Extraction**: Integrates with Google's Generative AI (`gemini-pro` and `gemini-pro-vision`) to run intelligent prompts that extract specific structured metadata (skills, CGPA, total experience duration) directly from unstructured resume text or images.
- **Applicant Management**: Stores parsed data in a local SQLite database under the `Applicant` model, mapping contact information directly alongside AI-generated skill summaries.

## Prerequisites

- **Python 3.8+**
- **SQLite3**
- **Google Generative AI API Key** (Required for Gemini access)

## Installation & Setup

1. **Clone the repository**:
   ```bash
   git clone <repo-url>
   cd SUNHACKS
   ```
2. **Create and activate a virtual environment**:
   ```bash
   python -m venv venv
   source venv/bin/activate
   ```
3. **Install Dependencies**:
   ```bash
   pip install -r requirements.txt
   # Ensure PyMuPDF, google-generativeai, and Django are installed
   ```
4. **Configure API Key**:
   - Locate the API key configurations in `ats/views.py`.
   - Replace the hardcoded `api_key` with your valid Google API Key (or ideally, move it to an environment variable).
5. **Run Migrations**:
   ```bash
   python manage.py makemigrations
   python manage.py migrate
   ```

## Usage / Running Locally

To run the application locally:
```bash
python manage.py runserver
```
Navigate to `http://127.0.0.1:8000/` to access the applicant interface, upload a resume, and trigger the AI parsing pipeline.

## Project Structure

```text
.
├── k/                       # Django project settings and WSGI/ASGI configurations
├── ats/                     # Core App logic
│   ├── models.py            # Applicant and Keyword schema definitions
│   ├── views.py             # Route handlers and Gemini AI extraction logic (pdfkey, imgkey)
│   ├── templates/           # HTML views (index, login, resume, thank)
│   └── static/              # CSS and JS assets
├── db.sqlite3               # Local database
└── manage.py                # Django execution entry point
```
