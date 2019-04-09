Steps to Restore your AWS DB

- Open your rds database in aws console and select the database you want to restore.

- Select the option as Maintenance and Backups
  
- Select the latest snapshot from the list and click on Restore

- Enter your new rds instance name that you want to create with the data backup in DB Instance Identifier

- Check the configuration of your prevoius database under modify section and select the same option here also for db backup rds and click on Restore Db Instance

- It will take some time to create the backup. Once its created log in to pgAdmin with the backup db host( username and password will be same for backup db as it was for the old one that you are doing back up of)

- Check if all the data is present in the restored db and then you can export the data from the backup db to a sql file using this command
```
    pg_dump -U username -h host databaseName >> dump.sql

```

- After the dump is created you can again import the sql file to your previous instance using this command

```
    psql -h hostname -d databaseName -U username -f dump.sql

```

- At last delete the backed up instance created and use the old db where you exported the backed file