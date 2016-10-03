# s3backup

Stream MySQL Backups to AWS S3.

## Prerequisites

- [s3gof3r](https://github.com/rlmcpherson/s3gof3r)

  s3gof3r provides fast, parallelized, pipelined streaming access to Amazon S3. It includes a command-line interface: gof3r
- [xtrabackup](http://www.percona.com/downloads/XtraBackup/LATEST/) >= 2.3

  Percona XtraBackup is an open-source hot backup utility for MySQL - based servers that doesn’t lock your database during the backup.

## Configuration

Set AWS S3 Bucket Name to store backups

```
S3_BUCKET_NAME='my_bucket'
```

Set AWS S3 Bucket path to store backups. This is usefull if you want to store all this backups in a dedicated directory

```
S3_BACKUP_PATH='databases'
```

Set Backup path to store backups, e.g cluster_name

```
S3_BACKUP_NAME='cluster_name'
```

MySQL User user when running a backup.

```
MYSQL_USER='root'
```

MySQL User password user when running a backup.

```
MYSQL_PASSWORD='root'
```

Command to start mysql, based on your distro.

```
MYSQL_SERVICE_CMD="service mysql start"
```

Directory used to restore the backup. If you are using *full-restore* set this to MySQL datadir otherwise set this to a temporal directory.

```
LOCAL_DIR='/tmp/restore_db'
```

AWS Region where S3 Bucket is located

```
AWS_REGION='s3-us-west-2.amazonaws.com'
```

AWS Access key

```
export AWS_ACCESS_KEY_ID='YOUR_AWS_ACCESS_KEY_ID'
```

AWS Secret key

```
export AWS_SECRET_ACCESS_KEY='YOUR_AWS_SECRET_ACCESS_KEY'
```

## Usage

Generate the AES256 key for backups encryption

```
s3backup genkey
```

Upload a full backup to S3 Bucket

```
s3backup backup
```

Prepare a full backup restore from S3 Bucket from desired date in format 'YYYYMMDD'. This will leave a restore ready to run *innobackupex --move-back DIR*

```
s3backup restore date
```

Restore a full backup from S3 Bucket from disered date in format 'YYYYMMDD'. Set LOCAL_DIR to MySQL datadir, make sure this
directory is empty and MySQL Service is not running.

```
s3backup full-restore date
```

## References

- https://mariadb.com/blog/streaming-mariadb-backups-cloud
