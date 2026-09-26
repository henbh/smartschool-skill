---
name: webtop
description: Read the Smartschool Webtop student portal through connected Chrome and produce Hebrew homework, timetable, grade, attendance, lesson-event, and teacher-message reports.
---

# Webtop Smartschool

Smartschool is the product and Webtop is its student portal. Use $webtop for explicit invocation. Natural-language requests mentioning either name also route here. The connected Chrome profile must already be signed in.

## Defaults

- Homework default: previous completed Sunday-Saturday week in Asia/Jerusalem. State exact dates.
- Last seven days means today and the preceding six dates.
- Homework table columns: תאריך השיעור | מקצוע | מורה | שיעורי בית | מועד הגשה | קבצים / הערות.
- Dates shown by Webtop are lesson dates, not verified posting timestamps.
- Do not infer deadlines, grades, absences, or teacher roles.
- Do not submit justifications or request retests.

## Requirements

Use connected Chrome with its browser extension enabled, an active login to https://webtop.smartschool.co.il/, and the requested student selected. If Chrome or login is unavailable, explain the access blocker.

## Modules

Homework is read from Student Card 11 and the homework column only; lesson topics alone are not homework. Preserve instructions and attachments. Timetable is Student Card 10; label the regular grid current. Timetable changes are under Timetable_Changes and may be permission-denied. Grades are Student Card 6; preserve assessment details and never treat a missing grade as zero. Lesson events and attendance are Student Card 4; a missing presence row is not proof of absence. Include Student Card 5 for a full event report. Teacher messages are under Messages; read bodies, deadlines, and attachments. Reading is allowed; replying, deleting, moving, or bulk marking is outside scope.

## Reports and change detection

Use separate Hebrew report sections and clearly state date range, empty results, partial coverage, and permission limits. Do not present the current timetable as past history.

A daily homework update checks new or changed homework. A daily all-updates request checks homework, grades, attendance/events, verifiable timetable changes, and teacher messages against separate saved observations. Return only new or substantively changed records. First successful reads establish baselines and are not proof records are new. If a module is inaccessible or partial, name that limitation and do not claim no changes across all modules.

For recurring checks, read and update task-relevant history under ~/smartschool-homework. Store module observations separately with check time, student, year, date range, and coverage limitations. Preserve prior observations for comparisons. Revisit homework ranges to catch late additions. Never infer completion from age or disappearance. Do not save credentials, session tokens, or unrelated student data.

## Message format and delivery

For requested messaging output, write a concise Hebrew WhatsApp- or Telegram-ready update grouped by date/module. WhatsApp formatting can use single asterisks for bold. Separate actual homework from classwork notes. State when no changes were found and identify which modules were checked.

Preparing text is the default and does not send it. Sending is opt-in: the user must choose WhatsApp or Telegram, specify the intended recipient, and authorize sending in the request or scheduled task. Use only a connected, supported integration. Never guess the recipient or save login credentials or bot tokens. If the channel or integration is unavailable, return the prepared text and say it was not sent.

## Scheduling

The skill does not activate schedules. A daily homework-only prompt can be: Use $webtop to check for new or changed homework, prepare a Hebrew update, and save the observations for next time.

For all supported updates use: Use $webtop to check homework, grades, attendance and lesson events, timetable changes, and teacher messages for new or changed records since the previous check. Prepare one Hebrew update covering all changes, list any module that could not be checked, and save separate observations for next time.

To send automatically, append: Send the update via [WhatsApp or Telegram] to [the recipient configured for this task]. Do not send if the channel or recipient is unspecified or the integration is unavailable. Set the chosen schedule time separately and report it active only after the scheduling interface confirms it.
