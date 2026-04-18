## taskwarrior

### links

1. https://taskwarrior.org/download/
2. https://taskwarrior.org/docs/  --> Documentation
3. https://taskwarrior.org/docs/best-practices/
4. https://archlinux.org/packages/extra/x86_64/task/
5. https://samgriesemer.com/Taskwarrior
6. https://github.com/GothenburgBitFactory/taskwarrior

### commands

TODO

- [X] Your tasks are now stored in `taskchampion.sqlite3` in your `task`
      directory. Backup this file!

```sh
# task commands
task add Prepare the first draft of the proposal due:friday  # Create task
task add Read Taskwarrior documents later  # Create task
task add priority:H Pay bills              # Create task
task ID edit                               # edit task via your editor
# task reports
task list
task summary
task ghistory
task calendar
task burndown.daily
# best practices
task ID modify project:'Home and garden'  # Assign a project to your tasks if possible
task ID modify due:31st
task ID start
task ID modify +problem +house  # Add useful tags to a task
task ID modify depends:OTHER_ID
# projects
task projects  # list your projects
# using a project hierarchy example:
task add project:Home.Kitchen Clean the floor
task add project:Home.Kitchen Replace broken light bulb
task add project:Home.Garden Plant the bulbs
task project:Home.Kitchen count
2
task project:Home.Garden count
1
task project:Home count
3
```

---

[[/index|Get Back To Index]]
