# CAIE Assignment 9 – Google Sheets to Gmail Automation

## Project Overview

This project demonstrates an n8n workflow that retrieves student records from Google Sheets, formats the records into a single email, and sends the email using Gmail.

## Workflow

The workflow contains the following nodes:

1. **Manual Trigger** – starts the workflow when the user clicks Execute Workflow.
2. **Google Sheets – Get Row(s)** – reads the student records from the configured spreadsheet and worksheet.
3. **Code** – filters out empty records, formats the available student details, and prepares one email subject and message.
4. **Gmail – Send a message** – sends the formatted summary email.

## Sample Data

The Google Sheet used for the workflow contains these student records:

| Name | Course | Status |
|---|---|---|
| Arun | Generative AI | Completed |
| Priya | Python | In Progress |
| Karthik | Data Analytics | Completed |
| Divya | n8n Automation | Pending |
| Rahul | Machine Learning | Progress |

## Empty-Data Handling

The Code node checks whether any valid student records are present. If no valid records are found, it returns no output, preventing the Gmail node from sending a blank summary email.

> The workflow includes this empty-data safeguard. A separate live test with an empty spreadsheet has not been documented.

## Email Output

When records are available, the workflow creates one email containing the student names, courses, and statuses in a readable numbered list.

**Subject:** Data Summary from Google Sheet

## Technologies Used

- n8n
- Google Sheets
- Google Gmail
- JavaScript (n8n Code node)
- Google OAuth 2.0

## Repository Contents

```text
CAIE_Assignment9_Google_Sheets_Gmail/
├── CAIE_ASSIGNMENT9.json
├── README.md
└── screenshots/
```

- `CAIE_ASSIGNMENT9.json` – exported n8n workflow.
- `README.md` – project documentation.
- `screenshots/` – screenshots demonstrating the workflow and its output.

## Setup Notes

1. Import `CAIE_ASSIGNMENT9.json` into your n8n instance.
2. Create or select Google Sheets and Gmail OAuth credentials in n8n.
3. Select the appropriate Google spreadsheet and worksheet in the Google Sheets node.
4. Configure the Gmail node with the intended recipient.
5. Execute the workflow and verify the email output.

**Security:** Google OAuth credentials are managed inside n8n. Do not commit client secrets, access tokens, refresh tokens, or other credentials to GitHub.

## Assignment Outcome

The workflow automates the process of collecting student data from Google Sheets and delivering it as a single formatted Gmail summary.
