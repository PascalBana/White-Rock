port: 21 tcp

standard access. NOTE: will often require password
```
ftp 192.168.255.255
```

logging in as a known user. NOTE: will require both username and password
```
ftp username@192.168.255.255
```

you can run nmap scripts to enumerate ftp
```
nmap --script "ftp*" -p 21 192.168.255.255
```
This approach is very noisy, and it can take awhile especially if your enumerating more than 1 machine

here is a breakdown of the scripts that will be run
1. **ftp-anon:** Checks if anonymous login is allowed.
2. **ftp-bounce:** Checks if the FTP server is vulnerable to FTP bounce attacks.
3. **ftp-syst:** Retrieves system information using the `SYST` command.
4. **ftp-proftpd-backdoor:** Checks for a backdoor vulnerability in ProFTPD servers.
5. **ftp-vsftpd-backdoor:** Detects a backdoor in vsFTPd version 2.3.4.
6. **ftp-libopie:** Detects vulnerable versions of FTP servers that use the OPIE authentication library.
7. **ftp-brute:** Performs a brute-force attack against the FTP server.


### Downloading files
```
get /etc/passwd
```
