As far as I know RDP is required in order to use this due to the way credentials get entered.

There are two major commands to get started.
one to send a single command and one to set up a constant connection over powershell.

### Invoke-command
If you are already authenticated to run commands across the domain use this
```
invoke-command -ComputerName <ComputerName> -ScriptBlock {<commandToRun>}
```
If you do not know the computer name please reference [[PowerView Enumeration]].

If you need to enter other credentials in order to run the remote command use this
```
invoke-command -ComputerName <ComputerName> -ScriptBlock {<commandToRun>} -Credential (Get-Credential)
```

### Enter-PSSession
```
Enter-PSSession -ComputerName <ComputerName> -Credential (Get-Credential)
```
