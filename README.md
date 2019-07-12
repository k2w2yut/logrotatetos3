# Configuration example for backup log to s3

## Flow
Use logrotate to zip, create new and call s3 command

## Prerequisite
1. Assign "Name" Tag for EC2
2. Assign IAM role to EC2 with policies
	* AmazonS3FullAccess
		* to write S3 file
	* AmazonEC2ReadOnlyAccess
		* to get "Name" tag
3. Put the conf file at /etc/logrotate.d/
4. Edit the config file
	* line  1 change to the log file that you want to backup
	* rotate: how many files (including .log and .gz) would you like to keep
	* AWS s3 sync config: LOG_FOLDER, REGION, BUCKET
	* line 24 update the --include and --exclude as proper with the log file
5. You can try with
	* sudo logrotate {path_to_config}/railslog --verbose --force

