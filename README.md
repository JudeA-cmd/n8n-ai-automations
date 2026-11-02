# n8n AI Automations

AI-powered workflows built with n8n and Google Gemini during the Nexith AI Academy (Cohort 6). Each folder holds the exported workflow, a README with the node chain and setup steps, and screenshots of a working run.

| # | Project | What it does |
|---|---------|--------------|
| 01 | [Daily Motivational Quote](01-daily-motivation) | Gemini writes a fresh quote at 07:00 and Gmail sends it to a Google Sheets recipient list |
| 02 | [AI ATS Resume Screening](02-ats-resume-screening) | Form intake, PDF text extraction, Gemini scores the CV against the job description, ranks candidates in Sheets, alerts HR and emails the candidate |
| 03 | [AI Email Assistant](03-ai-email-assistant) | Classifies Gmail into six categories, assigns priority, drafts a reply for human approval, labels the thread, routes unclear emails to review |

## Running any workflow
1. n8n → Create Workflow → ⋯ → Import from File → the project's `.json`
2. Add credentials: Google Gemini (PaLM) API, Gmail OAuth2, Google Sheets OAuth2 as listed in the project README
3. Set the Sheet IDs / Gmail labels the README names
4. Test, then Publish

Credentials are stored in n8n, never in these files.

## Author
Jude Mamah – Senior Commissioning & Start-Up Engineer, building automation and training tools for plant operations.
