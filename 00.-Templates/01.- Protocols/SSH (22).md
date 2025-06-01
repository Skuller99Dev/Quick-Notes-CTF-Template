<%*
let Port = await tp.system.prompt("Enter the SSH port")
let User = await tp.system.prompt("Enter the SSH user")
-%>

- Launch nmap SSH Scripts on port <% Port %>


>[!example]   [SSH](SSH%20commands.md)
>```shell
 >ssh -p <% Port %> <% User %>@<% tp.frontmatter["VictimIP"] %>
>```

