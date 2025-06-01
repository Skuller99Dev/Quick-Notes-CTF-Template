Active Directory is challenging for everyone, With the provided credentials, simply run an Nmap scan to enumerate services and open ports. Use the scan results to determine where to apply the credentials effectively based on the identified services. there are three different machines: Machine01, Machine02, Domain01. The Machine01 machine always begins with initial access and privilege escalation as a standalone. Please use the following steps to work on Active Directory:


- [ ] Run net user /domain.
- [ ] List users and run sharpHound.ps1 to find domain users (otherwise not in user list) and also with the steps below.
- [ ] Run secretdumps, and if you come from a reverse shell, then change the administrator password.
- [ ] For tunneling (use Chisel or run with SSH), if there is an issue, revert the machine.
- [ ] Find user and password from secretdumps, mimikatz c drive, config files, winpeas, etc.
- [ ] Check services with open ports such as 22, 1433, 5896, 5895, 445, etc.
- [ ] Use CrackMapExec with user and password, testing with the above services.
- [ ] Perform AS-REP Roasting with GetUserSPN.py or Rubeus.exe.
- [ ] If SQL, use mssqlclient.py; if SMB, use psexec.py; if WinRM or evil-winrm, check the administrator, then move to the next step to find the Windows root.
- [ ] For Domain01:
- [ ] Run secretsdump (Default administrator) with user pass or hash, same with psexec, winrm, SSH, etc.
- [ ] Directly rooted.