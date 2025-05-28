if your getting 301's it's almost certainly a directory, gobust the sub-directories


if adding a port number remember you need to use the full url, for instance
```
gobuster dir -u http://10.10.42.47:8080 -w /usr/share/wordlists/dirb/big.txt
```

>[!todo]
>Documentation should be rewritten to use Ferrox Buster instead, as it is the modern standard.

