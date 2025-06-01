
You can send phishing email with this port to get reverse shell.
Used to send, receive, and relay outgoing emails and Main attacks are user enumeration and using an open relay to send spam

- nmap scripts 

```
nmap <% tp.frontmatter["IPVictima"] %> --script=smtp* -p 25
```

- always login Telnet

```
telnet <% tp.frontmatter["IPVictima"] %> 25
```

