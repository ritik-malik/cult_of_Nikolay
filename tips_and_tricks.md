# Tips & Tricks

Because once a cross eyeballed Nikolay said:

 ~ `Hail the cult of Nikolay Kadnikov`

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



