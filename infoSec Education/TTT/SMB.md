ports: 139 and 445 TCP



## SMBclient
standerd mode of entry

```
smbclient -L //192.168.1.100 -U anonymous
```

## SMBmap

```
smbmap -H 192.168.255.255
```
smbmap can often also be used with ``` -u guest``` in order to get a basic view of the files your dealing with
```
smbmap -H 192.168.255.255 -u guest
```

to list the files in a directory you can also add
```
-r <name of folder>
```

to download a file from the remote, you can use
```
-A "string"
```
Note: you do not need the full string, and any matches it finds will be downloaded into your current directory


For brute forcing please refrence the relevant section of [[hydra]]