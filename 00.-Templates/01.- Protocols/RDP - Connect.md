<%*
let Name = await tp.system.prompt("Enter the name")
let Pass = await tp.system.prompt("Enter the password")
-%>

>[!example]  RDP - Windows - SIMPLE
>```
> xfreerdp /u:'<% Name %>' /p:'<% Pass %>' /v:<% tp.frontmatter["VictimIP"] %> /dynamic-resolution /drive:"/home/kali/Shared/",Shared
>```


>[!example]  RDP - Windows - DOMAIN
>```
> 					xfreerdp /u:'<% Name %>' /p:'<% Pass %>' /d:<% tp.frontmatter["DOMAIN"] %> /v:<% tp.frontmatter["VictimIP"] %> /dynamic-resolution /drive:"/home/kali/Shared/",Shared
>```
