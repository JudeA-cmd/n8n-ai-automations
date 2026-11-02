# AI ATS Resume Screening

An applicant submits a form with a PDF CV. The workflow extracts the text, pulls the job description for the chosen role from Google Sheets, asks Gemini to score the candidate 0–100 with matched skills, missing skills, red flags and a justification, saves the record to a Candidates sheet (the ranking), alerts HR, and emails the candidate an interview invitation (score ≥ 70) or an acknowledgement.

## Flow
Application Form → Extract CV Text (PDF) → Get Job Description (Sheets) → Build Prompt (Code) → Gemini Screen CV (HTTP) → Parse Screening (Code) → Save to Candidates (Sheets) → Notify HR (Gmail) → Shortlisted? (IF ≥ 70)
- true → Invite Candidate (Gmail)
- false → Acknowledge Candidate (Gmail)

## Files
| File | Purpose |
|------|---------|
| `AI ATS Screening.json` | Workflow |
| `sample-data/ATS_Screening.xlsx` | Jobs tab (one JD) and Candidates tab headers – upload to Google Sheets |
| `sample-data/CV_Adaeze_Okonkwo_Process_Engineer.pdf` | Strong test candidate (scores 90+) |
| `sample-data/CV_Tunde_Bello_Marketing.pdf` | Off-target test candidate (scores < 30) |
| `screenshots/` | Canvas, both executions, Candidates sheet, HR and candidate emails |

## Setup
1. Upload `ATS_Screening.xlsx` to Google Drive → open with Sheets → File → Save as Google Sheets
2. Import the JSON; add Gemini, Google Sheets and Gmail credentials
3. Get Job Description and Save to Candidates → Document → pick the sheet
4. Notify HR → change the To address
5. Publish; share the form's Production URL with applicants

## Adding a role
Add a row to the Jobs tab and the same name to the form's Position dropdown. No other change.
