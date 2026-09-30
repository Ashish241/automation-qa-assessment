# Automation & QA Assessment — Ashish Kumar Ishwar

## Task 1: QA
Tested the Wasp RealWorld demo at https://wasp-rwa.netlify.app in Edge on Windows. Five findings cover authentication availability, failure feedback, client validation, label association and password autocomplete metadata. Registration/login preflights returned HTTP 503, blocking authenticated create/edit/delete/logout testing. See `Task1_QA_Report_Ashish_Kumar_Ishwar.pdf` and `Images/`. The original suggested demo returned 404.

## Task 2: API digest
JSONPlaceholder was selected because its free sample data needs no API key. `/posts` supplies posts; `/users/{userId}` enriches the highest-ID selected post with author and company. Code validates fields, sorts by descending ID and keeps five posts. ID order is a demonstration rule, not a publication-time ranking. A second Code node builds the digest and counts the top post's words. An IF node routes counts above 30 to a long-post message; other counts receive a standard brief. Telegram delivers to the tester's own chat using an n8n credential reference, without exporting the bot token.

## Errors and verification
Both HTTP nodes use an error output connected to a failure-message Code node and Telegram alert. The code handles string/object errors and limits details to 500 characters. Fetch Posts has a 10-second timeout; Fetch Author uses its default timeout. Telegram and Code failures stop visibly in execution history. Successful standard/long branch runs were demonstrated; `Images/task2_error.png` shows the Fetch Posts failure path executing. The tester confirmed both API failure tests. There is no separate Error Trigger workflow or retry policy.

## Run
Import `Task2_Workflow_Ashish_Kumar_Ishwar.json` into a compatible n8n instance. Create/select a Telegram credential, set your own Chat ID in all three Telegram nodes, and start your bot chat. Execute manually. Publish/activate to enable the hourly Schedule Trigger and keep n8n running. Export is inactive; timezone is Asia/Kolkata. Sample data produces a repeated digest rather than live news. Screenshots include the canvas, successful execution and failure path. Optional uptime bonus was not implemented.

## Walkthrough
Add the shareable recording link here before submission.
