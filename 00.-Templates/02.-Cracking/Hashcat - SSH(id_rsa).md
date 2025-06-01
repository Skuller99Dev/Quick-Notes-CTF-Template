<%*
let File = await tp.system.prompt("Enter the name of the SSH id_rsa File")
-%>

- Cracking with  #Hascat SSH <% File %>.hash:

```
ssh2john id_rsa > <% File %>.hash
hashcat -m 22921 <% File %>.hash /usr/share/wordlists/rockyou.txt
```

> [!warning] Loading  hashcat error 
> Token length exception /  No hashes loaded. --> Load into John
> ```
> john --wordlist=/usr/share/wordlists/rockyou.txt <% File %>.hash
> ```

