mysql-cron-db-backup-ubuntu14.04.1
====================

###Create a directory to store backups.
```
mkdir -p /var/backups/db-backups
```

###Edit crontab file.
```
crontab -e
```
###Paste the following into the file at the end.
```
30 2 * * *  /usr/bin/mysqldump -u MYSQLUSER -pYOURPASSWORD YOURDATABASE | gzip > /var/backups/db-backups/`date +\%Y-\%m-\%d`.sql.gz
```
--------------
Replace the following with the appropriate options:
- MYSQLUSER - your mysql user (usually root).
- YOURPASSWORD - your mysql user (root) password.
- YOURDATABASE - your database name.

Note: The above script will create a backup everyday at 2:30 AM. To view various crontab time options click [here](http://manpages.ubuntu.com/manpages/maverick/man5/crontab.5.html).
