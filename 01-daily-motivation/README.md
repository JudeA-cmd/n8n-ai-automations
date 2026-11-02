# Daily Motivational Quote

Every day at 07:00 (Africa/Lagos) Gemini writes one original motivational quote and Gmail sends it to every Active recipient in a Google Sheet.

## Flow
Schedule Trigger (07:00) → Generate Quote (Gemini) → Get Recipients (Google Sheets, Status = Active) → Send Email (Gmail, one per row)

## Files
| File | Purpose |
|------|---------|
| `Daily Motivational Quote - Gemini.json` | Workflow |
| `screenshots/` | Canvas after a green run, delivered email, recipient sheet |

## Setup
1. Google Sheet with a tab `Recipients` and headers `Name | Email | Status`; set Status to Active for each recipient
2. Import the JSON; add Google Gemini (PaLM) API, Google Sheets OAuth2 and Gmail OAuth2 credentials
3. Get Recipients → Document → pick the sheet
4. Workflow Settings → Timezone → Africa/Lagos
5. Publish

## Notes
The prompt injects today's date and a random theme so each day's quote differs. The quote is generated once per run and reused for every recipient.
