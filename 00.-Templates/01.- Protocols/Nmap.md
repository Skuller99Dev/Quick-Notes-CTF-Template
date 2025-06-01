- Launch nmap for port discovery

>[!example]  [Nmap](Utilities/Nmap.md)
>```shell
> sudo nmap -T5 -v -sV -A <% tp.frontmatter["VictimIP"] %> -p- -sC -oN nmap_<% tp.frontmatter["VictimIP"] %>.txt
>```
