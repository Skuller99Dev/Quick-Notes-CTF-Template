<%*
let File = await tp.system.prompt("Enter the kerberoast File name")
-%>

- Cracking with #Hascat the <% File %>.kerberoast:

```
sudo hashcat -m 13100 <% File %>.kerberoast /usr/share/wordlists/rockyou.txt -r /usr/share/hashcat/rules/rockyou-30000.rule --force
```