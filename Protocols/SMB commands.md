#### PORT 139, port 445  (also PORT 137 (name services) & PORT 138 (datagam) UDP netbios)

Always check guest login and then check public share with write and execute permission and you will find credential, files pdf ps1 etc

```sh
nmap -v -script smb-vuln* -p 139,445 <% tp.frontmatter["IPVictima"] %>
```

- (public shares) (check read write and execute)

```sh
smbmap -H <% tp.frontmatter["IPVictima"] %>   
```

- (check specific folder like tmp)

```sh
smbmap -H <% tp.frontmatter["IPVictima"] %> -R tmp   
```

- (best command to find details and users list)

```sh
enum4linux -a <% tp.frontmatter["IPVictima"] %>   
```

```sh
smbclient -p 4455 -L //<% tp.frontmatter["IPVictima"] %>/ -U noman --password=noman1234
```

```sh
smbclient -p 4455 //<% tp.frontmatter["IPVictima"] %>/scripts -U noman --password noman1234  (login)
```

