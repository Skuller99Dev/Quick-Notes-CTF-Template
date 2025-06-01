<%*
let File = await tp.system.prompt("Enter the name of the Keepass File")
-%>

```
keepass2john <% File %> > <% File %>_keepass.hash
```

- Cracking with  #Hascat the <% File %>.hash:


```
hashcat -m 13400 <% File %>_keepass.hash /usr/share/wordlists/rockyou.txt -r /usr/share/hashcat/rules/rockyou-30000.rule --force
```