# housemaint

Tracks recurring home maintenance for one person. It builds schedules from appliance manuals and shows what's due.

## Things in the home

**Asset**:
A thing in or around the home that needs maintenance, such as a water heater, the gutters or the smoke detectors.
_Avoid_: Item, appliance, equipment, device

**The House**:
The Asset that always exists. It holds maintenance that doesn't belong to any more specific Asset.
_Avoid_: Home, general, misc

**Document**:
A file attached to an Asset, such as a manual, receipt or warranty.
_Avoid_: Attachment, file

**Manual**:
A Document that describes how to maintain its Asset, and the only kind of Document that Extraction reads.
_Avoid_: Guide, instructions

**Receipt**:
A Document recording the purchase of an Asset.
_Avoid_: Invoice, proof of purchase

**Warranty**:
A Document stating an Asset's warranty terms.
_Avoid_: Guarantee, coverage

## Schedules

**Task**:
A recurring piece of maintenance on exactly one Asset, repeated every Interval.
_Avoid_: Chore, job, reminder, schedule

**Interval**:
The length of time between occurrences of a Task: a whole number of days, weeks, months or years.
_Avoid_: Frequency, period, cadence

**Retired**:
Hidden from the overview but kept with its full history, and it can be un-retired. Retiring an Asset retires all of its Tasks.
_Avoid_: Archived, inactive, disabled

**Overdue**:
A Task whose Due date is before today.
_Avoid_: Late, missed

**Due soon**:
A Task whose Due date is today or within the next 14 days.
_Avoid_: Upcoming (that's the next status), pending

**Upcoming**:
A Task whose Due date is more than 14 days away.
_Avoid_: Future, scheduled

**Completion**:
A record that a Task was done on a given date, with an optional note and cost.
_Avoid_: Log entry, done event, history item

**Last-done date**:
An optional date, entered when a Task is accepted, for when it was last done before housemaint tracked it. It is not a Completion.
_Avoid_: Initial completion, start date

**Due date**:
The date a Task is next due. It is one Interval after the Completion with the latest date (not the most recently entered one), or else after the Last-done date, or else after the date the Task was created. When adding months lands past the end of a month, it falls on that month's last day.
_Avoid_: Next date, deadline

## Extraction

**Extraction**:
Reading a Manual to propose Suggested Tasks.
_Avoid_: Import, parsing, scan

**Suggested Task**:
A Task proposed by Extraction. It is not tracked until the user accepts it.
_Avoid_: Draft, candidate, pending task

**Citation**:
The page number and verbatim quote from the Manual that a Suggested Task came from. It stays with the Task once the Task is accepted.
_Avoid_: Source, reference, evidence

**Review**:
The step where the user accepts, edits or rejects each Suggested Task.
_Avoid_: Approval, confirmation
