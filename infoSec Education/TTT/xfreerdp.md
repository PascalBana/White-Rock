```
xfreerdp3 /u:offsec /p:lab /v:192.168.X.194 /drive:/tmp
```
/u:username
/p:password
/v:ip_address
/drive:shared_drive_on_windows_machine
/d:domain_name

for AD
```
xfreerdp3 /u:offsec /d:corp.com /v:192.168.X.194
```
often with AD you omit the password and then add it once the command is being run.


drive is used to transfer files from the windows pc back to kali
check the