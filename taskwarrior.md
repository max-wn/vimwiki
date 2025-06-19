## taskwarrior

### links

1. https://taskwarrior.org/download/
2. https://taskwarrior.org/docs://taskwarrior.org/docs/
3. https://taskwarrior.org/docs/best-practices/
4. https://samgriesemer.com/Taskwarrior
5. https://github.com/GothenburgBitFactory/taskwarrior

### commands

Your tasks are now stored in `taskchampion.sqlite3` in your `task` directory. Backup this file!

example
```sh
# task commands
task add Prepare the first draft of the proposal due:friday  # Create task
task add Read Taskwarrior documents later  # Create task
task add priority:H Pay bills              # Create task
task ID modify project:Home                # Assign a project to your tasks if possible
task ID modify +problem +house             # Add useful tags to a task
task ID edit                               # edit task via your editor
# task reports
task list
task summary
task ghistory
task calendar
task burndown.daily
```

other examples see in `tldr`

---

[[/index|Get Back To Index]]
