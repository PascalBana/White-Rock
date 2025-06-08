For a mind map version of the same info please look here [[PowerView Enumeration Mind Map.canvas|PowerView Enumeration Mind Map]].
if anything of these commands give no or confusing output you can always add the `-Verbose` flag in order to get more info
## OS Enumeration
#### Computers
```
Get-NetComputer | select operatingsystem,dnshostname
```
## Domain Enumeration
#### Current Domain
```
Get-Domain | select Name,Parent,Forest,DomainControllers |fl
```

```
Get-DomainSID
```
#### Domain Policy(Password Policy)
```
(Get-DomainPolicyData).systemaccess
```
#### Domain Controllers
```
Get-DomainController | select Name,OSversion,IPAddress | fl
```

---
## Users Enumeration
#### Current Domain Users
```
Get-DomainUser | select name,logoncount,description,memberof,useraccountcontrol
```
#### User Full Detail
```
Get-DomainUser -identity <USER> -Properties
```

---
## Computers Enumeration
#### Current Domain Computers
```
Get-DomainComputer | select name,logoncount,description,operatingsystem
```
#### Server Computers
Note: Makes a lot of noise i.e. easily detected.
```
Get-DomainComputer -OperatingSystem "*Server*"
```
#### Pingable Computers
```
Get-DomainComputer -Ping | select name,logoncount,description,operatingsystem
```

---
## Groups Enumeration
### Domain Groups
#### Current Domain Groups
```
Get-DomainGroup | select Name
```
#### Domain Groups Contains "Admin"
```
Get DomainGroup *admin* | select name,Description
```
#### Domain Group Members
```
Get-DomainGroupMember -identity "Domain Admins" | select MemberName,MemberObjectClass,MemberSID
```

### Local Groups
#### Local Groups For Computer
```
Get-NetLocalGroup -ComputerName <HOST>
```
#### Local Group Members
```
Get-LocalGroupMember -Group Administrators
```
#### Other Computer's Group Members
```
Get-NetLocalGroupMember -ComputerName <HOST> -GroupName Administrators | select MemberName,IsGroup,IsDomain
```

---
## Logged On Users
#### Current Local Logged On Users
```
Get-NetLoggedon | select username
```
#### Current Computer Logged On Users
```
Get-LoggedonLocal -ComputerName <HOST>
```
#### Last Login For a Domain Computer
```
Get-LastLoggedOn -ComputerName <HOST>
```

---
## Group Policy (GPO)
#### Domain GPO's
```
Get-DomainGPO | select displayname,name
```
#### Domain GPA's for Computer
```
Get-DomainGPO -ComputerIdetity <HOST> | select displayname,name
```
#### Local Group Users GPO
```
Get-DomainGPOComputerLocalGroupMapping -ComputerIdentity <HOST>
```

```
Get-DomainGPOUserLocalGroupMapping -Identity <USER>
```
#### GPO Applied on Specific OU
```
Get-DomainGPO -Identity "{3E04167E-C2B6-4A9A-8FB7-C811148DC97C}"
```

---
## Organization Unit (OU)
#### Current Domain OU's
```
Get-DomainOU | select name,gplink
```
#### Computers On Specific OU
```
(Get-DomainOU -Identity <OU>).distinguishedname | %{Get-DomainComputer -SearchBase $_} | select name
```

---
## Access Control List(ACL)
#### ACL's For Object
```
Get-DomainObjectAcl -SamAccountName <USER> -ResolveGUIDs
```
#### ACL's For Prefix or Group
```

```