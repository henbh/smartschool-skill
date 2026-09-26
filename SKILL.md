---
name: webtop-smartschool
description: Read the Smartschool Webtop student portal through connected Chrome and produce Hebrew homework, timetable, grade, attendance, lesson-event, and teacher-message reports.
---

# Webtop Smartschool

Smartschool is the product and Webtop is its student portal. Use this skill for requests mentioning either name. The connected Chrome profile must already be signed in.

## Defaults

- Homework default: previous completed Sunday-Saturday week in Asia/Jerusalem. State exact dates.
- Last seven days means today and the preceding six dates.
- Homework table columns: תאריך השיעור | מקצוע | מורה | שיעורי בית | מועד הגשה | קבצים / הערות.
- Dates shown by Webtop are lesson dates, not verified posting timestamps.
- Do not infer deadlines, page ranges, grades, absences, or teacher roles.
- Do not send messages, submit absence justifications, or request retests.

## Modules

Homework is read from Student Card 11 and the homework column only. Lesson topics alone are not homework. Combine repeated assignments while preserving distinct instructions and attachment names.

Timetable is Student Card 10. Show the current weekly grid and label it current. Timetable changes are under Timetable_Changes; if permission is denied, report that limitation.

Grades are Student Card 6. Preserve period, assessment name, teacher, subject, grade, verbal evaluation, weight, components, notes, date, and retest-request state. Never treat a missing grade as zero.

Lesson events and attendance are Student Card 4. Preserve event type, date, lesson, study group, note, justification, and reason. A missing presence row is not proof of absence. Include Student Card 5 only for a full event report.

Teacher messages are Messages. Filter by sent date, summarize message bodies and explicit deadlines, and list attachments. Reading is allowed; replying, deleting, moving, or bulk marking is outside scope.

## Output and history

Use Hebrew tables for reports and Hebrew WhatsApp-ready text only when requested. Separate modules into sections. Report empty results, partial coverage, and permission limits clearly.

For recurring homework checks, read the local history at ~/smartschool-homework, compare content, and report only new or changed assignments. Save dated observations after successful reads. Never save credentials or unrelated student data.

Use the explicit invocation $webtop-smartschool.
