<%*
let File = await tp.system.prompt("Enter the NTLM File Name")
-%>

- Cracking with #Hascat  NTLM <% File %>  :

```
hashcat -m 1000 <% File %> /usr/share/wordlists/rockyou.txt -r /usr/share/hashcat/rules/best64.rule --force
```
