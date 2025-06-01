<%*
let Port = await tp.system.prompt("Enter the MSSQL port")
-%>

- Launch nmap scripts for MS-SQL on port  <% Port %>

>[!example]  [MS-SQL](MSSQL%20commands.md) #nmap #BBDD 
>```shell
> nmap -n -v -sV -Pn -p   <% Port %> –script ms-sql-info,ms-sql-ntlm-info,ms-sql-empty-password <% tp.frontmatter["VictimIP"] %>
>```
