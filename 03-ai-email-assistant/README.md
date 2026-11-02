# AI Email Assistant

Reads incoming Gmail, classifies each email into Sales / Support / Billing / Partnerships / Jobs / Others, assigns High / Medium / Low priority, writes a 2-sentence summary and a draft reply, applies the matching Gmail label, and saves the reply as a Gmail draft inside the thread for human approval. Nothing is sent automatically. Low-confidence or unparseable results go to a Needs Review label with a note explaining why.

## Flow
Gmail Trigger → Prepare Email (Code) → AI Classify (Gemini via HTTP) → Parse AI Output (Code) → Needs Review? (IF)
- true → Label Needs Review → Review Draft
- false → Switch Category → Label Sales | Support | Billing | Partnerships | Jobs | Others → Create Draft

Error handling: retries on the Gemini call, a try/catch in Parse AI Output that forces review, and a separate Error Trigger workflow that emails an alert if any node fails.

## Files
| File | Purpose |
|------|---------|
| `AI Email Assistant.json` | Main workflow |
| `AI Email Assistant - Error Handler.json` | Error Trigger → alert email |
| `system_prompt.txt` | AI role, tone, category and priority rules, restrictions, JSON schema |
| `screenshots/` | Canvas, six test executions, Gmail labels, drafts, error alert |

## Setup
1. Gmail: create labels Sales, Support, Billing, Partnerships, Jobs, Others, Needs Review
2. Import both JSON files; add Google Gemini (PaLM) API and Gmail OAuth2 credentials
3. Main workflow → Settings → Error Workflow → select the handler
4. Publish. The trigger polls INBOX every minute

## Tested scenarios
Sales quote, login problem, double charge, speaking invitation, job application, and a one-line ambiguous email (routed to Needs Review).

## Demo
Video: PASTE_LINK
