## Keepass Database

- Database Hash

```sh
keepass2john Database.kdbx > keepass.hash
```

- remove  *Database:*
- Cracking con Hashcat 

```
hashcat -m 13400 keepass.hash /usr/share/wordlists/rockyou.txt -r /usr/share/hashcat/rules/rockyou-30000.rule --force
```