# Algo User Guide

Algo is a command-line task manager for users who prefer quick typed commands.
It supports todos, deadlines, and events, and saves your task list automatically
between sessions.

## Quick Start

Run the application, then enter one command per line. Use `bye` to exit.

```text
todo read book
deadline submit report /by 2026-09-20
event team meeting /from 2026-09-20 1400 /to 2026-09-20 1600
list
bye
```

## Adding Todo Tasks

Adds a task without a date or time.

Format:

```text
todo <description>
```

Example:

```text
todo read book
```

Expected outcome:

```text
Got it. I've added this task:
[T][ ] read book
Now you have 1 tasks in the list.
```

## Adding Deadlines

Adds a task that must be completed by a date, with an optional time.

Format:

```text
deadline <description> /by yyyy-MM-dd [HHmm]
```

Examples:

```text
deadline submit report /by 2026-09-20
deadline project meeting /by 2026-09-20 1800
```

Expected outcome:

```text
Got it. I've added this task:
[D][ ] submit report (by: Sep 20 2026)
Now you have 1 tasks in the list.
```

## Adding Events

Adds a task that happens between a start date/time and an end date/time. The end
must be after the start.

Format:

```text
event <description> /from yyyy-MM-dd [HHmm] /to yyyy-MM-dd [HHmm]
```

Example:

```text
event team meeting /from 2026-09-20 1400 /to 2026-09-20 1600
```

Expected outcome:

```text
Got it. I've added this task:
[E][ ] team meeting (from: Sep 20 2026 14:00 to: Sep 20 2026 16:00)
Now you have 1 tasks in the list.
```

## Listing Tasks

Displays all stored tasks.

Format:

```text
list
```

Expected outcome:

```text
Here are the tasks in your list:
1.[T][ ] read book
2.[D][ ] submit report (by: Sep 20 2026)
```

If there are no tasks, Algo displays:

```text
No tasks yet
```

## Marking Tasks

Marks a task as done.

Format:

```text
mark <task number>
```

Example:

```text
mark 2
```

Expected outcome:

```text
Nice! I've marked this task as done:
[D][X] submit report (by: Sep 20 2026)
```

## Unmarking Tasks

Marks a completed task as not done.

Format:

```text
unmark <task number>
```

Expected outcome:

```text
OK, I've marked this task as not done yet:
[D][ ] submit report (by: Sep 20 2026)
```

## Deleting Tasks

Removes a task from the list.

Format:

```text
delete <task number>
```

Example:

```text
delete 1
```

Expected outcome:

```text
Noted. I've removed this task:
  [T][ ] read book
Now you have 1 tasks in the list.
```

## Finding Tasks

Searches task descriptions for a keyword. Search is case-insensitive.

Format:

```text
find <keyword>
```

Example:

```text
find report
```

Expected outcome:

```text
Here are the matching tasks in your list:
1.[D][ ] submit report (by: Sep 20 2026)
```

If there are no matches, Algo displays:

```text
No matching tasks found.
```

## Exiting

Closes the application.

Format:

```text
bye
```

Expected outcome:

```text
Bye. Hope to see you again soon!
```

## Storage

Tasks are saved automatically in:

```text
data/algo.txt
```

If the save file is deleted, Algo starts with an empty task list and creates a
new save file the next time tasks are saved.

Manual edits to the save file are not recommended. If the file format is
invalid, Algo displays:

```text
Warning: Could not load tasks from storage.
```

## Command Summary

| Action | Format |
| --- | --- |
| List tasks | `list` |
| Add todo | `todo <description>` |
| Add deadline | `deadline <description> /by yyyy-MM-dd [HHmm]` |
| Add event | `event <description> /from yyyy-MM-dd [HHmm] /to yyyy-MM-dd [HHmm]` |
| Mark task | `mark <task number>` |
| Unmark task | `unmark <task number>` |
| Delete task | `delete <task number>` |
| Find tasks | `find <keyword>` |
| Exit program | `bye` |

## Common Errors

| Scenario | Message |
| --- | --- |
| Unknown command | `Invalid command.` |
| Empty todo description | `The description of a todo cannot be empty.` |
| Missing task number | `Please specify a task number.` |
| Non-numeric task number | `Task number must be a number.` |
| Task number outside the list | `Invalid task number.` |
| Missing find keyword | `Usage: find <keyword>` |
| Deadline format issue | `Usage: deadline <desc> /by yyyy-MM-dd [HHmm]` |
| Event format issue | `Usage: event <desc> /from yyyy-MM-dd [HHmm] /to yyyy-MM-dd [HHmm]` |
| Event end is not after start | `Event end time must be after start time.` |
