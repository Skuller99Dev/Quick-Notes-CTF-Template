<%*
let Port = await tp.system.prompt("Enter the HTTP port")
-%>

- We launch the Scripts to enumerate endpoints to the port   <% Port %>

>[!example]   [HTTP](HTTP%20commands.md) #gobuster
>```shell
>gobuster dir -u http://<% tp.frontmatter["VictimIP"] %>:<% Port %>/ -w /usr/share/seclists/Discovery/Web-Content/raft-medium-words.txt -t 5 -x php
>```

>[!example]   [HTTP](HTTP%20commands.md) #feroxbuster
>```shell
 >sudo feroxbuster -u http://<% tp.frontmatter["VictimIP"] %>:<% Port %> --scan-dir-listings -w /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-big.txt 
 >```


>[!example]   [HTTP](HTTP%20commands.md) #ffuz
>```shell
 >ffuf -w /usr/share/seclists/Discovery/Web-Content/raft-medium-words.txt -u http://<% tp.frontmatter["IPVicVictimIPtima"] %>:<% Port %>/FUZZ
 >```
 