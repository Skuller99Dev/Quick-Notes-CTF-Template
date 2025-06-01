<%*
let Port = await tp.system.prompt("Enter the SMTP port")
-%>

- Launch  nmap scripts for SMTP on port  <% Port %>

>[!example]  [SMPT](SMTP%20commands.md) #nmap
>```shell
 >nmap -sU -p<% Port %> --script "snmp-*" <% tp.frontmatter["VictimIP"] %>
>```
