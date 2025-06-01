<%*
let Port = await tp.system.prompt("Enter the MYSQL port")
-%>

- Launch nmap scripts for MYSQL on port  <% Port %>


>[!example]  [MYSQL](MYSQL%20commands.md) #nmap #BBDD 
>```shell
> nmap -sV -Pn -vv -script=mysql* <% tp.frontmatter["VictimIP"] %> -p <% Port %>
>```
