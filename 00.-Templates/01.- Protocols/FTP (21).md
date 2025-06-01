<%*
let Port = await tp.system.prompt("Enter the FTP port")
-%>

- Launch  nmap FTP Scripts on the port <% Port %>

>[!example]   [FTP](FTP%20commands.md) #nmap
>```shell
> nmap --script=ftp-* -p <% Port %> <% tp.frontmatter["VictimIP"] %> >
>```

- We check anonymous FTP

```
ftp anonymous@<% tp.frontmatter["VictimIP"] %> -p <% Port %>
```

