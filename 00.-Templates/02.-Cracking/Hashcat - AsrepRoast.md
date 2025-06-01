<%*
let File = await tp.system.prompt("Enter the AsrepRoast file name")
-%>

- Cracking with #Hascat el <% File %>.asreproast:

```
sudo hashcat -m 18200 <% File %>.asreproast /usr/share/wordlists/rockyou.txt -r /usr/share/hashcat/rules/best64.rule --force
```