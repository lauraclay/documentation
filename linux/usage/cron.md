# Cron / Crontab

Cron is a tool for configuring scheduled tasks on Unix systems, used to schedule commands or scripts to run periodically and fixed intervals, such as backing up the system's users' home folders every day at midnight, or logging CPU information every hour.

The command `crontab` (cron table) is used to edit the list of scheduled tasks in operation, and is done on a per-user basis - each user (including `root`) has their own `crontab`.

## Editing crontab

Run `crontab` with the `-e` flag to edit the cron table:

```
crontab -e
```

### Select an editor

The first time you run `crontab` you'll be prompted to select an editor - if you don't know the difference, choose `nano` by hitting `Enter`.

The layout for a cron entry is made up of six components:

Minute, Hour, Day of Month, Month of Year, Day of Week and the command to be executed.

```
# m h  dom mon dow   command
```

```
# * * * * *  command to execute
# ┬ ┬ ┬ ┬ ┬
# │ │ │ │ │
# │ │ │ │ │
# │ │ │ │ └───── day of week (0 - 7) (0 to 6 are Sunday to Saturday, or use names; 7 is Sunday, the same as 0)
# │ │ │ └────────── month (1 - 12)
# │ │ └─────────────── day of month (1 - 31)
# │ └──────────────────── hour (0 - 23)
# └───────────────────────── min (0 - 59)
```

For example:

```
0 0 * * *  /home/pi/backup.sh
```

This cron entry would run the `backup.sh` script every day at midnight.
