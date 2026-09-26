# Webtop Smartschool skill

Read the Smartschool Webtop student portal through connected Chrome and create Hebrew student reports.

Webtop portal: https://webtop.smartschool.co.il/

## Requirements

- Chrome with the connected Chrome extension enabled.
- An active login to the Webtop portal in that connected Chrome profile.
- The Smartschool student account and requested student selected in Webtop.

If Chrome or the login is unavailable, the skill reports the access blocker instead of guessing.

## How to use

Mention $webtop in a message and describe the report you want. You can write in Hebrew or English.

| Report | Example prompt |
| --- | --- |
| Last week's homework | Use $webtop to list last week's homework in a Hebrew table. |
| Specific dates | Use $webtop to list homework from 01/09/2026 through 26/09/2026. |
| New homework | Use $webtop to check for new or changed homework since the previous check. |
| WhatsApp text | Use $webtop to prepare last week's homework as a Hebrew WhatsApp message. |
| Timetable | Use $webtop to show tomorrow's timetable and any available changes. |
| Grades | Use $webtop to summarize grades for the current study period. |
| Attendance | Use $webtop to list last week's recorded absences and lateness. |
| Teacher messages | Use $webtop to summarize last week's teacher messages and explicit deadlines. |
| Full report | Use $webtop to prepare a full weekly report in Hebrew. |

Hebrew example:

> השתמש ב־$webtop והצג את שיעורי הבית של השבוע שעבר בטבלה בעברית.

## Example output

| תאריך השיעור | מקצוע | מורה | שיעורי בית | מועד הגשה | קבצים / הערות |
| --- | --- | --- | --- | --- | --- |
| 24/09/2026 | חשבון | דנה | להשלים עמודים 42–43 | לא צוין | — |
| 25/09/2026 | עברית | יעל | לקרוא את הטקסט ולענות על שאלות 1–3 | 29/09/2026 | קובץ: reading.pdf |

הטבלה מציגה תאריכי שיעור כפי שנרשמו ב-Webtop. אם אין הרשאה, אין נתונים, או שהקריאה חלקית, התשובה מציינת זאת במפורש.

## Defaults and scope

- Last week means the previous completed Sunday–Saturday week in Israel time. Last seven days means today and the previous six dates.
- Homework lists use a Hebrew table with lesson date, subject, teacher, homework, deadline, and attachments or notes.
- WhatsApp output is text for you to copy; it is not sent automatically.
- New-homework checks compare with saved local history. A full date-range list includes previously reported assignments too.
- The regular timetable is current, not a reconstruction of past weeks.
- Reports read existing records; they do not submit absence justifications, request retests, or send teacher messages.

## Saved history

The existing baseline and reports stay in ~/smartschool-homework. This is local file history, not account-wide memory. Credentials are not saved there.

## Daily scheduling suggestions

Creating this skill does not activate a schedule. In the desktop app's Scheduled section, create a daily task at 17:00 in Asia/Jerusalem with this prompt:

> Use $webtop to check for new or changed homework, prepare a Hebrew WhatsApp-ready message, and save the observations for the next run.

Keep the computer and desktop app running, keep connected Chrome open, and keep the Webtop login active. Review the first run to verify access and output. The prompt checks homework only; request a full report if you want grades, attendance, messages, or timetable data too. A schedule is active only after the scheduling interface confirms it.

## Skill files

- [SKILL.md](SKILL.md): workflow and homework instructions.
- [Student modules](references/student-modules.md): timetable, grades, events, and messages.
