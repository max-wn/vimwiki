## rsync cheatsheet

### links
https://rsync.samba.org/            # oficial site
https://wiki.archlinux.org/title/Rsync  # archwiki

### Basic example

```bash
rsync -avz ./src /dest    # syncing folder src into dest:
rsync -avz ./src/ /dest/  # syncing the content of src into dest:

# syncing the content of src into dest dir (examples):

## Recursively copy directories, use archive mode, resolve symlinks and skip files that are newer on the destination:
rsync --recursive --archive --update --copy-links path/to/src path/to/dest
## my script
sudo rsync -avzPuh --delete \
    ~/name_of_user/documents_1/ \
    /media/name_of_user/USB_8GB/docs1_backup/
sudo rsync -avzPuh --delete \
    ~/name_of_user/documents_2/ \
    /media/name_of_user/WD_Passport/docs2_backup/
## rsync over ssh
rsync -avz /path/to/file root@example.org:/path/on/the/server
## rsync to USB
rsync -avp /path/to/src /mount point/path/to/dest

    -a  # archive (-rlptgoD), where:
        -r, --recursive
        -l, --links      # copy symlinks as links
        -p, --perms      # preserve permissions
        -t, --times      # preserve times
        -g, --group      # preserve group
        -o, --owner      # preserve owner
        -D               # same as --devices --specials
    -A  # preserve ACLs (implies --perms)
    -X  # preserve extended attributes
    -v  # verbose
    -z  # compress file data during the transfer and decompress on destination
    -P  # same as --partial --progress
    -h, --human-readable # human readable
    -r  # recursive
    -t  # transfer modification times, which allows skipping files that have not been modified on future uploads
    -x  # this tells rsync to avoid crossing a filesystem boundary when recursing
    -R  # use relative paths
    -S  # try to handle sparse files efficiently so they take up less space on the destination
    -u  # skip files that are newer on the receiver
    -m  # prune empty directory chains from file-list
    --delete            # this tells rsync to delete extraneous files from the receiving side (ones that aren't on the sending side)
    --backup, -b        # make backups
    --backup-dir=DIR    # make backups into hierarchy based in DIR
    --exclude=/tmp/*    # exclude dir
    --exclude=".cache"  # exclude dir
```

### OSX

```bash
--exclude '.Trashes'
--exclude '.Spotlight-V100'
--exclude '.fseventsd'
```

### Transfer options

```bash
-z, --compress
-n, --dry-run
    --partial       # allows resuming of aborted syncs
    --bwlimit=RATE  # limit socket I/O bandwidth
```

### Display options

```bash
-q, --quiet
-v, --verbose
    --stats
-h, --human-readable
    --progress
-P                  # same as --partial --progress
```

### Skipping options

```bash
-u, --update        # skip files newer on dest
-c, --checksum      # skip based on checksum, not mod-time & size
```

### Backup options

```bash
-b, --backup           # backup with suffix
    --suffix=SUFFIX    # default ~ without --backup-dir
    --backup-dir=DIR
```

### Include options

```bash
--exclude=PATTERN
--include=PATTERN
```

```bash
--exclude-from=FILE  # read exclude patterns from file
--include-from=FILE
--files-from=FILE    # read list of filenames from FILE
```

```bash
-C, --cvs-exclude    # exclude from local/global .cvsignore
```

### Archive options

```bash
-a, --archive        # archive (-rlptgoD), where:
    -r, --recursive
    -l, --links      # copy symlinks as links
    -p, --perms      # preserve permissions
    -t, --times      # preserve times
    -g, --group      # preserve group
    -o, --owner      # preserve owner
    -D               # same as --devices --specials
```

```bash
--delete         # Delete extra files
```

### tldr

Transfer files either to or from a remote host (but not between two remote hosts), by default using SSH.
To specify a remote path, use `host:path/to/file_or_directory`.
More information: https://download.samba.org/pub/rsync/rsync.1.

- Transfer a file:
`rsync path/to/source path/to/destination`

- Use archive mode (recursively copy directories, copy symlinks without resolving and preserve permissions, ownership and modification times):
`rsync --archive path/to/source path/to/destination`

- Compress the data as it is sent to the destination, display verbose and human-readable progress, and keep partially transferred files if interrupted:
`rsync --compress --verbose --human-readable --partial --progress path/to/source path/to/destination`

- Recursively copy directories:
`rsync --recursive path/to/source path/to/destination`

- Transfer directory contents, but not the directory itself:
`rsync --recursive path/to/source/ path/to/destination`

- Recursively copy directories, use archive mode, resolve symlinks and skip files that are newer on the destination:
`rsync --recursive --archive --update --copy-links path/to/source path/to/destination`

- Transfer a directory to a remote host running `rsyncd` and delete files on the destination that do not exist on the source:
`rsync --recursive --delete rsync://host:path/to/source path/to/destination`

- Transfer a file over SSH using a different port than the default (22) and show global progress:
`rsync --rsh 'ssh -p port' --info=progress2 host:path/to/source path/to/destination`

### How to Backup Daily, Weekly, and Monthly with tar, rsync, and cron (source [LINK][https://tonyteaches.tech/rsync-backup-tutorial/])
#### Daily Backup
The following tar command will create a compressed archive of the `/var/www/html` folder in the `/home/tony/backup/daily/` folder. The find command will remove all daily backups that are older than 7 days.
```
tar -zcf /home/tony/backup/daily/backup-$(date +%Y%m%d).tar.gz -C /var/www/ html
find /home/tony/backup/daily/* -mtime +7 -delete
```
After modifying to suite your needs, put these two commands in a script called backup-daily.sh.

#### Weekly Backup
The following tar command will create a compressed archive of the `/var/www/html` folder in the `/home/tony/backup/weekly/` folder. The find command will remove all weekly backups that are older than 31 days or 1 month.
```
tar -zcf /home/tony/backup/weekly/backup-$(date +%Y%m%d).tar.gz -C /var/www/ html
find /home/tony/backup/weekly/* -mtime +31 -delete
```
After modifying to suite your needs, put these two commands in a script called backup-weekly.sh.

#### Monthly Backup
The following tar command will create a compressed archive of the `/var/www/html` folder in the `/home/tony/backup/monthly/` folder. The find command will remove all monthly backups that are older than 365 days or 1 year.
```
tar -zcf /home/tony/backup/monthly/backup-$(date +%Y%m%d).tar.gz -C /var/www/ html
find /home/tony/backup/monthly/* -mtime +365 -delete
```
After modifying to suite your needs, put these two commands in a script called backup-monthly.sh.

#### Automate with Cron
You can create a cronjob to call the daily, weekly, and monthly backup scripts. Open the cron editor with the crontab -e command and add the following while specifying the actual full path to your script files.
```
15 0 * * * sh /home/tony/backup-daily.sh
30 0 * * 1 sh /home/tony/backup-weekly.sh
45 0 1 * * sh /home/tony/backup-monthly.sh
```
In case you’re not familiar with cron syntax, this is what we’re doing:

Execute the daily backup script everyday at 12:15 AM
Execute the weekly backup script every Monday at 12:30 AM
Execute the monthly backup script the 1st of every month at 12:45 AM
Backup Externally
Next, it’s a good idea to take your local backup files and back them up to another system. The reason we want to do this is in case this system is compromised and/or you lose access to it.

We can make a mirror image of our local backup directory and everything in it with the rsync command.
```
rsync -a --delete /home/tony/backup/ root@XXX.XX.XXX.XXX:/path/to/remote/backups/
```
Notice the `–delete` flag above. This will ensure that we don’t unnecessarily keep the backups that we deleted locally with the find command on the remote server. In other words, `/home/tony/backup/` on the local system will be a mirror image of `/path/to/remote/backups/` on the remote system.

In order to execute the rsync command without the need to provide a password, you will need to install the public key on the remote server.

The last thing to do is to create a cronjob to execute the rsync command.
```
0 2 * * * rsync -a --delete /home/tony/backup/ root@XXX.XX.XXX.XXX:/path/to/remote/backups/
```
We will execute the rsync command every day at some point after all the backups have been generated.

---

[[/index|Get Back To Index]]
