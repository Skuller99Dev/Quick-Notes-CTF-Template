<%*
let File = await tp.system.prompt("Enter the name of the Output File for SSH id_rsa")
-%>

- Cracking  #john id_rsa  <% File %>.hash SSH:

```
ssh2john <% File %> > <% File %>.hash
```

```
john --wordlist=/usr/share/wordlists/rockyou.txt  --rules=sshRules <% File %>.hash
```

```
hashcat -m 22921 <% File %>.hash --wordlist=/usr/share/wordlists/rockyou.txt -r ssh.rule --force
```
