# Webtop Smartschool skill

Read the Smartschool Webtop student portal through connected Chrome and create Hebrew student reports.

Webtop portal: [https://webtop.smartschool.co.il/](https://webtop.smartschool.co.il/)

## Install in Codex

See the [Codex skills guide](https://developers.openai.com/codex/skills) for how Codex discovers and invokes skills. To install this repository manually, download its ZIP from GitHub and copy `SKILL.md` and the `references/` folder into `~/.codex/skills/webtop/` (create the `webtop` folder if needed). The installed folder should contain `SKILL.md` and `references/student-modules.md`. Start a new Codex chat and invoke the skill with `$webtop`.

## Claude Code compatibility

Claude Code supports skills using `SKILL.md`. Its personal skill location is `~/.claude/skills/webtop/`, and the command is `/webtop`; see the [Claude Code skills guide](https://code.claude.com/docs/en/skills). This repository is currently written for Codex, so Claude Code use is not verified as a drop-in experience: you must also configure a browser integration that Claude Code can access to read Webtop through Chrome. The Codex connected-Chrome setup described below is not bundled for Claude Code.

## Setup

Requirements:

- Chrome with the connected Chrome extension enabled.
- An active login to the Webtop portal in that connected Chrome profile.
- The Smartschool student account and requested student selected in Webtop.

## How to use

Mention $webtop in a message and describe the report you want. You can write in Hebrew or English.

| Report | Example prompt |
| --- | --- |
| Last week's homework | `Use $webtop to list last week's homework in a Hebrew table.` |
| Specific dates | `Use $webtop to list homework from 01/09/2026 through 26/09/2026.` |
| New homework only | `Use $webtop to check for new or changed homework since the previous check.` |
| Daily all-updates message | `Use $webtop to check all supported sections for new or changed updates since the previous check and prepare one Hebrew message.` |
| WhatsApp text | `Use $webtop to prepare last week's homework as a Hebrew WhatsApp message.` |
| Timetable | `Use $webtop to show tomorrow's timetable and any available changes.` |
| Grades | `Use $webtop to summarize grades for the current study period.` |
| Attendance | `Use $webtop to list last week's recorded absences and lateness.` |
| Lesson events | `Use $webtop to list last week's lesson events, including positive feedback.` |
| Teacher messages | `Use $webtop to summarize last week's teacher messages and explicit deadlines.` |
| Full report | `Use $webtop to prepare a full weekly report in Hebrew: homework, grades, attendance and lesson events, teacher messages, and the current timetable with available changes.` |

Hebrew example:

> השתמש ב־$webtop והצג את שיעורי הבית של השבוע שעבר בטבלה בעברית.

## Example homework output

| תאריך השיעור | מקצוע | מורה | שיעורי בית | מועד הגשה | קבצים / הערות |
| --- | --- | --- | --- | --- | --- |
| 24/09/2026 | חשבון | דנה | להשלים עמודים 42–43 | לא צוין | — |
| 25/09/2026 | עברית | יעל | לקרוא את הטקסט ולענות על שאלות 1–3 | 29/09/2026 | קובץ: reading.pdf |

הטבלה מציגה תאריכי שיעור כפי שנרשמו ב-Webtop. אם אין הרשאה, אין נתונים, או שהקריאה חלקית, התשובה מציינת זאת במפורש.

## Defaults and scope

- “Last week” means the previous completed Sunday–Saturday week in Israel time. “Last seven days” means today and the previous six dates.
- Homework lists use a Hebrew table with lesson date, subject, teacher, homework, deadline, and attachments/notes. Dates on this page are lesson dates, not verified publication dates.
- WhatsApp or Telegram output is prepared for copying by default; it is not sent automatically.
- New-update checks compare with saved local history. A full date-range list includes previously reported homework too.
- The regular timetable is current, not a reconstruction of past weeks. Timetable changes may be unavailable if the account lacks permission.
- Reports read existing records; they do not submit absence justifications or request retests.

## Saved history

Reports and comparison observations are stored locally in `~/smartschool-homework`. This is local file history, not account-wide memory. Credentials, session tokens, and bot tokens are not saved there.

## Daily scheduling options

Creating this skill does not activate a schedule. Choose either a homework-only check or a daily message covering all supported updates.

For homework only, configure a daily task at a time you choose (the earlier requested time was **17:00, Asia/Jerusalem**) with this prompt:

> Use $webtop to check for new or changed homework, prepare the Hebrew update, and save the observations for the next run.

For all supported updates, use this prompt:

> Use $webtop to check homework, grades, attendance and lesson events, timetable changes, and teacher messages for new or changed records since the previous check. Prepare one Hebrew update covering all changes, clearly list any module you could not check, and save separate observations for the next run.

Choose how to deliver the update:

- **Prepare only:** leave it in chat as WhatsApp- or Telegram-ready text for you to copy. This is the default.
- **Send automatically:** configure one channel (WhatsApp or Telegram), the intended recipient, and a connected supported messaging integration. Add this instruction to the scheduled prompt: `Send the update via [WhatsApp or Telegram] to [the recipient configured for this task].` Sending is opt-in; if the channel or recipient is missing, or the integration is unavailable, the skill returns the prepared text and reports that it was not sent. Keep account credentials and bot tokens out of the skill files and history.

Example daily message:

```text
📚 עדכון Webtop יומי | 27/09/2026

שיעורי בית חדשים/שהשתנו:
• 27/9, חשבון: להשלים עמ׳ 42–43.

ציונים:
• 26/9, עברית: נוספה הערכה "הבנת הנקרא" — 90.

נוכחות ואירועי שיעור:
• 27/9, שיעור 2: נרשם איחור.

הודעות מורים:
• 26/9, יעל: להביא מחברת ביום שני.

שינויים במערכת: לא ניתן לבדוק — אין הרשאה לעמוד השינויים.

שליחה: נשלח דרך Telegram לנמען שהוגדר במשימה.
```

The example is illustrative; the message should include only records actually found since the previous successful check. On a module's first check, its existing records establish a baseline and are not described as new. Keep the computer and desktop app running, connected Chrome open, and the Webtop login active. Review the first run to verify access and output. If you already created a task using an earlier skill name, update its prompt to $webtop. A schedule is active only after the scheduling interface confirms it.

## Skill files

- [SKILL.md](SKILL.md): workflow and homework instructions.
- [Student modules](references/student-modules.md): timetable, grades, events, and messages.
