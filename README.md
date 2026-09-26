# Webtop Smartschool skill

A Codex skill for reading the Smartschool Webtop student portal and producing Hebrew student reports.

## Use

Invoke with $webtop-smartschool to:
- list last week's homework in a Hebrew table
- show homework for specific dates
- summarize grades
- list attendance or lesson events
- show the current timetable and available changes
- summarize teacher messages and deadlines
- prepare a Hebrew WhatsApp-ready message
- prepare a full weekly report

Last week means the previous completed Sunday-Saturday week in Asia/Jerusalem. WhatsApp output is prepared for copying and is not sent automatically. Timetable changes may be unavailable when the account lacks permission. The skill reads records and does not submit justifications, request retests, or send messages.

Local recurring history can be stored in ~/smartschool-homework. Do not commit credentials, student identifiers, or local history.
