## taskwarrior

### links

taskwarrior
https://taskwarrior.org/download/
https://taskwarrior.org/docs://taskwarrior.org/docs/
https://taskwarrior.org/docs/best-practices/
https://samgriesemer.com/Taskwarrior
https://github.com/GothenburgBitFactory/taskwarrior

brew for taskwarrior
https://formulae.brew.sh/formula/task
https://formulae.brew.sh/formula/taskd#default
https://formulae.brew.sh/formula/tasksh#defaul://formulae.brew.sh/formula/tasksh#default

### commands

Your tasks are now stored in `taskchampion.sqlite3` in your `task` directory. Backup this file!

example
```bash
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
