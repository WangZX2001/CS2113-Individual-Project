# Algo

Algo is a command-line task manager written in Java. It helps you keep track of
todos, deadlines, and events through typed commands, and automatically saves
your task list between sessions.

This repository is maintained as a CS2113 individual project.

## Features

- Add todo, deadline, and event tasks
- List all saved tasks
- Mark and unmark tasks as done
- Delete tasks by task number
- Search tasks by keyword
- Persist tasks in a local save file

## Requirements

- JDK 17 or later
- A terminal or an IDE such as IntelliJ IDEA

## Project Structure

```text
src/main/java/algo/          Main application classes
src/main/java/algo/command/  Command implementations
src/main/java/algo/task/     Task models
docs/README.md               User guide
text-ui-test/                Legacy text UI test fixtures
```

The application entry point is `algo.Algo`.

## Running the Application

From the repository root:

```powershell
New-Item -ItemType Directory -Force bin
javac -cp src/main/java -d bin src/main/java/algo/*.java src/main/java/algo/command/*.java src/main/java/algo/task/*.java
java -cp bin algo.Algo
```

On startup, Algo shows a welcome message and waits for commands.

## Command Summary

| Action | Command format |
| --- | --- |
| List tasks | `list` |
| Add todo | `todo <description>` |
| Add deadline | `deadline <description> /by yyyy-MM-dd [HHmm]` |
| Add event | `event <description> /from yyyy-MM-dd [HHmm] /to yyyy-MM-dd [HHmm]` |
| Mark task as done | `mark <task number>` |
| Mark task as not done | `unmark <task number>` |
| Delete task | `delete <task number>` |
| Find tasks | `find <keyword>` |
| Exit | `bye` |

Dates must use `yyyy-MM-dd`. Times are optional and use 24-hour `HHmm`
format, for example `2026-09-20 1800`.

## Example Commands

```text
todo read book
deadline submit report /by 2026-09-20
deadline project meeting /by 2026-09-20 1800
event team meeting /from 2026-09-20 1400 /to 2026-09-20 1600
list
mark 2
find report
delete 1
bye
```

## Storage

Algo saves tasks to `data/algo.txt`. The `data` directory and save file are
created automatically when tasks are saved.

If the save file is missing, Algo starts with an empty task list. If the save
file cannot be read or has invalid formatting, Algo shows a loading warning and
starts with an empty task list.

## More Documentation

See [docs/README.md](docs/README.md) for the full user guide with examples.
