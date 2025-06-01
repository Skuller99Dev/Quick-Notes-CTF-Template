---
tags:
  - nmap
---
- Quick discovery :

```
sudo nmap -sP -vv -PS22,3389 <% tp.frontmatter["VictimIP"] %>/0.24
```

- (best tool with UDP and TCP scan, you don’t want to use -sU -sT)

```
autorecon <% tp.frontmatter["VictimIP"] %>  
```

- (Best Nmap command for initial access)

```
 nmap -A -Pn <% tp.frontmatter["VictimIP"] %> 
```

- UDP ports 

```shell
sudo nmap -sU <% tp.frontmatter["VictimIP"] %> 
```

- always check version for each port vsftp 3.02 exploitable search google or searchsploits

```shell
nmap -sC -sV -A -T4 -Pn -o 101.nmap 192.168.10.10  ( *)
```

- powershell 

```powershell
 Test-NetConnection -Port 445 192.168.10.10 (check 445 is on) 1..1024 | % {echo ((New-Object Net.Sockets.TcpClient).Connect("<% tp.frontmatter["VictimIP"] %>", $)) "TCP port $ is open"} 2>$null    (check port 1 to 1024)   (for window)
```

- (for specific Port)

```shell
For each port nmap -sC -A -p21 <% tp.frontmatter["VictimIP"] %>   
```

