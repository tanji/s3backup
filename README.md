s3backup
========

MariaDB to Amazon S3 backup script.

Requires [s3gof3r](https://github.com/rlmcpherson/s3gof3r) and [xtrabackup](http://www.percona.com/downloads/XtraBackup/LATEST/) to work.

Please edit the script before running it, with your own user and password and Amazon S3 credentials.

Usage:
s3backup genkey				Generate the AES256 key for encryption.
s3backup upload [bucket]		Upload to S3 bucket named [bucket]
s3backup restore [bucket] [name]	Restore from S3 [bucket] backup named [name] (without .xbcrypt extension)

_This tool is not supported neither endorsed by MariaDB Corporation. Use at your own risk!_
