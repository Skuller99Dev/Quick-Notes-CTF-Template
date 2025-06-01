---
tags:
  - gobuster
---

>[!example] Gobuster
> - [ ] Launched
>```
> gobuster dir -u http://<% tp.frontmatter["VictimIP"] %>/ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -t 5
> 
>```
>- Files enumeration
>-  [ ] Launched
>```
>gobuster dir -u http://<% tp.frontmatter["VictimIP"] %> -w /usr/share/wordlists/seclists/Discovery/Web-Content/common.txt -x pdf,txt -t 5
>```

>[!example] Dirb
> - [ ] Launched
>```
> dirb http://<% tp.frontmatter["VictimIP"] %>/ /usr/share/wordlists/dirb/common.txt -w
>```
