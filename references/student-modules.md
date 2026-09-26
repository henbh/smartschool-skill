# Additional Smartschool modules

Navigation and field names below were observed on 2026-09-26. Reconfirm the live page, selected student, year, period, filters, and pagination on each run. Use visible navigation if routes change. Collect only requested modules. These are read-and-summarize workflows; adding support does not authorize replying to messages, submitting justification, requesting a retest, or editing records.

## Timetable and changes

- Regular timetable: `מערכת שעות`, `/Student_Card/10`. Student and school-year selectors are visible. The grid is organized by weekday and lesson number, with subject and teacher in populated cells.
- Use the grid's actual weekday and lesson labels to map cells. Some accessibility text omits the number inside the cell; use the associated container/header or screenshot rather than inferring the number from text order.
- Output `יום | שיעור / שעה | מקצוע | מורה | חדר / הערות`, omitting room information if absent. Do not invent clock times from lesson numbers.
- Changes: `מ. שעות ושינויים`, `/Timetable_Changes`. On the observed account this returned `לא נמצאו הרשאות לצפייה בנתונים`. If still denied, state that changes could not be checked and use the regular timetable only as a labeled fallback. Do not work around permissions.
- If the changes page becomes accessible, inspect its actual date controls and record only explicitly shown cancellations, substitutions, and room/time changes. Suggested output: `תאריך | שיעור | השינוי | פרטים`. Do not interpret a blank regular-timetable slot as a cancellation.
- Default undated timetable request: current regular weekly timetable. For tomorrow or another day, specify the exact date and whether exceptions were verifiable. Last-week reports cannot reconstruct historical changes from the current regular grid.

## Grades

- `ציונים שוטפים`, `/Student_Card/6`; observed selectors include `שנת לימוד` and `תקופת לימוד` (e.g. `מחצית א`), with sort and export controls.
- Observed fields: `שם האירוע`, `מורה`, `מקצוע`, `ציון`, `הערכה מילולית`, `משקל`, `מרכיבי הערכה`, `הערה`, `תאריך`, and `בקשה למועד ב׳`.
- Read every applicable period when a date range crosses periods. Filter by the displayed assessment date; do not assume it is the publication date.
- Output `תאריך | מקצוע | אירוע / הערכה | ציון | הערכה מילולית / הערות | מורה`. Include weight/components when present and useful or requested.
- An assessment row can exist without a numeric grade. Show `לא הוזן ציון` rather than zero, failure, or completion. Preserve qualitative grades as text. Do not calculate an official average from incomplete marks or unknown weighting; any requested calculation must state its inputs and method.
- Do not select the retest-request checkbox while reading.
- Default undated grades request: selected current study period, named explicitly in the result.

## Attendance and lesson events

- `אירועי שיעור`, `/Student_Card/4`; study-year/period controls, sorting, and tabs `פירוט אירועים` and `מונה אירועים` were visible.
- Detail fields: `סוג האירוע`, `תאריך`, `שעה`, `קבוצת לימוד`, `הערה`, `הצדקה`, `סיבת הצדקה`, `הערות להצדקה`.
- Events can include presence, absence, lateness, missing homework/materials, and positive feedback. Preserve the actual category. Do not classify every event as absence or misconduct, and do not infer absence from a missing presence entry.
- Output `תאריך | שיעור | סוג האירוע | מקצוע / מורה | הערה | הצדקה` with justification reasons where provided.
- For a weekly student report, include positive feedback (מילים טובות) and behavior-related comments as separate subsections. Preserve the site's original category and wording; count records for the requested week and group by subject only when the event is actually associated with a subject in the source. Do not infer a subject from the timetable or call ordinary academic reminders/missing materials behavior notes.
- Attendance-only requests include only relevant attendance categories. Broader lesson-event requests include positive and other events too. Keep distinct lesson records even when the same event text appears twice in a day; totals count records, not unique wording.
- Use the counter tab only when needed, and ensure its period matches the report. If counting detail rows, label totals as counts of recorded events, not school days or attendance percentages.
- For year-to-date statistics, inspect all available records from the start of the selected school year through the report date, or use the site's event counter with the school-year filter explicitly set. Summarize recorded absences, lateness, positive-feedback entries, and behavior-note entries separately; show breakdowns by subject/category when supported. State the exact school year and covered dates. Do not treat period counts as year totals, do not add an incomplete detail-page count to a counter count, and state any unavailable category, filter, pagination, or permission limitation. These are counts of records, not unique days or percentages.
- `אירועים מחוץ לשיעור`, `/Student_Card/5`, is a separate section. The observed page had no data. Include it for a full event report and adapt to actual fields if records appear.
- Default undated events request: previous completed Sunday–Saturday week. No matching records means no recorded events in the checked range, not proof of perfect attendance.

## Teacher messages

- `תיבת הודעות`, `/Messages` (observed inbox URL `/Messages?view=Inbox`). Controls include `חיפוש`, `סינון`, folders, and tabs `נכנסות`, `יוצאות`, `טיוטות`, `נמחקו`.
- Use the inbox for teacher-message summaries. Read relevant message bodies, not just titles, when producing content summaries or action items. Opening a message may change its read status as an ordinary consequence of reading; do not bulk-change read status, delete, move, or reply.
- List entries display sender, sent date/time, and subject. Filter the requested range by sent date and read relevant attachments when needed. Separate teacher senders from system notices or unknown roles; do not guess a sender's role.
- Output `תאריך | שולח/ת | נושא | עיקרי ההודעה | פעולה נדרשת / מועד | קבצים`. Preserve explicit deadlines; distinguish your inferred action suggestions from the teacher's instructions.
- An unread count of zero does not mean the inbox is empty. Search/filter and pagination coverage must support any claim that all matching messages were read.
- The site indicated that messages through 30/06/26 were under `הודעות משנים קודמות` in the filter menu. For older ranges inspect this control and its current cutoff rather than assuming deleted messages.
- Default undated message summary: previous completed Sunday–Saturday week; an explicit unread/latest request overrides this.

## Reports and local history

For full weekly student reports use separate sections and tables for homework, grades/events, and messages, plus positive feedback, behavior notes, annual event statistics, and the current timetable. Show annual statistics year-to-date for the selected academic year and report date. WhatsApp format is optional on request. Store each module's observations separately under the existing history folder so a daily all-updates check can compare homework, grades, events, timetable changes, and messages without mixing their records. Keep enough event category, subject, date, lesson, and detail to audit the weekly breakdowns and annual counts. Save only task-relevant data, preserving student/year/range and check time. A module's first observation is a baseline, not proof its entries were newly posted.

Examples:

- `Use $webtop to show last week's homework in a Hebrew table.`
- `Use $webtop to summarize last week's homework, grades, lesson events, and teacher messages, plus the current timetable and any verifiable changes.`
- `Use $webtop to prepare my weekly student report: last week's homework, positive feedback, behavior notes counted and grouped by subject, year-to-date totals for absences and lateness, and the current timetable.`
- `Use $webtop to show tomorrow's timetable and changes.`
- `Use $webtop to summarize grades for the current semester.`
